---
title: "glooctl create secret"
weight: 5
---
## glooctl create secret

Create a secret

### Synopsis

Create a secret

```
glooctl create secret [flags]
```

### Options

```
  -h, --help                           help for secret
      --use-vault                      use Vault Key-Value storage as the backend for reading and writing secrets
      --vault-address string           address of the Vault server. This should be a complete  URL such as "http://vault.example.com". Use with --use-vault (default "https://127.0.0.1:8200")
      --vault-ca-cert string           CACert is the path to a PEM-encoded CA cert file to use to verify the Vault server SSL certificate.Use with --use-vault
      --vault-ca-path string           CAPath is the path to a directory of PEM-encoded CA cert files to verify the Vault server SSL certificate.Use with --use-vault
      --vault-client-cert string       ClientCert is the path to the certificate for Vault communication.Use with --use-vault
      --vault-client-key string        ClientKey is the path to the private key for Vault communication.Use with --use-vault
      --vault-root-key string          key prefix for for Vault key-value storage. (default "gloo")
      --vault-tls-insecure             Insecure enables or disables SSL verification.Use with --use-vault
      --vault-tls-server-name string   TLSServerName, if set, is used to set the SNI host when connecting via TLS.Use with --use-vault
      --vault-token string             address of the Vault server. This should be a complete  URL such as "http://vault.example.com". Use with --use-vault
```

### Options inherited from parent commands

```
      --dry-run             print kubernetes-formatted yaml rather than creating or updating a resource
  -i, --interactive         use interactive mode
      --name string         name of the resource to read or write
  -n, --namespace string    namespace for reading or writing resources (default "gloo-system")
  -o, --output OutputType   output format: (yaml, json, table, kube-yaml, wide) (default table)
```

### SEE ALSO

* [glooctl create](../glooctl_create)	 - Create a Gloo resource
* [glooctl create secret apikey](../glooctl_create_secret_apikey)	 - Create an ApiKey secret with the given name (Enterprise)
* [glooctl create secret aws](../glooctl_create_secret_aws)	 - Create an AWS secret with the given name
* [glooctl create secret azure](../glooctl_create_secret_azure)	 - Create an Azure secret with the given name
* [glooctl create secret oauth](../glooctl_create_secret_oauth)	 - Create an OAuth secret with the given name (Enterprise)
* [glooctl create secret tls](../glooctl_create_secret_tls)	 - Create a secret with the given name

