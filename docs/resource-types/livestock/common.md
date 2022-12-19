---

title: Common Livestock Objects
menu_order: 1
post_status: publish
post_excerpt: Common Livestock Data Objects
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Common Livestock Objects

- [Metadata](#metadata)
- [Embedded Animal Set](#embedded-animal-set)
- [Inventory Classification](#inventory-classification)

---

## Metadata

This provides metadata about a given object, including information about the creator, provenance and timestamps relating to its creation and modification.

```json
{ 
  "source": "string",
  "sourceId": "string",
  "isDeleted": "false",
  "created": "2022-07-06T10:11:21.460Z", 
  "creator": "string", 
  "modified": "2022-07-06T10:11:21.460Z", 
  "validFrom": "2022-07-06T10:11:21.460Z", 
  "validTo": "2022-07-06T10:11:21.460Z" 
} 
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Source** | Source where data is retrieved from. | URI |
| **SourceId** | Unique Id for the resource in the original source system. | UUID |
| **Is Deleted** | Indicating if this resource has been deleted in the source system. | Boolean | 
| **Created** | The date on which it was created | Date |
| **Creator** | The person responsible for creating the data | String |
| **Modified** | The date on which the data was updated | Date |
| **Valid From** | The timestamp from which this data is valid | Date/Time |
| **Valid To** | The date to which the data is valid (or `null` for always valid) | Date/Time |

---

## Embedded Animal Set
Specifies the set of animals as a list of member animal identifiers.

Embedded Animal Set object returns the following properties: 
```json
{
    "self": "string",
    "location": {...},
    "meta": {...},
    "resourceType": "/livestock/animal-set",
    "id": "string",
    "member":[{...}],
    "name": "string",
    "purpose": "string"
}
```
| Response Item | Description | Data Type |
|-|-|-|
| **Self** | A link to this specific Animal Set. | URI | 
| **Location** | An identifier for the location of the Animal Set. | [Identifier](/resource-types/common.md#identifier) |
| **Meta** | Meta data for the resource. | [Metadata](#metadata) | 
| **Resource Type** | The fixed discriminator for the Animal Set resource type. <br/>Value: /livestock/animal-set  | String | 
| **Id** | The *Pure Farming* Id of this Animal Set. | UUID |
| **Member** |  An identifier for the animal of the Animal Set. | Array of [Identifier](/resource-types/common.md#identifier) | 
| **Name** | Human readable name of the Animal Set. | String | 
| **Purpose**| Purpose of the Animal Set.</br>(Valid values: Enclosure, Feeding, Health, Lactation, Movement, Reproduction, Session, Other) | Enumeration |

---

## Inventory Classification
Describe the group of animals by their characteristics rather than animal identifiers.

Inventory Classification object returns the following properties: 

```json
{
    "birthPeriod": "string",
    "count": 10,
    "lactationStatus": "string",
    "name": "string",
    "primaryBreed": {...},
    "productionPurposes": [...],
    "reproductiveStatus": "string",
    "sex": "string",
    "species": "string"
}
```
| Response Item | Description | Data Type |
|-|-|-|
| **Birth Period** | The range of birth dates | String | 
| **Count** | The count or number of animals in this inventory classification | Number | 
| **Lactation Status** | The lactation status of animals</br>(Valid values: Dry, Lead, Fresh, Early, Lactating) | Enumeration |
| **Name** | Human-readable name for this inventory grouping | String |
| **Primary Breed** | Primary breed defined using an identifier and scheme | [Identifier](/resource-types/common.md#identifier) |
| **Production Purposes** | Defines the primary product that for which this animal is bred or kept </br>(Valid values: Meat, Milk, Wool)| Array of Enumeration |
| **Reproductive Status** | The reproductive/pregnancy status of animals </br>(Valid values: Open, Inseminated, Pregnant, NotPregnant, Birthed, DoNotBreed, PregnantMultipleFoetus)  | Enumeration |  
| **Sex** | The sex of animals </br>(Valid values: Female, FemaleNeuter, Male, MaleCryptorchid, MaleNeuter, Unknown) | Enumeration |
| **Species** | The species of animals </br>(Valid values: Buffalo, Cattle, Deer, Elk, Goat, Horse, Pig, Sheep)| Enumeration | 
 
