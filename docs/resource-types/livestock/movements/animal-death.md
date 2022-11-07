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
GET /data/livestock/movement/animal-deaths/{DeathId}
```

Get all deaths that are linked to the provided holding id

```
GET /data/holdings/{HoldingId}/livestock/movement/animal-deaths
```

Get the death for the specified holding that is linked to the provided death id

```
GET /data/holdings/{HoldingId}/livestock/movement/animal-deaths/{DeathId}
```

---

## Response Structure

A call to the Deaths endpoints returns the following fields.

```json
{
  "self": "string",
  "location": {...},
  "meta": {...},
  "resourceType": "/livestock/movement/animal-deaths",
  "contemporaryGroup": "string",
  "eventDateTime": "DateTimeOffset",
  "id": "string",
  "remark" : "string",
  "responsible" : "string",
  "traitLabel" : {...},
  "animal" : {...},
  "consignment": {...},
  "deathMethod" : "string",
  "deathReason" : "string",
  "disposalMethod" : "string",
  "disposalOperator" : "string",
  "disposalReference" : "string",
  "explanation" : "string",
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
|**Self** | A link to this specific Animal Death | URI |
|**Location** | An identifier for the location of the Animal Death | Identifier |
|**Meta** | Meta data for the resource | Metadata |
|**Resource Type** | The fixed discriminator for the animal death resource type.<br/>Value: /livestock/movement/death  | String |
|**ContemporaryGroup** | For manually recorded events, record any contemporary group code that would affect statistical analysis. | String |
|**Event Date Time**| The Time that this event occured | DateTimeOffset |
|**Id** | The Pure Farming Id of this death event | UUID |
|**Remark** | A comment or remark field for additional user-specified information about the event. | String |
|**Responsable** | Use if an observation is manually recorded, or an event is carried out or authorised by a person. SHOULD be a person object. | String |
|**Trait Label** | If the event represents a formal trait, this identifies the recording system and trait.| Identifier |
|**Animal** | Unique animal scheme and identifier combination. | Identifier |
|**Consignment** | Consignment information for a movement (arrival, departure). | Consignment |
|**Death Method** | How the animal was killed (Valid values: Accident, Culled, Lost, Other, Perished, Slaughter, Theft) | Enumeration |
|**Death Reason** | The reason for the death (Valid values: Missing, Parturition, Disease, Accident, Consumption, Culled, Other, Unknown, Age, Mastitis, Production, LegOrClaw, MilkingAbility
Nutrition, Fertility) | Enumeration |
|**Disposal Method** | How the animal was disposed of (Valid values: ApprovedService, Consumption, OnPremise, Other) | Enumeration |
|**Disposal Operator** | Disposal operator official name (should really be schema.org/organization). | String |
|**Disposal Reference** | Reference (receipt, docket, or ID) for disposal. | String |
|**Explanation** | Free text explanation of the reason for death. | String |

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
