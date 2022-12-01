---

title: Holdings
menu_order: 1
post_status: publish
post_excerpt: Connected Data - Holdings
taxonomy:
    category:
        - root
        - core
    post_tag:
        - root
        - core

---

# Resource Type: Core – Holdings

- [URLs](#urls)
- [Response Structure](#response-structure)

---

## URLs

Get all holdings you have access to. 

```
GET /data/holdings
```

Get a specified holding. 

```
GET /data/holdings/{Id}
```

---

## Response Structure

Holdings are a representation of a working Farm, whether it be comprised of multiple areas of land (contiguous or non-contiguous) or not, it is represented as a Holding. An individual Holding may have spatial information, or may not, if present it may be a centroid (point), or spatial feature (feature) or both.

A call to the Holdings endpoint returns the following fields.

```json
{
  "featureCatalog": "string",
  "centroid": {...},
  "spatialFeature": {...},
  "totalArea": {...},
  "totalLength": {...},
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
| **Feature Catalog** | URL to a Feature Catalog that filtered to features that relate to the holding. | URI |
| **Centroid** | The center point of the Holding in relation to its Spatial Feature. This is a GeoJSON Point. | GeoJSON Point |
| **Spatial Feature** | The GeoJson Feature that provides the boundary of the holding.  | GeoJSON Feature |
| **Total Area** | The total area of the Holding. | [Total Area](/resource-types/common.md#total-area) |
| **Total Length** | The total length of all boundaries for this Holding. | [Total Length](/resource-types/common.md#total-length) |
| **Id** | The *Pure Farming* ID of the Holding. | UUID |
| **Meta** | This shows the metadata about the Holding | [Metadata](/resource-types/common.md#metadata) |
| **Self** | A link to itself, to allow navigation. | URL |
| **Identifiers** | Any identifiers for this Holding | Array of [Identifiers](/resource-types/common.md#identifier) |
| **Links** | Any links relevant to this Holding | Array of [Links](/resource-types/common.md#link) |
| **Name** | The name of the Holding | String |

