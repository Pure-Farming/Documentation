---

title: Load Resource Common Objects
menu_order: 1
post_status: publish
post_excerpt: Load Resource Common Objects
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Load Resource Common Objects

- [Source](#source)
- [Destination](#destination)
- [Analysis](#analysis)
- [Laboratory](#laboratory)
- [Analysis Result](#analysis-result)

---

### Source

This represents an individual load that has been received.

```json
{ 
  "consignmentDate": "2022-07-08T07:24:20.249Z", 
  "feature": { … }, 
  "organisation": { … } 
} 
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Consignment date** | The date on which the load arrived at a location | Date |
| **Feature** | The feature that this load is linked to | [Feature](/resource-types/common.md/#feature)  |
| **Organisation** | The organisation that this source belongs to | Organisation |

---

### Destination

This provides all the details about the destination of the load. 

```json
{ 
  "consignmentDate": "2022-07-08T07:24:20.249Z", 
  "feature": { …  }, 
  "organisation": { … } 
} 
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Consignment date** | The date on which the load arrived at a location | Date |
| **Feature** | The feature that this load is linked to | [Feature](/resource-types/common.md/#feature)  |
| **Organisation** | The organisation that this destination belongs to | Organisation |

---

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
| **Laboratory** | Information about the laboratory where the analysis was done | Laboratory |
| **Laboratory Identifier** | The identifier of the laboratory that performed the analysis | String |
| **Responsible** | The person responsible for taking the analysis | String |
| **Results** | This shows the results of the analysis | Array of Analysis Result |
| **Session Identifier** | It provides information about the batch of samples that was analysed | String |

## Laboratory

It provides information about the laboratory where the analysis was done including the leiCode of the laboratory, its URI, etc. 

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

It shows the results of a analysis that was done on a given crop. 

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
| **Status** | This shows the status of the analyses that were done on the crop that was received. The status can be completed, inProgress, notDetected, outOfBounds, scheduled | Enumeration |
| **Unit** | The standard unit of measurement. | String |
| **Value** | The value determined after it has been converted into the standardised unit. | String |