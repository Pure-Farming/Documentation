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
| **Resource Type** | The fixed discriminator for the Animal Birth Registration resource type. <br/>Value: /crop/work-record | String
|**Id** |The Pure Farming Id of this Work Record |UUID            |
| **Operation** | Constant value in any concrete class for the operation type | String |
| **Status** | Allowable statuses of a work item | Enumeration |
| **Priority** | Allowable priorities of a work item | Enumeration |
| **Meta** |Meta data for the resource. |Metadata |