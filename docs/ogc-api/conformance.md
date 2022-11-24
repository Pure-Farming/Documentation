---

title: Conformance
menu_order: 1
post_status: publish
post_excerpt: OGC - Conformance
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# OGC: Conformance

- [URLs](#urls)
- [Response Structure](#response-structure)

---

## URLs
Get all the links to the standards that OGC API conforms to.

```
GET /ogc/conformance
```

## Response Structure
A call to the conformance endpoint returns the following fields:

```json
{
  "conformsTo": [...]
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| ConformsTo | This shows the standards that the OGC APIs Conforms to. This includes ogcapi - features related to core, oas30, html, geojson, and gmlsf0 | An array of conformsTo |

## ConformsTo

It provides links to the tests which verify the standards that OGC API conforms to.

```json
{
  "conformsTo": [
    "https://www.opengis.net/spec/ogcapi-features-1/1.0/conf/core",
    "https://www.opengis.net/spec/ogcapi-features-1/1.0/conf/oas30",
    "https://www.opengis.net/spec/ogcapi-features-1/1.0/conf/html",
    "https://www.opengis.net/spec/ogcapi-features-1/1.0/conf/geojson",
    "https://www.opengis.net/spec/ogcapi-features-1/1.0/conf/gmlsf0"
  ]
}
```

| Links | Standards that OGC API conforms to |
| ----- | ---------------------------------- |
| https://www.opengis.net/spec/ogcapi-features-1/1.0/conf/core | This page provides tests that verify that Pure Farming OGC API conforms to conformance class core | 
| https://www.opengis.net/spec/ogcapi-features-1/1.0/conf/oas30 | This page provides tests that verify that Pure Farming OGC API conforms to conformance class oas30 |
| https://www.opengis.net/spec/ogcapi-features-1/1.0/conf/html | This page provides tests that verify that Pure Farming OGC API conforms to conformance class HTML |
| https://www.opengis.net/spec/ogcapi-features-1/1.0/conf/geojson | This page provides tests that verify that Pure Farming OGC API conforms to conformance class GeoJSON |
| https://www.opengis.net/spec/ogcapi-features-1/1.0/conf/gmlsf0 | This page provides tests that verify that Pure Farming OGC API conforms to conformance class GML Simple Features Level 0 | 