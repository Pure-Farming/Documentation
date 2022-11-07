---

title: Animal Arrival
menu_order: 1
post_status: publish
post_excerpt: Animal - Arrival
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: Animal-Arrival

- [URLs]()
- [Response Structure]()

---

## URLs

Get all animal arrival events that you have access to.

```
GET /data/livestock/movement/animal-arrivals
```

Get an individual animal arrival event for the specified id. 

```
GET /data/livestock/movement/animal-arrivals/{ArrivalId}
```

Get all animal arrival events that are linked to the provided holding id.

```
GET /data/holdings/{HoldingId}/livestock/movement/animal-arrivals
```

Get an individual animal arrival event for a given holding. 

```
GET /data/holdings/{HoldingId}/livestock/movement/animal-arrivals/{ArrivalId}
```

---

## Response Structure

A call to the animal arrival endpoints returns the following fields.

```json
{
  "self": "string",
  "location": {...},
  "meta": {...},
  "resourceType": "/livestock/movement/animal-arrival",
  "consignment": {...},
  "responsable": "string",
  "contemporaryGroup": "string",
  "remark": "string",
  "animalId": "string",
  "animalScheme": "string",
  "animalDetail" : {...},
  "arrivalReason": "string",
  "id": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
|**Self** | A link to this specific Animal Arrival | URI |
|**Location** | An identifier for the location of the Animal Arrival.| Identifier |
|**Meta** | Meta data for the resource | Metadata |
|**Resource Type** | The fixed discriminator for the animal arrival resource type.<br/>Value: /livestock/movement/animal-arrival  | String |
|**Consignment** | Consignment information for a movement (arrival, departure). [See the Consignment definition](/resource-types/livestock/movements/consignment.md) | Consignment |
|**Responsable** | Use if an observation is manually recorded, or an event is carried out or authorised by a person. SHOULD be a person object. | String |
|**ContemporaryGroup** | For manually recorded events, record any contemporary group code that would affect statistical analysis.| String |
|**Remark** | A comment or remark field for additional user-specified information about the event. | String |
|**Animal Id** | The main identifier for the animal | String |
|**Animal Scheme** | The scheme for the main identifier | String |
|**Animal Detail** | Core schema for representing animal. [See the Animal definition](/resource-types/livestock/animals.md).  | Animal Detail |
|**Arrival Reason** | The Reason for the arrival (Valid values: Purchase, Internal Transfer, Imported, Stud Service, Stud Service Return, Slaughter, Agistment, Agistment Return, Show, Show Return, Sale, Sale Return, Other) | Enumeration |
|**Id** | The Pure Farming Id of this Animal Arrival | UUID |