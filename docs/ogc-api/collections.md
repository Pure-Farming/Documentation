---

title: Collections
menu_order: 1
post_status: publish
post_excerpt: OGC - Collections
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: OGC – Collections

- [URLs](#urls)
- [Response Structure](#response-structure)

---

## URLs
Get a list of all collections of geographic data on holdings, plots, and land-covers or metadata describing geographic data on holdings, plots, and land-covers. 

```
GET /ogc/collections
```

Get all the collections of geographic data for all holdings.

```
GET /ogc/collections/holdings
```

Get a collection of data on a specific holding. The ID of the holding is required.

```
GET /ogc/collections/holdings/{holdingId}/collections
```

Get all the collections of geographic data for all plots.

```
GET /ogc/collections/plots
```

Get a collection of data on plots for a specific holding. The ID of the holding is required.

```
GET /ogc/collections/holdings/{holdingId}/collections/plots
```

Get all the collections of geographic data for all land-covers.

```
GET /ogc/collections/land-covers
```

Get a collection of data on land-covers for a specific holding. The ID of the holding is required.

```
GET /ogc/collections/holdings/{holdingId}/collections/land-covers
```

## Collections
A call to the collection endpoint returns the following fields: 

```json
{
  "links": [....]
  "collections": [....]
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Links** | Any links for the set of collections returned. See [links](/ogc-api/common#links) for more information. | An array of [links](/ogc-api/common#links) |
| **Collections** | Different collections of data available through this API (in *Pure Farming's* case: holdings, land-covers and plots) | An array of [collections](/ogc/common.md#collections) |
