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
Get all the collections of data which includes location information that you have access to. 

```
GET /ogc/collections
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
| **Links** | This shows the links to the collections of data which includes location information related to holdings, land-covers and plots | An array of links
| **Collections** | This shows the collections of metadata of holdings, land-covers and plots, and collection of items in the respective geographic locations | An array of collections

## Links

It provides all the links for the collections of the data that shows geographical specifications of locations like holdings, land-covers and plots

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
| Href | It shows URL to the links of collections of data of different locations | URL
| Rel | 
| Type | It is the type of the format used for storing data. For example, json | String
| Hreflang | It is the language used in the response like English | String

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
| ID | It shows the type of geographical location. For example, holding | String
| Links | This shows the links to a specific collection of data related to holdings | An array of links
| Href | It shows URL to the links of collection of metadata of holdings | URL
| Rel | 
| Type | It is the type of the format used for storing data. For example, json | String
| Hreflang | It is the language used in the data like English | String
| Title | It is the code of the metadata. For example, holdings | String
| Href | It shows URL to the links of collection of items of holdings | URL
| Rel | 
| Type | It is the type of the format used for storing data. For example, geo+json | String
| Hreflang | It is the language used in the response like English | String
| Title | It is the code of the items. For example, holdings | String
| ID | It shows the type of geographical area. For example, land-covers | String
| Links | This shows the links to a specific collection of data related to land-covers | An array of links
| Href | It shows URL to the links of collection of metadata of land-covers | URL
| Rel | 
| Type | It is the type of the format used for storing data. For example, json | String
| Hreflang | It is the language used in the response like English | String
| Title | It is the code of the metadata. For example, land-covers | String
| Href | It shows URL to the links of collection of items of land-covers | URL
| Rel | 
| Type | It is the type of the format used for storing data. For example, geo+json | String
| Hreflang | It is the language used in the response like English | String
| Title | It is the code of the items. For example, holdings | String
| ID | It shows the type of geographical area. For example, plots | String
| Links | This shows the links to a specific collection of data related to plots | An array of links
| Href | It shows URL to the links of collection of metadata of plots | URL
| Rel | 
| Type | It is the type of the format used for storing data. For example, json | String
| Hreflang | It is the language used in the response like English | String
| Title | It is the code of the metadata. For example, plots | String
| Href | It shows URL to the links of collection of items of plots | URL
| Rel | 
| Type | It is the type of the format used for storing data. For example, geo+json | String
| Hreflang | It is the language used in the response like English | String
| Title | It is the code of the items. For example, plots | String