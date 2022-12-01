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
Get a list of all collections of geographic data for holdings, plots, and land-covers or metadata describing the geographic data for holdings, plots, and land-covers. 

```
GET /ogc/collections
```

Get all the collections of geographic data for all holdings.

```
GET /ogc/collections/holdings
```

Get a collection of data for a specific holding. The ID of the holding is required.

```
GET /ogc/collections/holdings/{holdingId}/collections
```

Get all the collections of geographic data for all plots.

```
GET /ogc/collections/plots
```

Get a collection of data for all plots on a specific holding. The ID of the holding is required.

```
GET /ogc/collections/holdings/{holdingId}/collections/plots
```

Get all the collections of geographic data for all land-covers.

```
GET /ogc/collections/land-covers
```

Get a collection of data for all land-covers on a specific holding. The ID of the holding is required.

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
| **Links** | This shows the links to the collections of data which includes location information related to holdings, land-covers and plots | An array of [links](/ogc/common.md#links) |
| **Collections** | This shows collection items that have a certain set of metadata | An array of [collections](/org/common.md#collections) |
