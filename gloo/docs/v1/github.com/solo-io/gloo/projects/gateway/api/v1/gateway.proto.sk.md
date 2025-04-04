
---
title: "gateway.proto"
weight: 5
---

<!-- Code generated by solo-kit. DO NOT EDIT. -->


### Package: `gateway.solo.io` 
#### Types:


- [Gateway](#gateway) **Top-Level Resource**
  



##### Source File: [github.com/solo-io/gloo/projects/gateway/api/v1/gateway.proto](https://github.com/solo-io/gloo/blob/master/projects/gateway/api/v1/gateway.proto)





---
### Gateway

 
A gateway describes the routes to upstreams that are reachable via a specific port on the Gateway Proxy itself.

Deprecated: see gateway.solo.io.v2.Gateway

```yaml
"ssl": bool
"virtualServices": []core.solo.io.ResourceRef
"bindAddress": string
"bindPort": int
"plugins": .gloo.solo.io.HttpListenerPlugins
"status": .core.solo.io.Status
"metadata": .core.solo.io.Metadata
"useProxyProto": .google.protobuf.BoolValue

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `ssl` | `bool` | if set to false, only use virtual services with no ssl configured. if set to true, only use virtual services with ssl configured. |  |
| `virtualServices` | [[]core.solo.io.ResourceRef](../../../../../../solo-kit/api/v1/ref.proto.sk#resourceref) | names of the the virtual services, which contain the actual routes for the gateway if the list is empty, all virtual services will apply to this gateway (with accordance to tls flag above). |  |
| `bindAddress` | `string` | the bind address the gateway should serve traffic on |  |
| `bindPort` | `int` | bind ports must not conflict across gateways in a namespace |  |
| `plugins` | [.gloo.solo.io.HttpListenerPlugins](../../../../gloo/api/v1/plugins.proto.sk#httplistenerplugins) | top level plugin configuration for all routes on the gateway |  |
| `status` | [.core.solo.io.Status](../../../../../../solo-kit/api/v1/status.proto.sk#status) | Status indicates the validation status of this resource. Status is read-only by clients, and set by gloo during validation |  |
| `metadata` | [.core.solo.io.Metadata](../../../../../../solo-kit/api/v1/metadata.proto.sk#metadata) | Metadata contains the object metadata for this resource |  |
| `useProxyProto` | [.google.protobuf.BoolValue](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/bool-value) | Enable ProxyProtocol support for this listener |  |





<!-- Start of HubSpot Embed Code -->
<script type="text/javascript" id="hs-script-loader" async defer src="//js.hs-scripts.com/5130874.js"></script>
<!-- End of HubSpot Embed Code -->
