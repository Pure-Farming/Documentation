---

title: Root URL
menu_order: 1
post_status: publish
post_excerpt: OGC - Root URL
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# OGC - Root URL

- [URLs](#urls)
- [Response Structure](#root-url)

---

## URLs

Get all the links to the API definition, the conformance, and collections resource types. 

```
GET /ogc
```

## Root URL
A call to the OGC endpoint returns the following fields: 

```json
{
  "title": "The OGC API landing page",
  "description": "Access to data via a Web API that conforms to the OGC API Features specification.",
  "links": [...]
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| Title | This is the title of the OGC API landing page that provides links to the API definition, the conformance statements, and the feature collections in the data set. | String |
| Description | It provides the description of the OGC API landing page that provides links to the API definition, the conformance statements, and the feature collections in the data set. | String |
| Links | This provides the links that show the capabilities of different APIs that you may have access to | An array of links |

## Links

It provides all the links that show the capabilities of the different APIs.

```json
{
  "links": [
    {
      "href": "https://api.test.purefarming.com/ogc/",
      "rel": "self",
      "type": "application/json",
      "hreflang": "en",
      "title": "The OGC API landing page"
    },
    {
      "href": "https://api.test.purefarming.com/data/spec/ogc/oas3.json",
      "rel": "service-desc",
      "type": "application/vnd.oai.openapi+json;version=3.0.1",
      "hreflang": "en",
      "title": "The OGC API definition"
    },
    {
      "href": "https://api.test.purefarming.com/ogc/conformance",
      "rel": "conformance",
      "type": "application/json",
      "hreflang": "en",
      "title": "Conformance classes from standards or community specifications, identified by a URI, that the API conforms to"
    },
    {
      "href": "https://api.test.purefarming.com/ogc/collections",
      "rel": "data",
      "type": "application/json",
      "hreflang": "en",
      "title": "Feature collections provided by the API"
    }
  ]
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| Href | This is the location of the Link. | URL |
| Rel | This shows the type of link. For example, this is the link to self. | String | 
| Type | The type of format used for storing data. For example, json. | String |
| Hreflang | The language used in the data, like English. | String |
| Title | The human readable name for the Link. | String |