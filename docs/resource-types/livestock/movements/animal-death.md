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
|**Consignment** | Consignment information for a movement (arrival, departure). [See the Consignment definition](/resource-types/livestock/movements/consignment.md) | Consignment |
|**Death Method** | How the animal was killed (Valid values: Accident, Culled, Lost, Other, Perished, Slaughter, Theft) | Enumeration |
|**Death Reason** | The reason for the death (Valid values: Missing, Parturition, Disease, Accident, Consumption, Culled, Other, Unknown, Age, Mastitis, Production, LegOrClaw, MilkingAbility, Nutrition, Fertility) | Enumeration |
|**Disposal Method** | How the animal was disposed of (Valid values: ApprovedService, Consumption, OnPremise, Other) | Enumeration |
|**Disposal Operator** | Disposal operator official name (should really be schema.org/organization). | String |
|**Disposal Reference** | Reference (receipt, docket, or ID) for disposal. | String |
|**Explanation** | Free text explanation of the reason for death. | String |

