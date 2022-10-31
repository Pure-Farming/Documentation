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

Pure farming OGC API - Features standard allows users to access all the collection of geographical specifications of holdings, land-covers, and plots, without any authentication. However, if users want to get the collection of items out of the APIs, they must be authenticated to access them. 

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