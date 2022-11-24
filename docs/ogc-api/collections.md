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
Get a list of all collections of data on geographical specifications of holdings, plots, and land-covers or metadata describing data on geographical specifications of holdings, plots, and land-covers. 

```
GET /ogc/collections
```

Get all the collections of data on geographical specifications of all the holdings.

```
GET /ogc/collections/holdings
```

Get a collection of data of a specific holding that you may have access to, the holdingID is required in this case.

```
GET /ogc/collections/holdings/{holdingId}/collections
```

Get all the collections of data on geographical specifications of all the plots.

```
GET /ogc/collections/plots
```

Get a collection of data of plots for a specific holding that you may have access to, the holdingID is required in this case.

```
GET /ogc/collections/holdings/{holdingId}/collections/plots
```

Get all the collections of data on geographical specifications of all the land-covers.

```
GET /ogc/collections/land-covers
```

Get a collection of data of land-covers for a specific holding that you may have access to, the holdingID is required in this case.

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
| **Links** | Any links for the set of collections returned. See [links](/ogc-api/common#links) for more information. | An array of links |
| **Collections** | This shows collection items that have a certain set of metadata | An array of collections |

## Collections

It provides the links to collections of metadata and items of holdings, land-covers and plots

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
| ID | It is the ID of the collection | String |
| Links | Links to the individual URLs for this collection. | An array of [links](/ogc-api/common#links) |
