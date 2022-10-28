---

title: OGC
menu_order: 1
post_status: publish
post_excerpt: OGC - OGC
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: OGC – OGC

- [URLs](#urls)
- [Response Structure](#response-structure)

---

## URLs

Get all the links that show the capabilities of different APIs that you have access to. 

```
GET /ogc
```

## OGC
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
| Title | This shows the OGC API landing page | String
| Description | It provides the description of the OGC API landing page | String
| Links | This provides the links that show the capabilities of different APIs | An array of links

## links

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
| Href | This is the link to the OGC API landing page | URL
| Rel | 
| Type | It is the type of the format used for storing data. For example, json | String
| Hreflang | It is the language used in the response like English | String
| Title | It is the code of the data. | String
| Href | This is the link to the OGC API definition | URL
| Rel | 
| Type | It is the type of the format used for storing data. For example, vnd.oai.openapi+json | String
| Hreflang | It is the language used in the response like English | String
| Title | It is the code of the data. | String