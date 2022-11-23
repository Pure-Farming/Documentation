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

## Introduction

OGC API allows users to find out the geographical features of a farm. With the help of the OGC API, users can find out the boundary, center point, bounding box, etc. of a holding, plot or land cover. The OGC API has three endpoints namely, Collections, OGC and Conformance. 

Collections- The collections endpoint helps you get a list of all feature collections specified in a standard that the server conforms to or metadata describing the collections of data available from the OGC API. 
OGC- The OGC endpoint provides information on the landing page that has the links to the API definition, the conformance statements and to the feature collection in the data set. 
Conformance- This endpoint provides information about the standards that the OGC API conforms to. 
The OGC API is based on the REST standard, where URLs represent data, and actions on the data are performed using HTTP verbs (Such as GET for retrieving data and POST for creating data). Any programming language capable of performing HTTPs requests can be used. Data returned from API uses the JSON standard. 

## OGC API - Features

Pure farming OGC API comply with the OGC Features API, which is a multi-part standard that makes it possible to produce, alter, and query spatial data on the web and that lays out guidelines and standards for APIs that seek to share feature data in a consistent manner. Here spatial data is defined as geographical data, thus also known as geospatial data. In other words, OGC API - Features standard allows users to work with spatial data over the web.
 Pure farming OGC API - Features standard allows users to access all the collection of geographical specifications of holdings, land-covers, and plots, without any authentication. However, if users want to get the collection of items from the APIs, they must be authenticated to access them.
The pure farming API uses OAuth2.0 for authentication. Thus, to get authentication, users are required to be passed by OAuth2.0.
Moreover, if the users are authenticated, they will also get some additional collections of data on the geographical specifications of different holdings, land-covers, and plots that they may have access to. It means that if the users want to get a collection of a specific geographical location like holding, land-cover, or plot that they may have access to, they can also get it provided that they are authenticated with the OGC API OAuth2.0.

To learn more about the OGC API - Features standard, you can visit their website at https://ogcapi.ogc.org/features/.

## Resource Types
- [OGC - Collections](resource-types/OGC/Collections.md)
Collections provides list of data on geographical specifications of holdings, plots and land-covers.
- [OGC - OGC](/resource-types/OGC/OGC.md)
OGC provides links to the API definition, conformance and collections endpoints. 
- [OGC - Conformance](/resource-types/OGC/Conromance.md)
Conformance provides links to the standards that OGC API conforms to. 

---

## Errors
The pure farming OGC API uses HTTP response status codes that indicate whether the API requests have been successful or failed.

There are five classes or groups in which all HTTP response status codes are separated. 

1. 1xx informational response – This range of codes indicates that the request was successfully received and the process is in progress.
2. 2xx successful – This range of codes indicates that the request was successful. 
3. 3xx redirection –  This range of codes indicates that further action is required to complete the request successfully. 
4. 4xx client error – This range of codes indicates that the request contained bad syntax or could not be fulfilled.
5. 5xx server error – This range of codes indicates that the server failed to fulfill an apparently valid request.

### HTTP Status Code Summary

| Code | Description |
| ---- | ----------- |
| 200 - Ok | It indicates the success of the API request. |
| 400 - Bad Request | It indicates that the request made was not accepted due to some client error. |
| 404 - Not Found | It indicated that the resource requested by the user could be found. |
| 429 - Quota Exceeded | The user has exceeded the limit of requests. |
| 500 - Internal Server Error | Something went wrong on Pure Farming’s server. |

## Authentication

Authentication
Users must obtain authorization in order to perform an API request. Pure Farming uses OAuth2.0 for authentication, which stands for “Open Authorisation.” On behalf of a user, it enables websites or applications to access resources stored on servers run by other web apps.  

OAuth2.0 uses Access Token to provide authentication. An access token is a piece of information that symbolizes the authorization to access resources on behalf of the end-user.

## Frequently Asked Questions

### How to make an API call?

To make an API call, firstly, the users need to find their desired API endpoint and send a request via the URI (Uniform Resource Identifier). They need to give a request verb, headers, and, optionally, a request body. Provided a valid request, an API makes a call to some external program for data and gives the data to the initial requesting program.

### What is spatial data?

Data that describes everything with a spatial extent, like size, shape, or position, is known as spatial data. This spatial data is also known as geospatial data when describing information about the things that are positioned relative to the earth. 

### Do I need authentication for all the API calls that I want to make?

No, the users do not need to get authentication for all the API calls. They can easily make an API call to get the collections of daṭa from the API, but they are required to get authentication if they want to get the items from the API.

### Is there a limit to API calls?

### What are conformance classes? 

Conformance gives a list that declares modules implemented by the API. These modules are named conformance classes. 

### I am having trouble accessing data. Whom shall I contact to?

If you are facing any trouble accessing data or making API calls, write to us at info@mapof.ag. 

### Where can I get more help?

If you have any other questions, this API documentation doesn't answer, kindly reach out here - info@mapof.ag.

### Is there a way to check the status of the API if there is an outage or downtime?

Absolutely! You can check the status of the APIs here - https://purefarming.statuspage.io/