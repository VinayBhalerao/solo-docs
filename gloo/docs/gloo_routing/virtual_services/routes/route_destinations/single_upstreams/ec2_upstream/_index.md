---
menuTitle: EC2 Upstreams
title: Routing to AWS EC2 Instances
weight: 3
description: Example of routing to EC2 instances.
---


Gloo allows you to create upstreams from groups of EC2 instances.

#### Sample EC2 Upstream Config

- Before jumping into the tutorial, familiarize yourself with the EC2 upstream specification.
  - The upstream config below creates an upstream that load balances to all EC2 instances that both match the filter criteria and are available to a user with the credentials provided by the secret.

```yaml
apiVersion: gloo.solo.io/v1
kind: Upstream
metadata:
  annotations:
  name: my-ec2-upstream
  namespace: gloo-system
spec:
  upstreamSpec:
    awsEc2:
      filters:
      - key: some-key
      - kvPair:
          key: some-other-key
          value: some-value
      region: us-east-1
      publicIp: true
      secretRef:
        name: my-aws-secret
        namespace: default
      roleArn: arn:aws:iam::123456789012:role/describe-ec2-demo
```

## Key points
- **Credentials**: each upstream can be configured with custom credentials which will influence what instances are available for use.
  - User credentials can be passed as an upstream-specific secret ref or through common AWS environment variables
  - A role can be optionally be included in the upstream spec. If provided, Gloo will assume this role on behalf of the upstream's user account prior to listing instances. This can be a convenient way to manage upstream-specific access control.
- **Filtering**: tag filters allow you to define which instances should be associated with your upstream.
  - Filters can be specified in terms of tag key or tag key-value matches
  - If multiple filters are specified, an instance must match each filter in order to be associated with the upstream.

## Tutorial: Basic Configuration of EC2 Upstreams

- Below is an outline of how to use the EC2 plugin to create routes to EC2 instances.
- Requirements: Gloo 0.17.4 or greater installed as a gateway.


### Prepare sample resources in AWS
*Note, if you already have an EC2 instance you would like to route to and the necessary credentials configured, you can skip to the next section.*

#### Configure an EC2 instance

- Provision an EC2 instance
  - Use an "amazon linux" image
  - Configure the security group to allow http traffic on port 80

- Tag your instance with the following tags
  - gloo-id: abcde123
  - gloo-tag: group1
  - version: v1.2.3

- Set up your EC2 instance
  - Download a demo app: an http response code echo app
    - This app responds to requests with the corresponding response code
      - ex: http://[my-instance-ip]/?code=404 produces a `404` response
  - Make the app executable
  - Run it in the background

```bash
wget https://mitch-solo-public.s3.amazonaws.com/echoapp2
chmod +x echoapp2
sudo ./echoapp2 --port 80 &
```

- Verify that you can reach the app
  - `curl` the app, you should see a help menu for the app

```bash
curl http://<instance-public-ip>/
```

#### Create a secret with AWS credentials

- Gloo needs AWS credentials to be able to find EC2 resources
- Recommendation: create a set of credentials that only have access to the relevant resources.
  - In this example, pretend that the secret we create only has access to resources with the `gloo-tag:group1` tag.

```bash
glooctl create secret aws \
  --name gloo-tag-group1 \
  --namespace default \
  --access-key [aws_secret_key_id] \
  --secret-key [aws_secret_access_key]
```


#### Create a role for Gloo to assume on behalf of your upstreams
- For additional control over Gloo's access to your resources and as an additional filter on your EC2 Upstream's list of
available instances it is recommended that you credential your upstreams with a low-access user account that has the
ability to assume the specific role it requires.
- When you provide both a secret ref and a Role ARN to your upstream, Gloo will call the AWS API with credentials
composed from the user account associated with the secret and the provided role (via the AssumeRole feature).

##### Create a role
- To configure you AWS account with the relevant ARN Role, there are two steps to take (if you have not already done so):
  - Create a policy that allows the policy holder to describe EC2 instances
  - Create a role that contains that policy and trusts (ie: grants role assumption to) the upstream's account 
- First create a role. In the AWS console:
  - Navigate to IAM > Roles, choose "Create Role"
  - Follow the interactive guide to create a role
    - Choose "AWS account" as the type of trusted entity and provide the 12 digit account id of the account which holds
    the EC2 instances you want to route to.
- Choose or create a policy for the role
    - An example of a **Policy** that allows the role to describe EC2 instances is shown below.

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": "ec2:DescribeInstances",
            "Resource": "*"
        }
    ]
}
```

##### Allow your upstream's user account to list EC2 instances
- Now grant the upstream's account acces to the role you created. In the AWS console:
  - Navigate to IAM > Roles, Select your role
  - Select the "Trust relationships" tab
      - Note the entries under the "Trusted entities" table
  - Click "Edit trust relationship"
  - Add your user/service account's ARN to the Principal.AWS list, as shown below
- An example of **Trust Relationship** is shown below (many other variants are possible)
  - Add the ARNs of each of the user accounts that you want to allow to assume this role.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": [
          "arn:aws:iam::[account_id]:user/[user_id]"
        ]
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```


### Create an EC2 Upstream

- Finally, make an upstream that points to the resources that you want to route to.
- Take note of a few of the options we have set for this sample upstream:
  - **Region**: this upstream indicates that it reads instances from the "us-east-1" region
  - **Public IP**: this upstream routes to the instances' public IPs. If not set, Gloo will default the private IPs.
  - **Secret Ref**: a reference to the secret associated with the AWS account that Gloo should use on behalf of the upstream.
  - **Role ARN**: a role that Gloo should assume on behalf of the upstream when listing the set of available instances.
  - **Filters**: this upstream uses three tag filters to indicate which instances, among those that are accessible given the upstream's credentials, should be routed to. One of the filters only specifies that a certain tag should be present on the instance. The other two filters require that a given tag and tag value are present.

```yaml
apiVersion: gloo.solo.io/v1
kind: Upstream
metadata:
  annotations:
  name: ec2-demo-upstream
  namespace: gloo-system
spec:
  upstreamSpec:
    awsEc2:
      filters:
      - key: gloo-id
      - kvPair:
          key: gloo-tag
          value: group1
      - kvPair:
          key: version
          value: v1.2.3
      region: us-east-1
      publicIp: true
      secretRef:
        name: gloo-tag-group1
        namespace: default
      roleArn: "<arn-for-the-role-you-created>"
```

- Save the spec to ``ec2-demo-upstream.yaml` and use `kubectl` to create the upstream in Kubernetes.


```
kubectl apply -f ec2-demo-upstream.yaml
```

### Create a route to your upstream

- Now that you have created an upstream, you can route to it as you would with any other upstream.

```bash
glooctl add route  \
  --path-exact /echoapp  \
  --dest-name ec2-demo-upstream \
  --prefix-rewrite /
```

- Verify that the route works
  - You should see the same output as when you queried the EC2 instance directly.

```bash
export URL=`glooctl proxy url`
curl $URL/echoapp
```

### Summary

In this tutorial, we created an upstream that allows us to route traffic from our gateway to a set of EC2 instances. We created a single upstream and associaed it with a single instance. You can of course create an arbitrary number of upstreams and associate them with an arbitrary number of instances. We reviewed how to prepare your AWS account with a sample instance, role, and policy so as to demonstrate the information Gloo needs to implement a routable EC2 upstream.
