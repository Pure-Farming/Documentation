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
| **Analysis** | The details of the analysis | Array of Analysis |
| **Priority** | This is the priority of this sample analyses. It can be high, immediately, low, medium, as soon as possible. | Enumeration |
| **Sampled Organism** | The crop that was sampled. | String |
| **Sampling Method** | The method used for the sampling | String |
| **Id** | The Id of the Sample analyses | UUID |
| **Meta** | Metadata about the Sample analyses | Metadata |
| **Observation Date** | The date of the Sample analyses | Date |
| **Feature** | The feature that this Sample analyses is linked to | Feature |
| **Feature Id** | The identifier for the Feature that this sample analyses is linked to | UUID |
| **Holding** | The Holding that this Sample Plan is linked to | Feature |
| **Holding Id** | The Identifier for the Holding | UUID |
| **Phenomenon Time** | The time when the sample analyses was done | Date/Time |
| **Remark** | Any remarks recorded against this analyses | String |
| **Responsible** | The person responsible for this Sample analyses | String |
| **Self** | A link to the specific Sample analyses | URL |
| **Identifiers** | Any identifiers for this Sample analyses | Array of Identifiers |
| **Links** | Any links relevant to this Sample analyses | Array of Links |
| **Name** | It is the name of the sample analyses | String |

## Analysis

It provides all the information about the analysis that was done including the laboratory where the analysis was performed, the results of the analysis, etc. 

```json
{ 
  "laboratory": { … }, 
  "laboratoryIdentifier": "string", 
  "responsible": "string", 
  "results": [ … ], 
  "sessionIdentifier": "string" 
} 
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Analysis** | The details of the analysis. | String |
| **Laboratory** | Information about the laboratory where the sample analysis was done | Laboratory |
| **Laboratory Identifier** | The identifier of the laboratory that performed the analysis | String |
| **Responsible** | The person responsible for taking the analysis | String |
| **Results** | This shows the results of the analysis | Array of Analysis Result |
| **Session Identifier** | It provides information about the batch of samples that was analysed | String |

## Laboratory

It provides information about the laboratory where the sample analysis was done including the leiCode of the laboratory, its URI, etc. 

```json
{ 
  "registration": { 
    "additionalProp1": "string", 
    "additionalProp2": "string", 
    "additionalProp3": "string" 
  }, 
  "leiCode": "string", 
  "name": "string", 
  "uri": "string", 
  "globalLocationNumber": "string" 
} 
```


| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Registration** | This shows any additional property that relates to the registration. It can be { “hello”: “world”, “bob”: “smith”, “value”: -1 } | Object |
| **LEI Code** | The legal entity identifier code of the laboratory | String |
| **Name** | It is the name of the laboratory | String |
| **URI** | The uniform resource identifier for this laboratory | String |
| **Global** | Location Number	It is the global location number of the laboratory | String |


## Analysis Result

It shows the results of a sample analysis that was done on a given crop. 

```json
{ 
  "abbreviation": "string", 
  "errorStatistic": 0, 
  "method": "string", 
  "metric": "string", 
  "name": "string", 
  "rawUnit": "string", 
  "rawValue": 0, 
  "resolution": 0, 
  "status": 0, 
  "unit": "string", 
  "value": 0 
} 
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Abbreviation** | The abbreviation for that particular result | String |
| **Error statistic** | It shows the statistical errors in the results | Numeric |
| **Method** | This describes the URI of the method | URI |
| **Metric** | It is the URI to the metric that the result represents | URI |
| **Name** | The name of test | String |
| **Raw Unit** | The raw unit of the data. | String |
| **Raw value** | The raw value of the data. | Numeric |
| **Resolution** | Where the values are numeric, it describes how many decimal places they are recorded. For instance, the resolution can be 4, which demonstrates that the value should be to 4 decimal places. | Numeric |
| **Status** | This shows the status of the sample analyses that were done on the crop that was received. The status can be completed, inProgress, notDetected, outOfBounds, scheduled | Enumeration |
| **Unit** | The standard unit of measurement. | String |
| **Value** | The value determined after it has been converted into the standardised unit. | String |