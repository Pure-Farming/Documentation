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

Get a list of plots that are linked to the provided holding id.

```
GET /data/holdings/{HoldingId}/plots/{PlotId}
```

---

## Response Structure

Plots are a field or a piece of land that is used for planting and reaping crops. Although it is smaller than the holdings but is a quite substantial piece of land. 

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
  "self": "string",
  "identifiers": [...],
  "links": [...],
  "name": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Crops** | Provides information on the crops that are currently being grown on a specific plot | Array of [Crops](#crop) |
| **Historic Crops** | Provides information on the crops that were historically grown on a specific plot | Array of [Historic Crops](#historic-crops) |
| **Activities** | Provides information on the various activities performed on a specific plot.  | Array of [Activities](#activity) |
| **Classifications** | Any classifications that an individual Plot may have | Array of [Classifications](#classification) |
| **Centroid** | This is the central point of the plot | GeoJSON Point |
| **Spatial Feature** | This is the GeoJson Feature that provides the Plot boundaries. | GeoJSON Feature |
| **Total Area** | The total area of the plot | [Total Area](/resource-types/common.md#total-area) |
| **Id** | The Pure Farming ID of the Plot. | String |
| **Meta** | Metadata about the Plot | [Metadata](/resource-types/common.md#metadata) |
| **Self** | A link to itself to allow for navigation | URL |
| **Identifiers** | Any identifiers for this Plot | Array of [Identifiers](/resource-types/common.md#identifier) |
| **Links** | Any links relevant to this Plot | Array of [Links](/resource-types/common.md#link) |
| **Name** | The name of the Plot, if present. | String |

---

## Crop

This provides information on the crops that are grown on a specific plot including their harvesting date, maturity date, name, etc.

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

## Historic Crops

Historic Crops have the same structure as that of a Crop, but the only difference is that it is not counted as a Crop.

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

## Activity

It provides information on the various activities performed on the plot. For instance, It can be plantation of a crop, harvesting, or some other such activity.

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
| **Id** | The Identifier for this Activity | [Identifier](/resource-types/common.md#identifier) |
| **IsPrimary** | Determines whether the Activity is the primary activity of the plot | Boolean |
| **Name** | The name of the Activity | String |
| **Productive Area** | The productive area relevant to this Activity | [Total Area](/resource-types/common.md#total-area) |

---

## Classification

It is the systematic arrangement of groups or categories based on certain characteristics or established criteria. Here it is Primary, Secondary, and Tertiary.

```json
{
  "primary": "string",
  "scheme": "string",
  "secondary": "string",
  "tertiary": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Primary** | The primary level of classification under the scheme. | String |
| **Scheme** | The scheme for this classification. This should be reverse DNS notation. | String |
| **Secondary** | The secondary level of classification under the scheme | String |
| **Tertiary** | The tertiary level of classification under the scheme. | String |
