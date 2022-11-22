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
- [Static Endpoints](#static-endpoints)
- [Errors](#errors)
- [Authentication](#authentication)
- [Frequently Asked Questions](#frequently-asked-questions)

---

## OGC API - Features

Pure Farming provides an API which complies with the OGC Features API, which is a multi-part standard.  
This allows for querying spatial data as well as laying out guidelines and standards for APIs that seek to share feature data in a consistent manner.  


The Pure Farming OGC compliant API allows users to access collections of geographical data representing resource types of holdings, land-covers, and plots.  

The API may be initially used un-authenticated, but in order to retrieve any meaningful data from it, one must first be authenticated. The Pure Farming OGC Features compliant API uses OAuth 2.0 for authentication, see [authentication](/authentication) for more details.

Moreover, if the users are authenticated, they will also get additional sub-collections of data depending on the different holdings, land-covers, and plots that they may have access to.

To learn more about the OGC API - Features standard, you can visit their website at https://ogcapi.ogc.org/features/.

---

## Static Endpoints
- [Collections](/ogc/collections.md)  
  Collections provides list of data on geographical specifications of holdings, plots and land-covers.  
  `/ogc/collections`  
- [Root Page](/ogc/ogc.md)  
  OGC provides links to the API definition, conformance and collections endpoints.  
  `/ogc`
- [Conformance](/ogc/conformance.md)  
  Conformance provides links to the standards that OGC API conforms to.  
  `/ogc/conformance`

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

---

## Authentication

Authentication
Users must obtain authorization in order to perform an API request. Pure Farming uses OAuth2.0 for authentication, which stands for “Open Authorisation.” On behalf of a user, it enables websites or applications to access resources stored on servers run by other web apps.  

OAuth2.0 uses Access Token to provide authentication. An access token is a piece of information that symbolizes the authorization to access resources on behalf of the end-user.

---

## Frequently Asked Questions

### How to make an API call?

To make an API call, firstly, the users need to find their desired API endpoint and send a request via the URI (Uniform Resource Identifier). They need to give a request verb, headers, and, optionally, a request body. Provided a valid request, an API makes a call to some external program for data and gives the data to the initial requesting program.

### What is spatial data?

Data that describes everything with a spatial extent, like size, shape, or position, is known as spatial data. This spatial data is also known as geospatial data when describing information about the things that are positioned relative to the earth. 

### What are the components of HTTP requests?

There are 5 following components of HTTP requests:

1. Verbs showing HTTP methods like GET, PUT, POST, and DELETE for retrieving, creating, updating or replacing, and deleting the resources, respectively. 
2. URI (Uniform Resource Identifier): URI is the identifier for the resource on the server.
3. HTTP version: It demonstrates the version like - HTTP V1.1.
4. Request Header: The Request Header contains metadata for the HTTP request message. Metadata can be a client type, a client-supported format, a message body format, a cache setting, etc.
5. Request Body: It demonstrates message content or resource representation.

### What is Resource in REST?

REST architecture considers each type of content as a resource i.e., text files, HTML pages, images, videos, and dynamic business information. REST server provides the ability to access the resources and modifies them. By using URIs or global IDs, users can identify each resource.

### Do I need authentication for all the API calls that I want to make?

No, the users do not need to get authentication for all the API calls. They can easily make an API call to get the collections of daṭa from the API, but they are required to get authentication if they want to get the items from the API.

### Is there a limit to API calls?

### What are conformance classes? 

Conformance gives a list that declares modules implemented by the API. These modules are named conformance classes. 

### I am having trouble accessing data. Whom shall I contact to?

If you are facing any trouble accessing data or making API calls, write to us at info@mapof.ag. Our team will reach out to you and resolve your issue within 24 hours.

### Where can I get more help?

If you have any other questions, this API documentation doesn't answer, kindly reach out here - info@mapof.ag.

### Is there a way to check the status of the API if there is an outage or downtime?

Absolutely! You can check the status of the APIs here - https://purefarming.statuspage.io/