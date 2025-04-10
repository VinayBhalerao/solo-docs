
---
title: "transformation.proto"
weight: 5
---

<!-- Code generated by solo-kit. DO NOT EDIT. -->


### Package: `envoy.api.v2.filter.http` 
#### Types:


- [RouteTransformations](#routetransformations)
- [Transformation](#transformation)
- [Extraction](#extraction)
- [TransformationTemplate](#transformationtemplate)
- [InjaTemplate](#injatemplate)
- [Passthrough](#passthrough)
- [MergeExtractorsToBody](#mergeextractorstobody)
- [HeaderBodyTransform](#headerbodytransform)
  



##### Source File: [github.com/solo-io/gloo/projects/gloo/api/v1/plugins/transformation/transformation.proto](https://github.com/solo-io/gloo/blob/master/projects/gloo/api/v1/plugins/transformation/transformation.proto)





---
### RouteTransformations



```yaml
"requestTransformation": .envoy.api.v2.filter.http.Transformation
"clearRouteCache": bool
"responseTransformation": .envoy.api.v2.filter.http.Transformation

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `requestTransformation` | [.envoy.api.v2.filter.http.Transformation](../transformation.proto.sk#transformation) |  |  |
| `clearRouteCache` | `bool` | clear the route cache if the request transformation was applied |  |
| `responseTransformation` | [.envoy.api.v2.filter.http.Transformation](../transformation.proto.sk#transformation) |  |  |




---
### Transformation

 
[#proto-status: experimental]

```yaml
"transformationTemplate": .envoy.api.v2.filter.http.TransformationTemplate
"headerBodyTransform": .envoy.api.v2.filter.http.HeaderBodyTransform

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `transformationTemplate` | [.envoy.api.v2.filter.http.TransformationTemplate](../transformation.proto.sk#transformationtemplate) |  |  |
| `headerBodyTransform` | [.envoy.api.v2.filter.http.HeaderBodyTransform](../transformation.proto.sk#headerbodytransform) |  |  |




---
### Extraction



```yaml
"header": string
"regex": string
"subgroup": int

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `header` | `string` |  |  |
| `regex` | `string` | what information to extract. if extraction fails the result is an empty value. |  |
| `subgroup` | `int` |  |  |




---
### TransformationTemplate



```yaml
"advancedTemplates": bool
"extractors": map<string, .envoy.api.v2.filter.http.Extraction>
"headers": map<string, .envoy.api.v2.filter.http.InjaTemplate>
"body": .envoy.api.v2.filter.http.InjaTemplate
"passthrough": .envoy.api.v2.filter.http.Passthrough
"mergeExtractorsToBody": .envoy.api.v2.filter.http.MergeExtractorsToBody

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `advancedTemplates` | `bool` |  |  |
| `extractors` | `map<string, .envoy.api.v2.filter.http.Extraction>` | Extractors are in the origin request language domain |  |
| `headers` | `map<string, .envoy.api.v2.filter.http.InjaTemplate>` |  |  |
| `body` | [.envoy.api.v2.filter.http.InjaTemplate](../transformation.proto.sk#injatemplate) |  |  |
| `passthrough` | [.envoy.api.v2.filter.http.Passthrough](../transformation.proto.sk#passthrough) |  |  |
| `mergeExtractorsToBody` | [.envoy.api.v2.filter.http.MergeExtractorsToBody](../transformation.proto.sk#mergeextractorstobody) |  |  |




---
### InjaTemplate

 
custom functions:
header_value(name) -> from the original headers
extracted_value(name, index) -> from the extracted values

```yaml
"text": string

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `text` | `string` |  |  |




---
### Passthrough



```yaml

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 




---
### MergeExtractorsToBody



```yaml

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 




---
### HeaderBodyTransform



```yaml

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 





<!-- Start of HubSpot Embed Code -->
<script type="text/javascript" id="hs-script-loader" async defer src="//js.hs-scripts.com/5130874.js"></script>
<!-- End of HubSpot Embed Code -->
