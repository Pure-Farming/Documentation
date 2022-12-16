---

title: Control Endpoint
menu_order: 1
post_status: publish
post_excerpt: Control Endpoint
taxonomy:
    category:
        - root
    post_tag:
        - root

---

# Control Endpoint

The Streaming API Control endpoint is used to determine which _Pure Farming_ holdings you can push data for using the [push endpoint](/streaming-api/resources.md)

```
GET /data/streaming/control
```


## Response Structure

```json
[
  {
    "holdingId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "connectedAt": "2022-12-16T02:02:54.632Z",
    "signature": "9b96a1fe1d548cbbc960cc6a0286668fd74a763667b06366fb2324269fcabaa4",
    "identifiers": [...],
    "resourceTypes": [...],
    "connectorIdentifiers": [...]
  }
]
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Holding ID** | The _Pure Farming_ ID of the holding you can push data for | UUID | 
| **Connected At** | The date and time this permission was granted | Datetime | 
| **Signature** | A SHA256 has representing the permissions for this holding | SHA256 string |
| **Identifiers** | A list of identifiers for this holding | List of [Identifier](/resource-types/common.md#identifier)|
| **Resource Types** | A list of the resource types you are permitted to supply data for, for this holding | List of [Streaming Resource Type](#streaming-resource-type) |
| **Connector Identifiers** | A list of identifiers relating to this specific data connection | List of [Identifier](/resource-types/common.md#identifier) |


## Streaming Resource Type

Represents a resource type (within the Streaming API). In the context of the control endpoint this is used to state which resource types you have permission to provide data for.

```json
{
    "id": "/core/holding",
    "href": "https://api.purefarming.com/data/streaming/datasets/holding",
    "changes": "https://api.purefarming.com/data/streaming/datasets/holding/changes",
    "updates": "https://api.purefarming.com/data/streaming/datasets/holding/resources",
    "description": "A holding in Pure Farming"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **ID** | The identifier of the _Pure Farming_ resource type | string | 
| **Href** | The link to the dataset metadata | URI |
| **Changes** | The link to get the latest changes to the resources | URI | 
| **Updates** | The link to publish updates for a resource | URI |
| **Description** | A description of the resource type | URI |
