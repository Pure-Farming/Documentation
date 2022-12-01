---

title: OGC API
menu_order: 1
post_status: publish
post_excerpt: OGC API
taxonomy:
    category:
        - root
    post_tag:
        - root

---

- [OGC API - Features](#ogc-api-features)
- [Errors](#errors)
- [Authentication](#authentication)
- [Frequently Asked Questions](#frequently-asked-questions)

---

## Introduction

OGC API allows users to find out the geographical features of a farm. With the help of the OGC API, users can find out the boundary, center point, bounding box, etc. of a holding, plot or land cover. The OGC API has three endpoints namely, Collections, OGC and Conformance. 

**Collections** - The collections endpoint helps you get a list of all feature collections specified in a standard that the server conforms to or metadata describing the collections of data available from *Pure Farming's* OCG API.  

**OGC** - The OGC endpoint provides information on the landing page that has the links to the API definition, the conformance statements and to the feature collection in the data set.   

**Conformance** - This endpoint provides information about the standards that the OGC API conforms to. 
The OGC API is based on the REST standard, where URLs represent data, and actions on the data are performed using HTTP verbs (Such as GET for retrieving data and POST for creating data). Any programming language capable of performing HTTPs requests can be used. Data returned from API uses the JSON standard. 

## OGC API - Features

Pure Farming provides an API which complies with the OGC Features API, which is a multi-part standard.  
This allows for querying spatial data as well as laying out guidelines and standards for APIs that seek to share feature data in a consistent manner.  

The *Pure Farming* OGC compliant API allows users to access collections of geographical data representing resource types of holdings, land-covers, and plots.  

The API may be used un-authenticated but in order to retrieve any meaningful data from it you must be authenticated. The *Pure Farming* OGC Features compliant API uses OAuth 2.0 for authentication, see [authentication](/authentication) for more details.

If you are authenticated, you will also get additional sub-collections of data depending on the different holdings, land-covers, and plots that you have access to.

To learn more about the OGC API - Features standard, you can visit their website at https://ogcapi.ogc.org/features/.

---

## Static Endpoints
- [Root Page](/ogc/ogc.md)  
  OGC provides links to the API definition, conformance and collections endpoints.  

  ```
  GET /ogc
  ```

- [Conformance](/ogc/conformance.md)  
  Conformance provides links to the standards that *Pure Farming's* OCG API conforms to.  

  ```
  GET /ogc/conformance
  ```

- [Collections](/ogc/collections.md)  
  Collections provides a list of geographic data for holdings, plots and land-covers.  
  
  ```
  GET /ogc/collections
  ```

---

## Dynamic Endpoints

The `/ogc/collections` endpoint is dynamic, in that if you are authenticated it will return further collections that relate to individual holdings should you wish to only use those.  

For more information please look at the [collections](/ogc-api/collections.md) documentation for all the relevant endpoints.  

For example, if you are unauthenticated or didn't have access to any holdings, you would be returned this:  
```json
{
  "links": [
    {
      "href":"https://api.purefarming.com/ogc/collections",
      "rel":"self",
      "type":"application/json",
      "hreflang":"en"
    }
  ],
  "collections": [
    {
      "id":"holdings",
      "links": [
        {
          "href":"https://api.purefarming.com/ogc/collections/holdings",
          "rel":"collection",
          "type":"application/json",
          "hreflang":"en",
          "title":"holdings"
        },
        {
          "href":"https://api.purefarming.com/ogc/collections/holdings/items",
          "rel":"items",
          "type":"application/geo+json",
          "hreflang":"en",
          "title":"holdings"
        }
      ]
    },
    ...
  ]
}
```

Whereas if you were authenticated (and had access to one or more holdings), you would see something like the following:  
```json
{
  "links": [
    {
      "href":"https://api.purefarming.com/ogc/collections",
      "rel":"self",
      "type":"application/json",
      "hreflang":"en"
    }
  ],
  "collections": [
    {
      "id":"holdings",
      "links": [
        {
          "href":"https://api.purefarming.com/ogc/collections/holdings",
          "rel":"collection",
          "type":"application/json",
          "hreflang":"en",
          "title":"holdings"
        },
        {
          "href":"https://api.purefarming.com/ogc/collections/holdings/items",
          "rel":"items",
          "type":"application/geo+json",
          "hreflang":"en",
          "title":"holdings"
        }
      ]
    },
    {
			"id": "holdings/a50a28ce-ff23-49e9-8d84-a60869de2096/collections/plots",
			"links": [
				{
					"href": "https://api.purefarming.com/ogc/collections/holdings/items/a50a28ce-ff23-49e9-8d84-a60869de2096",
					"rel": "items",
					"type": "application/geo+json",
					"hreflang": "en",
					"title": "holdings"
				},
				{
					"href": "https://api.purefarming.com/ogc/collections/holdings/a50a28ce-ff23-49e9-8d84-a60869de2096/collections/plots",
					"rel": "collection",
					"type": "application/json",
					"hreflang": "en",
					"title": "plots-for-a50a28ce-ff23-49e9-8d84-a60869de2096"
				},
				{
					"href": "https://api.purefarming.com/ogc/collections/holdings/a50a28ce-ff23-49e9-8d84-a60869de2096/collections/plots/items",
					"rel": "items",
					"type": "application/geo+json",
					"hreflang": "en",
					"title": "plots-for-a50a28ce-ff23-49e9-8d84-a60869de2096"
				}
			]
		},
    ...
  ]
}

```

---

## Errors
The pure farming OGC API uses HTTP response status codes that indicate whether the API requests have succeeded or failed.

There are five classes or groups in which all HTTP response status codes are separated. 

1. 1xx informational response – This range of codes indicates that the request was successfully received and the process is in progress.
2. 2xx successful – This range of codes indicates that the request was successful. 
3. 3xx redirection –  This range of codes indicates that further action is required to complete the request successfully. 
4. 4xx client error – This range of codes indicates that the request contained bad syntax or could not be fulfilled.
5. 5xx server error – This range of codes indicates that the server failed to fulfill an apparently valid request.


### HTTP Status Code Summary

| Code | Description |
| ---- | ----------- |
| 200 - Ok | The request was processed successfully |
| 400 - Bad Request | The request made was not accepted due to an error with the incoming data |
| 404 - Not Found | The resource requested by the user could be found |
| 429 - Quota Exceeded | The user has exceeded the limit of number of requests |
| 500 - Internal Server Error | Something went wrong on *Pure Farming's* server |

---

## Authentication

Users must be authenticated and authorised in order to make some API requests. *Pure Farming* uses OAuth2.0 for authentication.  
OAuth2.0 uses Access Tokens to provide authentication.  
See [authentication](/authentication) for more information
---

## Frequently Asked Questions

### What is spatial data?

Data that describes everything with a spatial extent, like size, shape, or position, is known as spatial data. This spatial data is also known as geospatial data when describing information about the things that are positioned relative to the earth. 

### Do I need to be authenticated to use the API?

No, you do not need to be authenticated to make _some_ API calls. You can easily make an API call to get the collections of daṭa from the API. However you _are_ required to be authenticated if you want to get actual data from the API (not just metadata on the collection).

### Is there a limit to API calls?

Yes, but for a normal use case you shouldn't notice it. If you find you are getting HTTP 429 responses try limiting your calls or contact us to increase the limit.

### What are conformance classes? 

A conformance class is an OGC specification or module that is implemented by our API. We implement many different OGC specifications, and have a list of the specifications that we conform to - our conformance classes. You can find them in the [ConformsTo](/ogc/conformance.md#conformsTo) section of the [conformance](/ogc/conformance.md) page (or through the API endpoint itself!)

### I am having trouble accessing data. Who do I talk to?

If you are facing any trouble accessing data or making API calls, please get in touch with us through our [contact form](https://www.purefarming.com/contact/)

### Where can I get more help?

If you have any other questions please reach out using our [contact form](https://www.purefarming.com/contact/)

### Is there a way to check the status of the API if there is an outage or downtime?

Absolutely! You can check the status of the APIs here - https://Pure Farming.statuspage.io/
