---

title: Plots
menu_order: 1
post_status: publish
post_excerpt: Connected Data - Plots
taxonomy:
    category:
        - root
        - core
    post_tag:
        - root
        - core

---

# Resource Type: Core – Plots

- [URLs](#urls)
- [Response Structure](#response-structure)

---

## URLs

Get all Plots that you have access to.

```
GET /data/plots
```

Get an individual Plot.

```
GET /data/plots/{id}
```

Get all plots that are linked to the provided holding id.

```
GET /data/holdings/{HoldingId}/plots
```

Get an individual plot based on the plot ID and it's holding ID
```
GET /data/holdings/{HoldingId}/plots/{PlotId}
```

---

## Response Structure

Plots are a field or a piece of land that is used for planting and reaping crops. A holding may have one or more pieces of land ("plots"). A plot will only have one holding that it is part of.

A call to the Plots endpoint returns the following fields:

```json
{
  "crops": [...],
  "historicCrops": [...],
  "activities": [...],
  "classifications": [...],
  "centroid": {...},
  "spatialFeature": {...},
  "totalArea": {...},
  "internalId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "id": "string",
  "meta": {...},
  "@self": "string",
  "identifiers": [...],
  "links": [...],
  "name": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Crops** | Information on the crops that are currently being grown on a specific plot | Array of [Crops](/resource-types/crops/index.md#crop) |
| **Historic Crops** | Information on the crops that were historically grown on a specific plot | Array of [Crops](/resource-types/crops/index.md#crop) |
| **Activities** | Information on the various activities performed on a specific plot  | Array of [Activities](#activity) |
| **Classifications** | Any classifications that an individual plot may have | Array of [Classifications](/resource-types/common.md#classification) |
| **Centroid** | The location of the center of the plot | GeoJSON Point |
| **Spatial Feature** | The plot boundaries | GeoJSON Feature |
| **Total Area** | The total area of the plot | [Total Area](/resource-types/common.md#total-area) |
| **Id** | The Pure Farming ID of the plot | String |
| **Meta** | Metadata about the plot | [Metadata](/resource-types/common.md#metadata) |
| **@Self** | A link to this specific plot record | URL |
| **Identifiers** | Any identifiers for this plot | Array of [Identifiers](/resource-types/common.md#identifier) |
| **Links** | Any links relevant to this plot | Array of [Links](/resource-types/common.md#link) |
| **Name** | The user-friendly name of the plot | String |

---

## Activity

Information on the various activities performed on the plot. 
For instance: planting a crop, harvesting, or some other such activity

```json
{
  "id": {
    "id": "string",
    "scheme": "string"
  },
  "isPrimary": true,
  "name": "string",
  "productiveArea": {
    "measurement": 123,
    "units": "MTK"
  }
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Id** | The Identifier for this activity | [Identifier](/resource-types/common.md#identifier) |
| **IsPrimary** | The activity is the primary activity of the plot | Boolean |
| **Name** | The user-friendly name of the activity | String |
| **Productive Area** | The productive area relevant to this activity | [Total Area](/resource-types/common.md#total-area) |
