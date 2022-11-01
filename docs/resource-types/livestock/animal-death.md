---

title: Animal Death
menu_order: 1
post_status: publish
post_excerpt: Animal - Death
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: Animal-Death

- [URLs]()
- [Response Structure]()

---

## URLs

Get all deaths that you have access to

```
GET /data/livestock/movement/animal-deaths
```

Get the death for the specified id

```
GET /data/livestock/movement/deaths/{DeathId}
```

Get all deaths that are linked to the provided holding id

```
GET /data/holdings/{HoldingId}/livestock/movement/deaths
```

Get the death for the specified holding that is linked to the provided death id

```
GET /data/holdings/{HoldingId}/livestock/movement/deaths/{DeathId}
```

---

## Response Structure

A call to the Deaths endpoints returns the following fields.

```json
{
  "self": "string",
  "location": {...},
  "meta": {...},
  "resourceType": "/livestock/movement/death",
  "consignment": {...},
  "responsable": "string",
  "contemporaryGroup": "string",
  "remark" : "string",
  "responsible" : "string",
  "traitLabel" : {...},
  "animalId": "string",
  "animalScheme": "string",
  "deathDate" : "DateTime",
  "deathReason" : "string",
  "deathMethod" : "string",
  "disposalMethod" : "string",
  "disposalOperator" : "string",
  "disposalReference" : "string",
  "explanation" : "string",
  "id": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
|**Self** | A link to this specific Death | URI
|**Location** | An identifier for the location of the Death | Identifier
|**Meta** | Meta data for the resource | Metadata
|**Resource Type** | The fixed discriminator for the animal death resource type.<br/>Value: /livestock/movement/death  | String
|**Consignment** | The consignment for this movement event | Consignment
|**Remark** | Something | String
|**Responsable** | Whos responsable for this arrival | String
|**Trait Label** | Something Trait Something | Identifier
|**ContemporaryGroup** | The Contemporary Group for this arrival | String
|**Animal Id** | The main identifier for the animal | String
|**Animal Scheme** | The scheme for the main identifier | String
|**Death Reason** | The reason for the death (Valid values: Missing, Parturition, Disease, Accident, Consumption, Culled, Other, Unknown, Age, Mastitis, Production, LegOrClaw, MilkingAbility
Nutrition, Fertility) | Enumeration
|**Death Method** | How the animal was killed (Valid values: Accident, Culled, Lost, Other, Perished, Slaughter, Theft) | Enumeration
|**Disposal Method** | How the animal was disposed of (Valid values: ApprovedService, Consumption, OnPremise, Other) | Enumeration
|**Disposal Operator** | Who disposed of the animal | String
|**Disposal Reference** | Reference for the disposal | String
|**Explanation** | Explanation | String
|**Id** | The Pure Farming Id of this Death | UUID |

---

### Consignment

Consignment are information about the transport of the animal in this event

```json
{
  "id": "string",
  "scheme": "string",
  "origin": {...},
  "destination": {...},
  "loadingDateTime": "DateTime",
  "unloadingDateTime": "DateTime",
  "expectedDuration": "double",
  "transportOperator": "string",
  "vehicle": "string",
  "transportReference": "string",
  "isolationFacilityUsed": "boolean",
  "farmAssuranceReferenceId": "string",
  "farmAssuranceReferenceScheme": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Id** |	The Id of this consignment | String |
| **Scheme** |	The Scheme of this consignment | String |
| **Origin** |	The Origin of this consignment | Location |
| **Destination** | The Destination of this consignment | Location |
| **Loading DateTime** | The time that the animals were loaded for this consignment | Date/Time |
| **Unloading DateTime** | The time that the animals were unloaded for this consignment | Date/Time |
| **Expected Duration** | The expected transport duration | Number |
| **Transport Operator** | The operator doing this consignment | String |
| **Vehicle** | The vehicle used for this consignment | String |
| **Transport Reference** | The Reference for this consignment | String |
| **Isolation Facility Used** | If an Isolation Facility was used as part of this consignment | Boolean |
| **Farm Assurance Reference Id** | The Farm Assurance Reference Id | String |
| **Farm Assurance Reference Scheme** | The Farm Assurance Reference Scheme | String |

---

### Location

A Location is an Origin or Destination for a consignment

```json
{
  "id": "string",
  "scheme": "string",
  "address": {...}
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Id** | The Id of the location | String |
| **Scheme** | The Scheme of the location | Number |
| **Address** | The postal address of this location | Address |

---

### Address

A address for a location

```json
{
  "country": "string",
  "locality": "string",
  "region": "string",
  "postOfficeBox": "string",
  "postCode": "string",
  "streetAddress": "string",
  "addressString": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Country** | The country part of the sdress | String |
| **Locality** | The locality part of the address | String |
| **Region** | The region for the address | String |
| **Post Office Box** | The post office box | String |
| **Post Code** | The post code | String |
| **Street Address** | The street address | String |
| **Address String** | The complete address | String |
