---

title: Dairy
menu_order: 1
post_status: publish
post_excerpt: Dairy
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: Dairy

- [URLs](#urls)
- [Response Structure]()

---

## URLs

Get all Milk Collections that you have access to

```
GET /data/dairy/milk-collections
```

Get the Milk Collection for the specified id

```
GET /data/dairy/milk-collection/{id}
```

Get all Milk Collections that are linked to the provided holding id

```
GET /data/holdings/{holdingId}/dairy/milk-collections
```

Get the Milk Collection for the specified id that is linked to the provided holding id

```
GET /data/holdings/{holdingId}/dairy/milk-collections/{id}
```

---

## Response Structure

A call to the Milk Collection endpoints returns the following fields.

```json
{
  "self": "string",
  "id": "string",
  "identifiers": [{...}],
  "links": [{...}],
  "meta": {...},
  "name": "string",
  "resourceType": "/dairy/milk-collection",
  "observationDate": "string",
  "holding": {...},
  "holdingId": "string",
  "source": {...},
  "destination": {...},
  "logisticUnit": "string",
  "quantity": "string",
  "units": "string",
  "rawQuantity": "string",
  "rawUnits": "string",
  "analysis": [{...}],
  "status": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
|**Self** | A link to this specific Milk Collection. | URI
|**Id** | The Pure Farming ExternalId of this Milk Collection. | UUID |
|**Identifiers** | Any identifier of this Milk Collection. | Array of [Identifiers](/resource-types/common.md#identifier) |
|**Links** | Used to define a relationship with another resource. | Array of [Link](/resource-types/common.md#link) |
|**Meta** | Meta data for the resource. | [Metadata](/resource-types/common.md#metadata)
|**Name** | A user-readable name for the resource. | String
|**Resource Type** | The fixed discriminator for the milk collection resource type.<br/>Value: /dairy/milk-collection  | String
|**Observation Date** | UTC Date (required) and time (optional) the milk collection was taken. | Date/Time
|**Holding** | The holding where the milk collection was recorded. | [Feature](/resource-types/common.md#feature)
|**Holding Id** | Internal purefarming holding id. To be used in internal versions of the schema, in place of the holding object (cannot have both, but valid to have neither!) | String
|**Source** | Source endpoint of the milk collection. | [Source](/resource-types/load-resource.md#source)
|**Destination** | Destination endpoint of the milk collection. | [Destination](/resource-types/load-resource.md#destination)
|**Logistic Unit** | Enumerated value of logistic units. (Valid values: Unknown, Tank, Field, Truck, Bale, Module) | Enumeration
|**Quantity** | Quantity in the milk collection. | String
|**Units** | Units for the quantity metric. | String
|**Raw Quantity** | Raw quantity before standardisation. | String
|**Raw Units** | Units for the raw quantity before standardisation. | String
|**Analysis** | The details of the analysis. | Array of [Analysis](/resource-types/load-resource.md#analysis)
|**Status** | The status of the milk collection. | String
---