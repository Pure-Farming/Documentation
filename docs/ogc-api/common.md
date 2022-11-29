---

title: Common Objects
menu_order: 1
post_status: publish
post_excerpt: OGC - Common Objects
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Common Objects

- [Collections](#collections)
- [Links](#links)

---

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
| Links | Links to the sub-collections and data in this collection | An array of [links](#links) |


## Links

A collection of data may be related to other data collections. A `link` is a link to a related collection or sub-collection. This is defined by [RFC 8288](https://www.rfc-editor.org/rfc/rfc8288.html)

```json
{
  "href": "https://api.purefarming.com/ogc/collections",
  "rel": "self",
  "type": "application/json",
  "hreflang": "en",
  "title": "Collections"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| Href | The URL of for this Link | URL |
| Rel | The type of relationship this link has to the collection. [OGC Features API Standard - Links](https://docs.opengeospatial.org/is/17-069r4/17-069r4.html#_link_relations) defines these | String |
| Type | The type of data provided by the URL. The same as a Content-Type header | String |
| Hreflang | The language of the data in the link. For instance: English (en), Spanish (es), etc | String |
| Title | The human readable name for the link | String |
