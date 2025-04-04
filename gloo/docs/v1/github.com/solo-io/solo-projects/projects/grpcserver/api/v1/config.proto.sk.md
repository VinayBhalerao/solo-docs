
---
title: "config.proto"
weight: 5
---

<!-- Code generated by solo-kit. DO NOT EDIT. -->


### Package: `glooeeapi.solo.io` 
#### Types:


- [OAuthEndpoint](#oauthendpoint)
- [GetVersionRequest](#getversionrequest)
- [GetVersionResponse](#getversionresponse)
- [GetOAuthEndpointRequest](#getoauthendpointrequest)
- [GetOAuthEndpointResponse](#getoauthendpointresponse)
- [GetSettingsRequest](#getsettingsrequest)
- [GetSettingsResponse](#getsettingsresponse)
- [UpdateSettingsRequest](#updatesettingsrequest)
- [UpdateSettingsResponse](#updatesettingsresponse)
- [GetIsLicenseValidRequest](#getislicensevalidrequest)
- [GetIsLicenseValidResponse](#getislicensevalidresponse)
- [GetPodNamespaceRequest](#getpodnamespacerequest)
- [GetPodNamespaceResponse](#getpodnamespaceresponse)
- [ListNamespacesRequest](#listnamespacesrequest)
- [ListNamespacesResponse](#listnamespacesresponse)
  



##### Source File: [github.com/solo-io/solo-projects/projects/grpcserver/api/v1/config.proto](https://github.com/solo-io/solo-projects/blob/master/projects/grpcserver/api/v1/config.proto)





---
### OAuthEndpoint



```yaml
"url": string
"clientName": string

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `url` | `string` |  |  |
| `clientName` | `string` |  |  |




---
### GetVersionRequest



```yaml

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 




---
### GetVersionResponse



```yaml
"version": string

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `version` | `string` |  |  |




---
### GetOAuthEndpointRequest



```yaml

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 




---
### GetOAuthEndpointResponse



```yaml
"oAuthEndpoint": .glooeeapi.solo.io.OAuthEndpoint

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `oAuthEndpoint` | [.glooeeapi.solo.io.OAuthEndpoint](../config.proto.sk#oauthendpoint) |  |  |




---
### GetSettingsRequest



```yaml

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 




---
### GetSettingsResponse



```yaml
"settings": .gloo.solo.io.Settings

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `settings` | [.gloo.solo.io.Settings](../../../../../../gloo/projects/gloo/api/v1/settings.proto.sk#settings) |  |  |




---
### UpdateSettingsRequest



```yaml
"ref": .core.solo.io.ResourceRef
"watchNamespaces": []string
"refreshRate": .google.protobuf.Duration
"settings": .gloo.solo.io.Settings

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `ref` | [.core.solo.io.ResourceRef](../../../../../../solo-kit/api/v1/ref.proto.sk#resourceref) | Deprecated |  |
| `watchNamespaces` | `[]string` | Deprecated |  |
| `refreshRate` | [.google.protobuf.Duration](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/duration) | Deprecated |  |
| `settings` | [.gloo.solo.io.Settings](../../../../../../gloo/projects/gloo/api/v1/settings.proto.sk#settings) |  |  |




---
### UpdateSettingsResponse



```yaml
"settings": .gloo.solo.io.Settings

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `settings` | [.gloo.solo.io.Settings](../../../../../../gloo/projects/gloo/api/v1/settings.proto.sk#settings) |  |  |




---
### GetIsLicenseValidRequest



```yaml

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 




---
### GetIsLicenseValidResponse



```yaml
"isLicenseValid": bool

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `isLicenseValid` | `bool` |  |  |




---
### GetPodNamespaceRequest



```yaml

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 




---
### GetPodNamespaceResponse



```yaml
"namespace": string

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `namespace` | `string` |  |  |




---
### ListNamespacesRequest



```yaml

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 




---
### ListNamespacesResponse



```yaml
"namespaces": []string

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `namespaces` | `[]string` |  |  |





<!-- Start of HubSpot Embed Code -->
<script type="text/javascript" id="hs-script-loader" async defer src="//js.hs-scripts.com/5130874.js"></script>
<!-- End of HubSpot Embed Code -->
