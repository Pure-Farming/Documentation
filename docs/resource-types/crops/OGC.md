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