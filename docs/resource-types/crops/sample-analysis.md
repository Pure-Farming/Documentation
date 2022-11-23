---

title: Sample Analysis
menu_order: 1
post_status: publish
post_excerpt: Crops - Sample Analysis
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: Crops – Sample Analysis

- [URLs](#urls)
- [Response Structure](#response-structure)

## URLs
Get all sample analyses that you have access to for a given Holding, the HoldingId is required in this case. 

```
GET /data/holdings/{HoldingId}/crops/sample-analyses 
```

Get an individual sample analysis for a given holding, both the HoldingId and Id of the sample analysis are required. 

```
GET /data/holdings/{HoldingId}/crops/sample-analyses/{Id} 
```

## Sample Analysis
A call to the Sample analyses endpoint returns the following fields: 

```json
{ 

  "operation": "string", 
  "status": 0, 
  "analysis": [ … ], 
  "priority": 0, 
  "sampledOrganism": "string", 
  "samplingMethod": "string", 
  "id": "string", 
  "meta": { … }, 
  "observationDate": "2022-07-07T12:52:56.227Z", 
  "feature": { … }, 
  "featureId": "3fa85f64-5717-4562-b3fc-2c963f66afa6", 
  "holding": { … }, 
  "holdingId": "3fa85f64-5717-4562-b3fc-2c963f66afa6", 
  "phenomenonTime": "string", 
  "remark": "string", 
  "responsible": "string", 
  "internalId": "3fa85f64-5717-4562-b3fc-2c963f66afa6", 
  "self": "string", 
  "identifiers": [ … ], 
  "links": [ … ], 
  "name": "string" 
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Operation** | The operation of the Sample | String |
| **Status** | The status of the Sample analyses | Enumeration |
| **Analysis** | The details of the analysis | Array of [Analysis](/resource-types/load-resource.md#analysis) |
| **Priority** | This is the priority of this sample analyses. It can be high, immediately, low, medium, as soon as possible. | Enumeration |
| **Sampled Organism** | The crop that was sampled. | String |
| **Sampling Method** | The method used for the sampling | String |
| **Id** | The Id of the Sample analyses | UUID |
| **Meta** | Metadata about the Sample analyses | Metadata |
| **Observation Date** | The date of the Sample analyses | Date |
| **Feature** | The feature that this Sample analyses is linked to | [Feature](/resource-types/common.md/#feature)  |
| **Feature Id** | The identifier for the Feature that this sample analyses is linked to | UUID |
| **Holding** | The Holding that this Sample Plan is linked to | [Feature](/resource-types/common.md/#feature)  |
| **Holding Id** | The Identifier for the Holding | UUID |
| **Phenomenon Time** | The time when the sample analyses was done | Date/Time |
| **Remark** | Any remarks recorded against this analyses | String |
| **Responsible** | The person responsible for this Sample analyses | String |
| **Self** | A link to the specific Sample analyses | URL |
| **Identifiers** | Any identifiers for this Sample analyses | Array of Identifiers |
| **Links** | Any links relevant to this Sample analyses | Array of Links |
| **Name** | It is the name of the sample analyses | String |
