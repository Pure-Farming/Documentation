---
title: Group Treatment Event
menu_order: 1
post_status: publish
post_excerpt: Livestock - Group Treatment Event
taxonomy:
  category:
    - api
    - data
  post_tag:
    - api
---

# Resource Type: Livestock - Group Treatment Event

- [URLs](#urls)
- [Response Structure](#response-structure)

---

## URLs

Get all group treatment events that you have access to

```
GET /data/livestock/treatments/group-events
```

Get a single group treatment event

```
GET /data/livestock/treatments/group-events/{TreatmentId}
```

Get all group treatment events associated with a holding

```
GET ​/data/holdings/{holdingId}/livestock/treatments/group-events
```

Get a single group treatment event associated with a holding

```
GET /data/holdings/{holdingId}/livestock/treatments/group-events/{treatmentId}
```

---

## Response Structure

A call to the group treatment event endpoints returns the following fields:

```json
{
    "resourceType": "/livestock/treatment/group-treatment-event",
    "@self": "string",
    "id": "string",
    "eventDateTime": "2022-09-05T06:06:00.000Z",
    "meta": {...},
    "location": {...},
    "responsible": "string",
    "traitLabel": {...},
    "remark": "string",
    "contemporaryGroup": "string",
    "countObserved": 3,
    "groupMethod": "string",
    "embeddedAnimalSet": {...},
    "inventoryClassification": {...},
    "medicine": {...},
    "procedure": "string",
    "site": "string",
    "positions": [{...}],
    "withdrawals": [{...}],
    "batches": [{...}],
    "dosePerAnimal": {...},
    "totalMedicineUsed": {...}
}
```

| Response Item                | Description                                                                                                               | Data Type                                             |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| **Resource Type**            | The fixed discriminator for the Animal Group resource type.<br/>Value: /livestock/treatment/group-treatment-event         | String                                                |
| **Self**                     | A link to this specific Group Treatment Event                                                                             | URI                                                   |
| **Id**                       | The Pure Farming Id of this Group Treatment Event                                                                         | UUID                                                  |
| **Location**                 | An identifier for the location of the Group Treatment Event                                                               | [Identifier](/resource-types/common.md#identifier)    |
| **Meta**                     | Meta data for the resource                                                                                                | [Metadata](/resource-types/livestock/common.md#metadata)        |
| **Event Date Time**          | The time the event occurred                                                                                                | Datetime                                              |
| **Responsible**              | Use if an observation is manually recorded, or an event is carried out or authorised by a person                          | String                                                |
| **Trait Label**              | Represents a formal trait, identifies the recording system and trait                                                      | [Identifier](/resource-types/common.md#identifier)    |
| **Remark**                   | A comment or remark field for additional user-specified information about the event                                       | String                                                |
| **Contemporary Group**       | A contemporary group code that would affect statistical analysis                                                          | String                                                |
| **Count Observed**           | The number of animals observed in the event                                                                             | Number                                                |
| **Group Method**             | Indicates whether the event references an existing animal set, has an embedded animal set, an inventory classification or both an inventory classification and animal set | Enumeration                                           |
| **Embedded Animal Set**      | Specifies the set of animals as a list of member animal identifiers                                                       | [Embedded Animal Set](#embedded-animal-set)           |
| **Inventory Classification** | Describe the group of animals by their characteristics rather than animal identifiers                                     | [Inventory Classification](#inventory-classification) |
| **Medicine**                 | A reference to the medicine used (where applicable)                                                                       | [Medicine](#medicine)                                 |
| **Procedure**                | Medicine application method or a non-medicine procedure                                                                   | String                                                |
| **Site**                     | Body site where the treatment was administered                                                                            | String                                                |
| **Positions**                | The possible positions for treatment or diagnosis                                                                         | Array of Enumeration                                  |
| **Withdrawals**              | Withholding details for the treatment administered                                                                        | [Withdrawals](#withdrawals)                           |
| **Batches**                  | Batches and expiry details for the medicine administered                                                                  | [Batches](#batches)                                   |
| **Dose Per Animal**          | The actual or average medicine dose administered per animal                                                               | [Dosage](#dosage)                                     |
| **Total Medicine Used**      | The total amount of medicine used                                                                                         | [Dosage](#dosage)                                     |

---

### Medicine

The medication used for treatment of the animals

```json
{
  "identifier": {...},
  "name": "string",
  "registeredIdentifier": {...},
  "approved": "string",
  "reltype": "string",
  "href": "string"
}
```

| Response Item             | Description                                                                                                                     | Data Type                                                   |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| **Identifier**            | Identifies a resource                                                                                                           | [Identifier](/resource-types/common.md#identifier)          |
| **Name**                  | Name of the medicine or remedy given for this treatment                                                                         | String                                                      |
| **Registered Identifier** | Identifies a medicine registraton with a national Scheme and a registered ID within that scheme                                 | Array of [Identifier](/resource-types/common.md#identifier) |
| **Approved**              | An indicator whether the medicine or remedy is an approved medicine                                                             | String                                                      |
| **Reltype**               | Defines the relationship between the current resource and the referenced resource. Defined in well-known/relationshipCatalog.md | String                                                      |
| **Href**                  | Where provided, this is the URI to the medication information page                                                              | URI                                                         |

---

### Withdrawals

Withholding details for the treatment administered

```json
[
  {
    "productType": "string",
    "endDate": "2022-10-31T17:06:00.000Z",
    "market": "string"
  }
]
```

| Response Item    | Description                                                                                             | Data Type   |
| ---------------- | ------------------------------------------------------------------------------------------------------- | ----------- |
| **Product Type** | Product or food item affected by this withdrawal                                                        | Enumeration |
| **End Date**     | The end date for this withholding period                                                                | Datetime    |
| **Market**       | The market to which the withdrawal applies, using a scheme such as au.gov.apvma.esi or au.gov.apvma.whp | String      |

---

### Batches

Batches and expiry details for the medicine administered

```json
[
  {
    "identifier": "string",
    "expiryDate": "2024-06-16T00:00:00.000Z"
  }
]
```

| Response Item   | Description                       | Data Type |
| --------------- | --------------------------------- | --------- |
| **Identifier**  | The ID, batch or lot number       | String    |
| **Expiry Date** | The expiry date of the medication | Datetime  |

---

### Dosage

Dose per Animal in Group Treatment Event are...

```json
{
  "doseQuantity": 27.5,
  "doseUnits": "string"
}
```

| Response Item     | Description                                     | Data Type   |
| ----------------- | ----------------------------------------------- | ----------- |
| **Dose Quantity** | Quantity of medicine or product administered    | Number      |
| **Dose Units**    | Units of measurement in UN/CEFACT 3-letter form | Enumeration |
