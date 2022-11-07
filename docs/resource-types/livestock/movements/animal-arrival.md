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
|**Consignment** | Consignment information for a movement (arrival, departure). | Consignment |
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
| **Loading DateTime** | A particular point in the progression of time. Shall be UTC format with Z, specified in RFC3339 (see https://ijmacd.github.io/rfc3339-iso8601/ for format guidance). | Date/Time |
| **Unloading DateTime** | A particular point in the progression of time. Shall be UTC format with Z, specified in RFC3339 (see https://ijmacd.github.io/rfc3339-iso8601/ for format guidance). | Date/Time |
| **Expected Duration** | Expected duration of transportation in hours. | Number |
| **Transport Operator** | Transport operator official name (should really be schema.org/organization).| String |
| **Vehicle** | Identification of the vehicle (for example, licence plate). | String |
| **Transport Reference** | Shipping or transporter reference.| String |
| **Isolation Facility Used** | True if an isolation facility was used for the movement. | Boolean |
| **Farm Assurance Reference Id** | A unique identification for the resource issued under the auspices of the scheme. | String |
| **Farm Assurance Reference Scheme** | The identifier (in reverse domain format) of an official scheme that manages unique identifiers. | String |

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
| **Country** | The country. For example, USA. You can also provide the two-letter ISO 3166-1 alpha-2 country code. | String |
| **Locality** | The locality in which the street address is, and which is in the region. For example, Mountain View. | String |
| **Region** | The region in which the locality is, and which is in the country. For example, California or another appropriate first-level Administrative division | String |
| **Post Office Box** | The post office box number for PO box addresses. | String |
| **Post Code** | The postal code. For example, 94043. | String |
| **Street Address** | The street address. For example, 1600 Amphitheatre Pkwy. | String |
| **Address String** | The complete address | String |