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

Get all the collections of geographic data of all holdings.

```
GET /ogc/collections/holdings
```

Get a collection of data on a specific holding. The ID of the holding is required in this case.

```
GET /ogc/collections/holdings/{holdingId}/collections
```

Get all the collections of geographic data on all plots.

```
GET /ogc/collections/plots
```

Get a collection of data on plots for a specific holding. The ID of the holding is required in this case.

```
GET /ogc/collections/holdings/{holdingId}/collections/plots
```

Get all the collections of geographic data on all land-covers.

```
GET /ogc/collections/land-covers
```

Get a collection of data on land-covers for a specific holding. The ID of the holding is required in this case.

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
| **Collections** | Different collections of data available through this API (in PureFarming's case: holdings, land-covers and plots) | An array of [collections](#collections) |

## Collections

Collections provide the links to collections of metadata and items for holdings, land-covers and plots

```json
 {
   "collections": [
    {
      "id": "holdings",
      "links": [
        {
          "href": "https://api.test.purefarming.com/ogc/collections/holdings",
          "rel": "collection",
          "type": "application/json",
          "hreflang": "en",
          "title": "holdings"
        },
        {
          "href": "https://api.test.purefarming.com/ogc/collections/holdings/items",
          "rel": "items",
          "type": "application/geo+json",
          "hreflang": "en",
          "title": "holdings"
        }
      ]
    },
    ...
  ]
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| ID | The ID/name of the collection | String |
| Links | Links to the sub-collections and data in this collection | An array of [links](/ogc-api/common#links) |
