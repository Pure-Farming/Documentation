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

Get all Arrivals that you have access to

```
GET /data/livestock/movement/animal-arrivals
```

Get the Arrival for the specified id

```
GET /data/livestock/movement/arrivals/{id}
```

Get all Arrivals that are linked to the provided animal id

```
GET /data/livestock/animals/{animalId}/arrivals
```

Get the Arrival for the specified id that is linked to the provided animal id

```
GET /data/livestock/animals/{animalId}/arrivals/{arrivalId}
```

---

## Response Structure

A call to the Arrivals endpoints returns the following fields.

```json
{
  "self": "string",
  "location": {...},
  "meta": {...},
  "resourceType": "/livestock/movement/arrival",
  "consignment": {...},
  "responsable": "string",
  "contemporaryGroup": "string",
  "remark": "string",
  "animalId": "string",
  "animalScheme": "string",
  "arrivalReason": "string",
  "id": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
|**Self** | A link to this specific Animal | URI
|**Location** | An identifier for the location of the Animal | Identifier
|**Meta** | Meta data for the resource | Metadata
|**Resource Type** | The fixed discriminator for the animal arrival resource type.<br/>Value: /livestock/movement/arrival  | String
|**Consignment** | The consignment for this movement event | Consignment
|**Responsable** | The date of birth of this Animal | Date/Time
|**ContemporaryGroup** | The breed fractions for this Animal | Breed Fractions
|**Remark** | The color of this Animal’s coat | String
|**Animal Id** | The color of this Animal’s coat using a national or breed-defined scheme and identifier | Identifier
|**Animal Scheme** | The gender of this Animal. (Valid values: Female, FemaleNeuter, Male, MaleCryptorchid, MaleNeuter, Unknown) | Enumeration
|**Arrival Reason** | The health status of this Animal. (Valid values: Healthy, Suspicious, Ill, InTreatment, ToBeCulled) | Enumeration
|**Id** | The Pure Farming Id of this Animal | UUID |

---

### Consignment

Consignment are …

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
| **Id** |	The Id of this consignment | string |
| **Scheme** |	The Scheme of this consignment | string |
| **Origin** |	The Origin of this consignment | Location |
| **Destination** | The Destination of this consignment | Location |
| **Loading DateTime** | The time that the animals were loaded for this consignment | DateTime |
| **Unloading DateTime** | The time that the animals were unloaded for this consignment | DateTime |
| **Expected Duration** | The expected transport duration | Number |
| **Transport Operator** | The operator doing this consignment | string |
| **Vehicle** | The vehicle used for this consignment | string |
| **Transport Reference** | The Reference for this consignment | string |
| **Isolation Facility Used** | If an Isolation Facility was used as part of this consignment | boolean |
| **Farm Assurance Reference Id** | | string |
| **Farm Assurance Reference Scheme** | | string |

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
| **Id** | The Id of the location | string |
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
| **Country** | The gender of this Animal. (Valid values: Female, FemaleNeuter, Male, MaleCryptorchid, MaleNeuter, Unknown) | Enumeration |
| **Locality** | The identifier of this Animal | Identifier |
| **Region** | Official herd-book name for this Animal | String |
| **Post Office Box** | The identifier for the child of the Animal | Identifier |
| **Post Code** | Identifies the type of parent. (Valid values: Genetic, Recipient, Adoptive) | Enumeration |
| **Street Address** | | string |
| **Address String** | | string |
