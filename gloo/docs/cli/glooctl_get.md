---
title: "glooctl get"
weight: 5
---
## glooctl get

Display one or a list of Gloo resources

### Synopsis

Display one or a list of Gloo resources

```
glooctl get [flags]
```

### Options

```
      --consul-address string      address of the Consul server. Use with --use-consul (default "127.0.0.1:8500")
      --consul-datacenter string   Datacenter to use. If not provided, the default agent datacenter is used. Use with --use-consul
      --consul-root-key string     key prefix for for Consul key-value storage. (default "gloo")
      --consul-scheme string       URI scheme for the Consul server. Use with --use-consul (default "http")
      --consul-token string        Token is used to provide a per-request ACL token which overrides the agent's default token. Use with --use-consul
  -h, --help                       help for get
      --name string                name of the resource to read or write
  -n, --namespace string           namespace for reading or writing resources (default "gloo-system")
  -o, --output OutputType          output format: (yaml, json, table, kube-yaml, wide) (default table)
      --use-consul                 use Consul Key-Value storage as the backend for reading and writing config (VirtualServices, Upstreams, and Proxies)
```

### Options inherited from parent commands

```
  -i, --interactive   use interactive mode
```

### SEE ALSO

* [glooctl](../glooctl)	 - CLI for Gloo
* [glooctl get proxy](../glooctl_get_proxy)	 - read a proxy or list proxies in a namespace
* [glooctl get upstream](../glooctl_get_upstream)	 - read an upstream or list upstreams in a namespace
* [glooctl get upstreamgroup](../glooctl_get_upstreamgroup)	 - read an upstream group or list upstream groups in a namespace
* [glooctl get virtualservice](../glooctl_get_virtualservice)	 - read a virtualservice or list virtualservices in a namespace

