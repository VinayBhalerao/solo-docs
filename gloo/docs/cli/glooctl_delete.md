---
title: "glooctl delete"
weight: 5
---
## glooctl delete

Delete a Gloo resource

### Synopsis

Delete a Gloo resource

```
glooctl delete [flags]
```

### Options

```
      --consul-address string      address of the Consul server. Use with --use-consul (default "127.0.0.1:8500")
      --consul-datacenter string   Datacenter to use. If not provided, the default agent datacenter is used. Use with --use-consul
      --consul-root-key string     key prefix for for Consul key-value storage. (default "gloo")
      --consul-scheme string       URI scheme for the Consul server. Use with --use-consul (default "http")
      --consul-token string        Token is used to provide a per-request ACL token which overrides the agent's default token. Use with --use-consul
  -h, --help                       help for delete
      --name string                name of the resource to read or write
  -n, --namespace string           namespace for reading or writing resources (default "gloo-system")
      --use-consul                 use Consul Key-Value storage as the backend for reading and writing config (VirtualServices, Upstreams, and Proxies)
```

### Options inherited from parent commands

```
  -i, --interactive   use interactive mode
```

### SEE ALSO

* [glooctl](../glooctl)	 - CLI for Gloo
* [glooctl delete proxy](../glooctl_delete_proxy)	 - delete a proxy
* [glooctl delete upstream](../glooctl_delete_upstream)	 - delete an upstream
* [glooctl delete upstreamgroup](../glooctl_delete_upstreamgroup)	 - delete an upstream group
* [glooctl delete virtualservice](../glooctl_delete_virtualservice)	 - delete a virtualservice

