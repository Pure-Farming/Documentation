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
| Title |The title of the OGC API landing page that provides links to the API definition, the conformance statements, and the feature collections in the data set | String |
| Description | The description of the OGC API landing page that provides links to the API definition, the conformance statements, and the feature collections in the data set. | String |
| Links | The links that show the capabilities of different APIs that you may have access to | An array of [links](/ogc/common.md#links) |
