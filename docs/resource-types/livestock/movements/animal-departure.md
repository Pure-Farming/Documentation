---

title: Animal Departure
menu_order: 1
post_status: publish
post_excerpt: Animal - Departure
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: Animal-Departure

- [URLs]()
- [Response Structure]()

---

## URLs

Get all Departures that you have access to

```
GET /data/livestock/movement/animal-departures
```

Get the Departure for the specified id

```
GET /data/livestock/movement/animal-departures/{DepartureId}
```

Get all Departures that are linked to the provided holding id

```
GET /data/holdings/{HoldingId}/livestock/movement/animal-departures
```

Get the Departure for the specified id that is linked to the provided holding id

```
GET /data/holdings/{HoldingId}/livestock/movement/animal-departures/{DepartureId}
```

---

## Response Structure

A call to the Departures endpoints returns the following fields.

```json
{
  "self": "string",
  "location": {...},
  "animalDetailMeta": {...},
  "resourceType": "/livestock/movement/animal-departures",
  "consignment": {...},
  "responsable": "string",
  "contemporaryGroup": "string",
  "remark": "string",
  "traitLabel" : {...},
  "animal" : {...},
  "departureKind" : "string",
  "departureReason": "string",
  "eventDateTime" : "DateTimeOffset",
  "id": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
|**Self** | A link to this specific Departure | URI |
|**Location** | An identifier for the location of the Arrival | Identifier |
|**Animal Detail Meta** | Meta data for the resource | Metadata |
|**Resource Type** | The fixed discriminator for the animal departure resource type.<br/>Value: /livestock/movement/animal-departures  | String |
|**Consignment** | The consignment for this movement event | Consignment |
|**Responsable** | Whos responsable for this arrival | String |
|**ContemporaryGroup** | The Contemporary Group for this arrival | String |
|**Remark** | The Remark for this event | String |
|**Trait Label** | Something Trait Something | Identifier |
|**Animal** | The primary identifier for the animal | Identifier |
|**Departure Kind** | The kind of departure event (Valid values: Agistment, AgistmentReturn, Export, InternalTransfer, Newborn, Other, Sale, SaleReturn, Show, ShowReturn, Slaughter, StudService,
StudServiceReturn) | Enumeration |
|**Departure Reason** | The Reason for the departure (Valid values: Age, BadType, Behaviour, Fertility, Health, LegOrClaw, Mastitis, MilkingAbility, Newborn, Nutrition, Other, Parturition,
Production, Sale, Slaughter, Superfluous, Unknown) | Enumeration |
|**Event Date Time** | The time and date the event occured | DateTimeOffset |
|**Id** | The Pure Farming Id of this Departure | UUID |

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
