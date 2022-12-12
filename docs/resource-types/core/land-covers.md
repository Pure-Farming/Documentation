---

title: Land Covers
menu_order: 1
post_status: publish
post_excerpt: Connected Data - Land Covers
taxonomy:
    category:
        - root
        - core
    post_tag:
        - root
        - core

---

# Resource Type: Core – Land Covers

- [URLs](#urls)
- [Response Structure](#response-structure)

---

## URLs

Get all Plots that you have access to.

```
GET /data/land-covers
```

Get an individual Land Cover.

```
GET /data/land-covers/{id}
```

Get all land covers that are linked to the provided holding id.

```
GET /data/holdings/{HoldingId}/land-covers
```

Get an individual land cover based on the land cover ID and it's holding ID
```
GET /data/holdings/{HoldingId}/land-covers/{LandCoverId}
```

---

## Response Structure

Land Covers are 

A call to the Land Covers endpoint returns the following fields:  

```json
{
  "classificationDescription": "string",
  "eligibility": {...},
  "landCoverClassification": {...},
  "activities": [...],
  "classifications": [...],
  "centroid": {...},
  "spatialFeature": {...},
  "totalArea": {...},
  "totalLength": {...},
  "id": "string",
  "meta": {...},
  "self": "string",
  "identifiers": [...],
  "links": [...],
  "name": "string",
  "resourceType": "/core/land-cover"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Classification Description** |   | String |
| **Eligibility** | The eligibility classification of this Land Cover | [Eligibility](#eligibility) |
| **Land Cover Classification** | The classification of this Land Cover | [Classification](/resource-types/common#classification) |
| **Activities** | Any activities recorded on this Land Cover | [Activity](#activity) |
| **Classifications** | The classifications of this Land Cover | Array of [Classifications](/resource-types/common#classification) |
| **Centroid** | A GeoJSON Point representing the center of the Land Cover | GeoJSON Point |
| **Spatial Feature** | A GeoJSON Feature representing this Land Cover | GeoJSON Feature |
| **Total Area** | The total area of this Land Cover | [Total Area](/resource-types/common#total-area) |
| **Total Length** | The total length of all polygons in this Land Cover | [Total Length](/resource-types/common#total-area) |
| **ID** | The ID of this Land Cover | UUID |
| **Meta** | The metadata for this Land Cover | [Metadata](/resource-types/common#metadata) |
| **Self** | A link back to this Land Cover | URI |
| **Identifiers** | Any identifiers for this Land Covers | Array of [Identifiers](/resource-types/common#identifier) |
| **Links** | Any Links for this Land Cover | Array of [Links](/resource-types/common#link) |
| **Name** | The name of this Land Cover | String |
| **Resource Type** | The constant value of this resource type<br/>`/core/land-cover` | String |

---

## Eligibility

This represents the eligibility of a given Land Cover.

Land Cover eligibility is defined as:

```json
{
  "primary": "string",
  "scheme": "string",
  "secondary": "string",
  "tertiary": "string",
  "eligible": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Primary** | The primary classification for a Land Cover Eligibility | String |
| **Secondary** | The secondary classification for a Land Cover Eligibility | String |
| **Tertiary** | The tertiary classification for a Land Cover Eligibility | String |
| **Scheme** | The scheme for which this Land Cover Eligibility is for | String |
| **Eligible** | Whether or not this Land Cover is eligible for this | String |

---

## Activity

An activity on a Land Cover is whatever the potential activities are possible to be recorded for a given Land Cover.

An Activity is defined as:

```json
{
  "id": {
    "id": "string",
    "scheme": "string"
  },
  "isPrimary": true,
  "name": "string",
  "productiveArea": {
    "area": 0,
    "units": "string"
  }
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **ID** | The Identifier for this Activity | [Identifier](/resource-types/common#identifier) |
| **Is Primary** | Whether or not this is the primary activity for this Land Cover | Boolean |
| **Name** | The name of this Activity | String |
| **Productive Area** | The productive area of this Activity | [Total Area](/resource-types/common#total-area) |
