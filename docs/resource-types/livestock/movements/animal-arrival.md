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
GET /data/livestock/movement/animal-arrivals/{ArrivalId}
```

Get all Arrivals that are linked to the provided holding id

```
GET /data/holdings/{HoldingId}/livestock/movement/animal-arrivals
```

Get the Arrival for the specified id that is linked to the provided holding id

```
GET /data/holdings/{HoldingId}/livestock/movement/animal-arrivals/{ArrivalId}
```

---

## Response Structure

A call to the Arrivals endpoints returns the following fields.

```json
{
  "self": "string",
  "location": {...},
  "meta": {...},
  "resourceType": "/livestock/movement/animal-arrivals",
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
|**Resource Type** | The fixed discriminator for the animal arrival resource type.<br/>Value: /livestock/movement/animal-arrivals  | String |
|**Consignment** | The consignment information for this movement event | Consignment |
|**Responsable** | Use if an observation is manually recorded, or an event is carried out or authorised by a person. SHOULD be a person object. | String |
|**ContemporaryGroup** | For manually recorded events, record any contemporary group code that would affect statistical analysis.| String |
|**Remark** | A comment or remark field for additional user-specified information about the event. | String |
|**Animal Id** | The main identifier for the animal | String |
|**Animal Scheme** | The scheme for the main identifier | String |
|**Animal Detail** | Core schema for representing animal. [See the Animal definition](/resource-types/livestock/animals.md).  | Animal Detail |
|**Arrival Reason** | The Reason for the arrival (Valid values: Purchase, Internal Transfer, Imported, Stud Service, Stud Service Return, Slaughter, Agistment, Agistment Return, Show, Show Return, Sale, Sale Return, Other) | Enumeration |
|**Id** | The Pure Farming Id of this Animal Arrival | UUID |

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