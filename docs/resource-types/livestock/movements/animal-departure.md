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
|**Self** | A link to this specific Animal Departure | URI |
|**Location** | An identifier for the location of the Animal Departure | Identifier |
|**Animal Detail Meta** | Meta data for the resource | Metadata |
|**Resource Type** | The fixed discriminator for the animal departure resource type.<br/>Value: /livestock/movement/animal-departures  | String |
|**Consignment** | Consignment information for a movement (arrival, departure). [See the Consignment definition](/resource-types/livestock/movements/consignment.md) | Consignment |
|**Responsable** | Use if an observation is manually recorded, or an event is carried out or authorised by a person. SHOULD be a person object. | String |
|**ContemporaryGroup** | For manually recorded events, record any contemporary group code that would affect statistical analysis. | String |
|**Remark** | A comment or remark field for additional user-specified information about the event. | String |
|**Trait Label** | If the event represents a formal trait, this identifies the recording system and trait. | Identifier |
|**Animal** | Unique animal scheme and identifier combination.| Identifier |
|**Departure Kind** | The kind of departure event (Valid values: Agistment, AgistmentReturn, Export, InternalTransfer, Newborn, Other, Sale, SaleReturn, Show, ShowReturn, Slaughter, StudService, StudServiceReturn) | Enumeration |
|**Departure Reason** | The Reason for the departure (Valid values: Age, BadType, Behaviour, Fertility, Health, LegOrClaw, Mastitis, MilkingAbility, Newborn, Nutrition, Other, Parturition,
Production, Sale, Slaughter, Superfluous, Unknown) | Enumeration |
|**Event Date Time** | The Time that this event occured | DateTimeOffset |
|**Id** | The Pure Farming Id of this Animal Departure | UUID |