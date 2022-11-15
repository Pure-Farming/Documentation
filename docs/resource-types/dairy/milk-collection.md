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

- [URLs]()
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

A call to the Animals endpoints returns the following fields.

```json
{
  "self": "string",
  "location": {...},
  "meta": {...},
  "resourceType": "/livestock/animal",
  "alternativeIdentifiers": [{...}],
  "birthDate": "string",
  "breedFractions": {...},
  "coatColor": "string",
  "coatColorIdentifier": {...},
  "gender": "string",
  "healthStatus": "string",
  "identifier": {...},
  "lactationStatus": "string",
  "managementTag": "string",
  "name": "string",
  "officialName": "string",
  "parentage": [{...}],
  "primaryBreed": {...},
  "productionPurpose": "string",
  "reproductionStatus": "string",
  "specie": "string",
  "status": "string",
  "id": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
|**Self** | A link to this specific Milk Collection | URI
|**ExternalId** | The Pure Farming ExternalId of this Milk Collection | UUID |

---