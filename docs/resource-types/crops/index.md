---

title: Crops
menu_order: 1
post_status: publish
post_excerpt: Connected Data - Crops
taxonomy:
    category:
        - root
        - crops
    post_tag:
        - root
        - crops

---

# Resource Types: Crops

Below are the currently provided resource types for Crops.

- [Sample Analysis](/resource-types/crops/sample-analysis.md)
- [Sample Plans](/resource-types/crops/sample-plan.md)
- [Load Receivals](/resource-types/crops/load-receival.md)
- [Work Records](/resource-types/crops/work-record.md)

---

# Common Objects

- [Crop](#crop)

---

## Crop

A generic object containing the information about a crop being grown at a specific time.

```json
{
  "establishmentDate": "2022-09-13T10:51:55.898Z",
  "harvestDate": "2022-09-13T10:51:55.898Z",
  "identifiers": [
    {
      "id": "string",
      "scheme": "string"
    }
  ],
  "maturityDate": "2022-09-13T10:51:55.898Z",
  "name": "string",
  "taxonomicName": "string",
  "variety": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Establishment Date** | The date on which the Crop was planted | Date |
| **Harvest Date** | The date on which the Crop was harvested. | Date |
| **Identifiers** | Any identifiers for this Crop. | Array of [Identifiers](/resource-types/common.md#identifier) |
| **Maturity Date** | The date on which the Crop reached maturity | Date |
| **Name** | The name of the Crop if present. | String |
| **Taxonomic Name** | The scientific name for this Crop. | String |
| **Variety** | The variety of the Crop. | String |

---
