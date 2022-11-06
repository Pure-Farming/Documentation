---

title: Work Record
menu_order: 1
post_status: publish
post_excerpt: Crops - Work Record
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: Crops – Work Record

- [URLs](#urls)
- [Response Structure](#response-structure)

## URLs

Get all work records that you have access to.

```
GET /data/crops/work-records
```

Get all work records that you have access to for a given Holding, the HoldingId is required in this case. 

```
GET /data/holdings/{HoldingId}/crops/work-records
```

Get an individual work record for a given holding, both the HoldingId and the Id of the work record are required. 

```
GET /data/holdings/{HoldingId}/crops/work-records/{WorkRecordId} 
```

## Response Structure

A call to the Work Record endpoints returns the following fields:

```json
{
    "resourceType": "/crop/work-record",
    "id": "string",
    "self": "string",
    "operation": "string",
    "status": "string",
    "priority": "string",
    "meta": { … }, 
    "observationDate": "2022-07-07T12:52:56.227Z", 
    "feature": { … }, 
    "holding": { … },
    "nonOverlapWorkedArea": { … },
    "workedArea": { … },
    "phenomenonStartTime": "2022-07-16T08:28:02:000Z",
    "phenomenonEndTime": "2022-07-16T10:18:02:000Z",
    "remark": "spray prod and spreading fert on back field",
    "responsible": "string",
    "loggedOperations":[ … ]
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Resource Type** | The fixed discriminator for the Crop Work Record resource type. <br/>Value: /crop/work-record | String
|**Id** |The Pure Farming Id of this Work Record |UUID |
| **Self** | A link to this specific work record | URI
| **Operation** | Constant value in any concrete class for the operation type | String |
| **Status** | Allowable statuses of a work item | Enumeration |
| **Priority** | Allowable priorities of a work item | Enumeration |
| **Meta** |Meta data for the resource. | [Metadata](/resource-types/common.md#metadata) |
| **Observation Date** |UTC Date (required) and time (optional) of the observation of the work record | Date/Time
| **Phenomenon Start Time** | ISO UTC DateTime for when the work record started | Date/Time
| **Phenomenon End Time** | ISO UTC DateTime for when the work record ended | Date/Time
| **Remark** | Notes or remarks | String
| **Responsible** | Identifier of the person responsible for the work record | String
| **Logged Operations** | Array of the operations completed in this work record | Array of [Operations](/resource-types/crops/work-record.md#operations)]

## Operations

This represents an individual operation within the work record

```json
{
    "resourceType": "/crop/operation-record",
    "id": "string",
    "identifiers": [ … ],
    "operation": "string",
    "operationName":"",
    "meta": { … }, 
    "links": [ … ],
    "observationDate": "2022-07-07T12:52:56.227Z", 
    "feature": { … }, 
    "holding": { … },
    "phenomenonStartTime": "2022-07-16T08:28:02:000Z",
    "phenomenonEndTime": "2022-07-16T10:18:02:000Z",
    "remark": "spray prod and spreading fert on back field",
    "responsible": "string",
    "summaryGeometry": { … },
    "loggedGeometry": { … },
    "products": [ … ],
    "environment": { … }
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Resource Type** | The fixed discriminator for the operation record resource type. <br/>Value: /crop/operation-record | String
| **Id** |The Pure Farming Id of this Operation Record |UUID |
| **Identifiers** | Any identifiers for this operation record | Array of [Identifiers](/resource-types/common.md#identifier) |
| **Operation** |  Encoding of the field operation | String
| **Operation Name** | Name of the field operation | String
| **Meta** |Meta data for the resource. | [Metadata](/resource-types/common.md#metadata) |
| **Links** | Any links relevant to this operation record | Array of [Links](/resource-types/common.md#link) |
| **Observation Date** | UTC Date (required) and time (optional) of the observation of the operation record | Date/Time
| **Feature** | The feature that this operation performed on | [Feature](/resource-types/common.md/#feature) |
| **Holding** | The Holding that this operation is linked to | [Feature](/resource-types/common.md/#feature)  |
| **Phenomenon Start Time** | ISO UTC DateTime for when the operation record started | Date/Time
| **Phenomenon End Time** | ISO UTC DateTime for when the operation record ended | Date/Time
| **Remark** | Notes or remarks | String
| **Summary Geometry** | The geojson feature (with its geometry) that summarises the operation activity.| GeoJSON Feature
| **Logged Geometry** | The geojson feature (with its geometry) that covers the logged track or activity record in detail.| GeoJSON Feature
| **Products** |Products applied in the operation| Array of Products
| **Environment** |Environmental data| Environment

## Product
A product applied in the operation

```json
{
    "applicationRate": {
        "measurement": 10,
        "units": "KGM",
        "resoultion": 0.1
    },,
    "spatialMetric":{
        "measurement": 10,
        "units": "MTK",
        "resoultion": 1
    },
    "applicationTotal":{
        "measurement": 100,
        "units": "KGM",
        "resoultion": 1
    },
    "components": [ … ],
}
```
| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
|** Application Rate ** | The rate at which the product is applied | Object
|** Spatial Metric ** | The spatial metric to which the application rate applies e.g., [per] linear metre (MTR) or square metre (MTK) | Object
|** Application Total ** | The total amount of product applied | Object
|** Components ** | The components in this product mix (can be one) | Array of Components


## Environment


## Components