---

title: Connected Data
menu_order: 1
post_status: publish
post_excerpt: Connected Data
taxonomy:
    category:
        - root
    post_tag:
        - root

---

- [Introduction](#introduction)
- [OGC API - Features](#ogc-api-features)
- [Resource Types](#resource-types)
- [Endpoints/Environments](#endpoints-environments)
- [Errors](#errors)
- [Authentication](#authentication)
- [Frequently Asked Questions](#frequently-asked-questions)
---

## OGC API - Features

Pure farming OGC API confirms OGC API - Features, a multi-part standard that makes it possible to produce, alter, and query spatial data on the web and that lays out guidelines and standards for APIs that seek to share feature data in a consistent manner. Here spatial data is defined as geographical data. In other words, OGC API - Features standard allows users to work with spatial data over the web.

Pure farming OGC API - Features standard allows users to access all the collection of data on geographical specifications of holdings, land-covers, and plots, without any authentication. However, if users want to get the collection of items out of the APIs, they must be authenticated to access them. 

The pure farming API uses OAuth2.0 for authentication. Thus, to get authentication, users are required to be passed by OAuth2.0.

Moreover, if the users are authenticated, they will also get some additional collections of geographical specifications of different holdings, land-covers, and plots that they may have access to. To explicate, if the users want to get a collection of a specific geographical location like holding, land-cover, or plot that they may have access to, they can also get it provided that they are authenticated with the OGC API OAuth2.0.

To learn more about the OGC API - Features standard, see the OGC API - Features website at ogcapi.ogc.org/features.

## Errors
The pure farming OGC API uses HTTP response status codes that indicate whether the API requests have been successful or failed.

There are five classes or groups in which all HTTP response status codes are separated. 

1. 1xx informational response – This range of codes indicates that the request was successfully received and the process is in progress.
2. 2xx successful – This range of codes indicates that the request was successful. 
3. 3xx redirection –  This range of codes indicates that further action is required to complete the request successfully. 
4. 4xx client error – This range of codes indicates that the request contains bad syntax or cannot be fulfilled.
5. 5xx server error – This range of codes indicates that the server failed to fulfill an apparently valid request.

### HTTP Status Code Summary

| Code | Description |
| ---- | ----------- |
| 200 - Ok | It indicates the success of the API request. |
| 400 - Bad Request | It indicates that the request made was not accepted due to some client error. |
| 404 - Not Found | The resource that the user requested cannot be found. |
| 429 - Quota Exceeded | The user has exceeded the limit of requests. |
| 500 - Internal Server Error | Something went wrong on Pure Farming’s server. |

## Frequently Asked Questions

### How to make an API call?

Making an API call is easy. First, the users need to find their desired API endpoint and send a request via the URI (Uniform Resource Identifier). They need to give a request verb, headers, and, optionally, a request body. Provided a valid request, an API makes a call to some external program for data and gives the data to the initial requesting program.

### What is spatial data?

Data that describes everything with a spatial extent, like size, shape, or position, is known as spatial data. This spatial data is also known as geospatial data when describing information about the things that are positioned relative to the earth. 

### What are the HTTP verbs?

There are 4 fundamental request patterns that are most applicable to all the endpoints in the APIs. These request patterns are based on the HTTP verbs. The 4 most commonly used HTTP verbs are:

1. GET: This verb is used for retrieving information, and users are only allowed to read the information and cannot change it. 
2. POST: This request pattern is used to create a new resource.
3. PUT: This verb is used to update or replace the already existing data. 
4. DELETE: Already clear from its name, this verb is used to delete the data or information present.

There are many other HTTP verbs also available, but they are used less frequently. 

### Do I need authentication for all the calls that I want to make?

No, the users do not need to get authentication for all the calls. They can easily make a call to get the collections of daṭa from the API, but they are required to get authentication if they want to get the items from the API.

### Is there a limit to API calls?



### I am having trouble accessing data. Whom shall I contact to?

If you are facing any trouble accessing data or making API calls, write to us at info@mapof.ag. Our team will reach out to you and resolve your issue within 24 hours.

### Where can I get more help?

If you have any other questions, this API documentation doesn't answer, kindly reach out to us at info@mapof.ag.