---
title: Animal Group
menu_order: 1
post_status: publish
post_excerpt: Livestock - Animal Groups
taxonomy:
  category:
    - api
    - data
  post_tag:
    - api
---

# Resource Type: Livestock - Animal Group

- [URLs](#urls)
- [Response Structure](#response-structure)

---

## URLs

Get all Animal Group that you have access to

```
GET /data/livestock/animal-groups
```

Get a specific animal group

```
GET /data/livestock/animal-groups/{animalGroupId}
```

Get all animal groups associated with a holding

```
GET /data/holdings/{holdingId}/livestock/animal-groups
```

Get a single animal group associated with a holding

```
GET /data/holdings/{holdingId}/livestock/animal-groups/{animalGroupId}
```

---

## Response Structure

A call to the animal group endpoints returns the following fields.

```json
{
  "classification": {...},
  "id": "string",
  "self": "string",
  "location": {...},
  "meta": {...},
  "resourceType": "/livestock/animal-group"
}
```

| Response Item      | Description                                                                                    | Data Type                                               |
| ------------------ | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| **Classification** | The set of shared characteristics that defines the group of animals                            | [Classification](#classification)                       |
| **Id**             | The Pure Farming Id of this Animal Group                                                       | UUID                                                    |
| **Self**           | A link to this specific Animal Group                                                           | URI                                                     |
| **Location**       | An identifier for the location of the Animal Group                                             | [Identifier](/resource-types/common.md#identifier) |
| **Meta**           | Meta data for the resource                                                                     | [Metadata](/resource-types/common.md#metadata)     |
| **Resource Type**  | The fixed discriminator for the Animal Group resource type.<br/>Value: /livestock/animal-group | String                                                  |

---

### Classification

Animal group classification are...

```json
{
  "birthPeriod": "string",
  "count": 1,
  "lactationStatus": "string",
  "name": "string",
  "primaryBreed": {...},
  "productionPurposes": [...],
  "reproductiveStatus": "string",
  "sex": "string",
  "species": "string"
}
```

| Response Item           | Description                                                                                                                                                           | Data Type                                                |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| **Birth Period**        | The range of birth dates of this Animal Group                                                                                                                         | String                                                   |
| **Count**               | The count or number of animals in this inventory classification                                                                                                       | Number                                                   |
| **Lactation Status**    | The lactation status of animals. (Valid values: Dry, Lead, Fresh, Early, Lactating)                                                                                   | Enumeration                                              |
| **Name**                | Human-readable name for this inventory grouping                                                                                                                       | String                                                   |
| **Primary Breed**       | ICAR breed code for this Animal Group. For example:<br/>`{ "scheme": "ICAR2", "id": "AN" }`<br/>For more details, see also Reference Data Breeds - PureFarming DevHub | [Indentifier](/docs/resource-types/common.md#identifier) |
| **Production Purposes** | Defines the primary product that for which this animal is bred or kept. (Valid values: Meat, Milk, Wool)                                                              | Array of Enumeration                                     |
| **Reproductive Status** | The reproductive/pregnancy status of animals. (Valid values: Open, Inseminated, Pregnant, NotPregnant, Birthed, DoNotBreed, PregnantMultipleFoetus)                   | Enumeration                                              |
| **Sex**                 | The gender of animals. (Valid values: Female, FemaleNeuter, Male, MaleCryptorchid, MaleNeuter, Unknown)                                                               | Enumeration                                              |
| **Species**             | The species of animals. (Valid values: Buffalo, Cattle, Deer, Elk, Goat, Horse, Pig, Sheep)                                                                           | Enumeration                                              |
