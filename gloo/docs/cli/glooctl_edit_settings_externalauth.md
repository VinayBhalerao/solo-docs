---
title: "glooctl edit settings externalauth"
weight: 5
---
## glooctl edit settings externalauth

Configure external auth settings (Enterprise)

### Synopsis

Let gloo know the location of the ext auth server. This is a Gloo Enterprise feature.

```
glooctl edit settings externalauth [flags]
```

### Options

```
      --extauth-server-name string        name of the ext auth server upstream
      --extauth-server-namespace string   namespace of the ext auth server upstream
  -h, --help                              help for externalauth
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
  -o, --output OutputType          output format: (yaml, json, table, kube-yaml, wide) (default table)
      --resource-version string    the resource version of the resource we are editing. if not empty, resource will only be changed if the resource version matches
      --use-consul                 use Consul Key-Value storage as the backend for reading and writing config (VirtualServices, Upstreams, and Proxies)
```

### SEE ALSO

* [glooctl edit settings](../glooctl_edit_settings)	 - root command for settings

