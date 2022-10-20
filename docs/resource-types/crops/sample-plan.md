---

title: Sample Plan
menu_order: 1
post_status: publish
post_excerpt: Crops - Sample Plan
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: Crops – Sample Plan

- [URLs](#urls)
- [Response Structure](#response-structure)

## URLs

Get all sample plans that you have access to for a given Holding, the HoldingId is required in this case. 

```
GET /data/holdings/{HoldingId}/crops/sample-plans
```

Get an individual sample plan for a given holding, both the HoldingId and the Id of the sample plan are required. 

```
GET /data/holdings/{HoldingId}/crops/sample-plans/{Id} 
```

## Response Structure

A call to the Sample Plan endpoint returns the following fields: 

```json
{ 
  "operation": "string", 
  "status": “string”, 
  "priority": 0, 
  "sampledOrganism": "string", 
  "samplingMethod": "string", 
  "id": "string", 
  "meta": { … }, 
  "observationDate": "2022-07-07T12:19:13.493Z", 
  "feature": { … }, 
  "holding": { … }, 
  "phenomenonTime": "string", 
  "remark": "string", 
  "responsible": "string", 
  "self": "string", 
  "identifiers": [ … ], 
  "links": [ … ], 
  "name": "string" 
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Operation** | The operation of the Sample | String |
| **Status** | The status of the Sample Plan | Enumeration |
| **Priority** | The priority of the Sample Plan, with possible values: immediately, soonAsPossible, high, medium, low | Enumeration |
| **Sampled Organism** | The organism that is planned to be sampled |  String |
| **Sampling Method** | The method used for the sampling | String |
| **Id** | The Id of the Sample Plan | UUID |
| **Meta** | Metadata about the Sample Plan | Metadata |
| **Observation Date** | The date of the Sample Plan | Date |
| **Feature** | The feature that this Sample Plan is linked to | Feature |
| **Holding** | The Holding that this Sample Plan is linked to | Feature |
| **Phenomenon Time** | The time that the Sample is due to be taken | Date/Time |
| **Remark** | Any remarks recorded against this planned sample | String |
| **Responsible** | The person responsible for this Sample Plan | String |
| **Self** | A link to the specific Sample Plan | URI |
| **Identifiers** | Any identifiers for this Sample Plan | Array of Identifiers |
| **Links** | Any links relevant to this Sample Plan | Array of Links |
| **Name** | This is the name of the sample plan | String |