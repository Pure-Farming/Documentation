---

title: Resources Endpoint
menu_order: 1
post_status: publish
post_excerpt: Resources Endpoint
taxonomy:
    category:
        - root
    post_tag:
        - root

---


# Resources Endpoint
You can publish data into a dataset using the resources endpoint

```
POST /data/streaming/dataset/{datasetid}/resources
```
where `datasetId` is the name of the dataset.


## Request Structure
Supply a list of objects that match the dataset specification. For example, for the `plots` dataset:

```json
[
    {
        "totalArea": {
          "measurement": 2000,
          "units": "MTK"
        },
        "totalLength": {
          "measurement": 100,
          "units": "MTK" 
        },
        "identifiers": [
            {
                "id": "79daf037-407e-49b0-b385-6cb5b9e5453c",
                "scheme": "com.purefarming.holdingId"  
            }
        ],
        "name": "My Plot",
        "resourceType": "/core/plot",
        "dataPointKey": "a-unique-id-in-my-system-for-this-plot"
    }
]
```

See [Supported Resource Types](/streaming-api/index.md#supported-resource-types) for a list of resource types the streaming API will accept.


## Response Structure
A response from the resources endpoint tells you if inserting the data into _Pure Farming_ succeeded or failed

```json
[
  {
    "successful": true,
    "index": 0
  },
  {
    "successful": false,
    "index": 1,
    "error": "Could not find Holding for: \"com.purefarming.holdingId\":\"79daf037-407e-49b0-b385-6cb5b9e5453c\""
  },
  ...
]
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Successful** | Whether the item at position `index` was successfully queued for processing in _Pure Farming_ | Boolean |
| **Index** | The zero-indexed position of the object in the incoming list that was sent | Integer |
| **Error** | An error message if the object could not be queued for processing in _Pure Farming_ | String |
