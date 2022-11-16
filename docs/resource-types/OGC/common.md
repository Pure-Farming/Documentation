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

- [Link](#link)

---

## Link

A collection of data may be related to other data collections. A `link` is a link to a related collection or sub-collection. This is defined by RFC 8288

```json
{
  "href": "https://api.test.purefarming.com/ogc/collections",
  "rel": "self",
  "type": "application/json",
  "hreflang": "en"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| Href | The URL of the collection or resource | URL |
| Rel | The type of relationship this link has to the collection. [RFC8288](https://docs.ogc.org/is/18-062r2/18-062r2.html#toc16) defines some of these, but PureFarming has additional ones such as `items` for items within a collection | String |
| Type | The type of data provided by the URL. The same as a Content-Type header | String |
| Hreflang | The language of the data in the link. For instance, English, Spanish, etc. | String |
