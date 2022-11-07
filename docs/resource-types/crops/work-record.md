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
| **Logged Operations** | Array of the operations completed in this work record | Array of [Operations](/resource-types/crops/work-record.md#operations)

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
| **Products** |Products applied in the operation| Array of [Products](#products)
| **Environment** |Environmental data| [Environment](#environment)

## Products
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
|**Application Rate** | The rate at which the product is applied | Object
|**Spatial Metric** | The spatial metric to which the application rate applies e.g., per linear metre (MTR) or square metre (MTK) | Object
|**Application Total** | The total amount of product applied | Object
|**Components** | The components in this product mix (can be one) | Array of [Components](#components)


## Environment
Environmental data for the operation.

```json
{
    "windSpeed":{
        "measurement":0,
        "resolution":1,
        "units":"MTS"
    },
    "windDirectionCompass":"E",
    "windDirectionDegrees":90,
    "airTemperature":{
        "measurement":10,
        "resolution":1,
        "units":"CEL"
    },
    "humidity":{
        "measurement":50,
        "resolution":1,
        "units":"P1"
    },
    "soilTemperature":{
        "measurement":10,
        "resolution":1,
        "units":"CEL"
    },
    "solarRadiation24hr":{
        "measurement":500,
        "resolution":1,
        "units":"D54"
    },
    "rainfall24hr":{
        "measurement":2.3,
        "resolution":0.1,
        "units":"MMT"
    }
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
|**Wind Speed**|Wind speed (velocity) | Object
|**Wind Direction (Compass)**|Wind direction in compass points at the time of activity.|Enumeration
|**Wind Direction (Degrees)**|Wind direction in decimal degrees at the time of activity. | Numeric
|**Air Temperature**|Air temperature at the time of activity. | Object
|**Humidity**|Humidity at the time of activity. | Object
|**Soil Temperature**|Soil temperature at or near the time of activity. | Object
|**Solar Radiation (24 hours)**|Cumulative solar radiation over 24 hour period | Object


## Components
A component in the product mix.

```json
{
    "mixSequence":1,
    "percent":100,
    "product": {
        "type":"string",
        "manufacturer":"string",
        "brand":"string",
        "form":"string",
        "uri":"string",
        "crop": { … },
        "specificGravity":1,
        "matterState":"Solid",
        "analysis":[ … ],
        "activeIngredients":[ … ],
        "withdrawals":[ … ],
        "claims":[ … ],
        "registrations":[ … ]
    }
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Mix Sequence** | The order of the product in the mix | Integer
| **Percent** | The proportion that this product composes of the mix. Can be calculated from Wt/Vol or other measures. | Percentage
| **Product Type** |Defines types of product that can be used in field activities. | Enumeration
| **Product Manufacturer** |Manufacturer of the product| String
| **Product Brand** |Brand of the product| String
| **Product Form** | The physical form of the product | Enumeration
| **Product Uri** |A link to the product. | URI
| **Crop**  |Defines a managed crop, or a species in a mixed sward | [Crop](/resource-types/crops/index.md#crop)
| **Specific Gravity** | Relative density. The ratio of the density (mass of a unit volume) of a substance to the density of a given reference material. For liquids this is typically water at 4 degrees celcius | Numeric
| **Matter State** | Matter states | Enumeration
| **Analysis** | Used to specify analysis of a product (for example, nutrient or energy). | Array of [Analysis](#product-analysis)
| **Active Ingredients** | Array of active ingredients in the product| Array of [Active Ingredients](#active-ingredients)
| **Withdrawals** |The withdrawal periods of the product| Array of [Withdrawals](#withdrawals)
| **Claims** | Claims associated with the product | Array of [Identifiers](/resource-types/common.md#identifier) 
| **Registrations** | Registrations associated with the product | Array of [Identifiers](/resource-types/common.md#identifier) 

## Product Analysis

```json
{
    "name":"Nitrogen",
    "percent":40,
    "id":{
        "id":"string",
        "scheme":"string"
    }
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Name** | Name of the product analysis| String
| **Percent** | Proportion of the product analysis | Number
| **Id** | Identifier of this analysis | [Identifier](/resource-types/common.md#identifier) 

## Active Ingredients
An active ingredient of the product

```json
{
    "name":"string",
    "id":"string",
    "scheme":"string"
}
```

| Response Item | Description | Data Type |
|---------------|-------------|-----------|
| **Name** | Human readable name of the product | String
| **Id** | Official Id of the active ingredient | String
| **Scheme** |Scheme of the id of the active ingredient | String


## Withdrawals

The withdrawal period of the product

```json
{
    "scheme":"string",
    "hours":24
}
```

| Response Type | Description | Data Type |
|---------------|-------------|-----------|
| **Scheme** |The scheme controlling the withdrawal period rules | String
| **Hours** |Duration of the withdrawal period in hours | Number
