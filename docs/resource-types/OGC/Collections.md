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
| **Links** | This shows the links to the collections of data which includes location information related to holdings, land-covers and plots | An array of links |
| **Collections** | This shows collection items that have a certain set of metadata | An array of collections |

## Links

It provides all the links for the collections of the data that show geographical specifications of locations like holdings, land-covers, and plots.

```json
{
  "links": [
    {
      "href": "https://api.test.purefarming.com/ogc/collections",
      "rel": "self",
      "type": "application/json",
      "hreflang": "en"
    }
  ],
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| Href |  | URL |
| Rel | It shows what type of link it is. For instance, it can be a link to self | String |
| Type | It is the type of the response in the link. For example, JSON | String |
| Hreflang | It shows the language of the data in the link. For instance, English, Spanish, etc. | String |

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
    {
      "id": "land-covers",
      "links": [
        {
          "href": "https://api.test.purefarming.com/ogc/collections/land-covers",
          "rel": "collection",
          "type": "application/json",
          "hreflang": "en",
          "title": "land-covers"
        },
{
          "href": "https://api.test.purefarming.com/ogc/collections/land-covers/items",
          "rel": "items",
          "type": "application/geo+json",
          "hreflang": "en",
          "title": "land-covers"
        }
      ]
    },
    {
      "id": "plots",
      "links": [
        {
          "href": "https://api.test.purefarming.com/ogc/collections/plots",
          "rel": "collection",
          "type": "application/json",
          "hreflang": "en",
          "title": "plots"
        },
        {
          "href": "https://api.test.purefarming.com/ogc/collections/plots/items",
          "rel": "items",
          "type": "application/geo+json",
          "hreflang": "en",
          "title": "plots"
        }
      ]
    }
  ]
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| ID | It is the ID of the holding | UUID |
| Links | This shows the links to a specific collection of data related to holdings | An array of links |
| Href |  | URL |
| Rel | It shows what type of link it is. For instance, it can be a link to self | String |
| Type | It is the type of the response in the link. For example, JSON | String |
| Hreflang | It shows the language of the data in the link. For instance, English, Spanish, etc. | String |
| Title | It is the title of the metadata | String |
| Href |  | URL |
| Rel | It shows what type of link it is. For instance, it can be a link to self | String | 
| Type | It is the type of the response in the link. For example, JSON | String |
| Hreflang | It shows the language of the data in the link. For instance, English, Spanish, etc. | String |
| Title | It is the title of the metadata  | String |
| ID | It is the ID of the land cover | UUID |
| Links | This shows the links to a specific collection of data related to land-covers | An array of links |
| Href |  | URL |
| Rel | It shows what type of link it is. For instance, it can be a link to self | String |
| Type | It is the type of the response in the link. For example, JSON | String |
| Hreflang | It shows the language of the data in the link. For instance, English, Spanish, etc. | String |
| Title | It is the title of the metadata | String |
| Href | It shows the URL of the links to the collection of items of land-covers | URL |
| Rel | It shows what type of link it is. For instance, it can be a link to self | String |
| Type | It is the type of the response in the link. For example, JSON | String |
| Hreflang | It shows the language of the data in the link. For instance, English, Spanish, etc. | String |
| Title | It is the title of the metadata | String |
| ID | It is the ID of the plot | UUID |
| Links | This shows the links to a specific collection of data related to plots | An array of links |
| Href | It shows the URL to the links of collection of metadata of plots | URL |
| Rel |  | String |
| Type | It is the type of the response in the link. For example, JSON | String |
| Hreflang | It shows the language of the data in the link. For instance, English, Spanish, etc. | String |
| Title | It is the title of the metadata | String |
| Href |  | URL |
| Rel | It shows what type of link it is. For instance, it can be a link to self | String |
| Type | It is the type of the response in the link. For example, JSON | String |
| Hreflang | It shows the language of the data in the link. For instance, English, Spanish, etc. | String |
| Title | It is the title of the metadata | String |