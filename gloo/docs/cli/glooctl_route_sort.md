---
title: "glooctl route sort"
weight: 5
---
## glooctl route sort

sort routes on an existing virtual service

### Synopsis

The order of routes matters. A route is selected for a request based on the first matching route matcher in the virtual serivce's list. sort automatically sorts the routes in the virtual service

Usage: `glooctl route sort [--name virtual-service-name] [--namespace virtual-service-namespace]`

```
glooctl route sort [flags]
```

### Options

```
  -h, --help                help for sort
  -o, --output OutputType   output format: (yaml, json, table, kube-yaml, wide) (default table)
```

### Options inherited from parent commands

```
      --consul-address string      address of the Consul server. Use with --use-consul (default "127.0.0.1:8500")
      --consul-datacenter string   Datacenter to use. If not provided, the default agent datacenter is used. Use with --use-consul
      --consul-root-key string     key prefix for for Consul key-value storage. (default "gloo")
      --consul-scheme string       URI scheme for the Consul server. Use with --use-consul (default "http")
      --consul-token string        Token is used to provide a per-request ACL token which overrides the agent's default token. Use with --use-consul
  -i, --interactive                use interactive mode
      --name string                name of the resource to read or write
  -n, --namespace string           namespace for reading or writing resources (default "gloo-system")
      --use-consul                 use Consul Key-Value storage as the backend for reading and writing config (VirtualServices, Upstreams, and Proxies)
```

### SEE ALSO

* [glooctl route](../glooctl_route)	 - subcommands for interacting with routes within virtual services

