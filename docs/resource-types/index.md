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
- [Resource Types](#resource-types)
- [Endpoints/Environments](#endpoints-environments)
- [Errors](#errors)
- [Authentication](#authentication)
- [Frequently Asked Questions](#frequently-asked-questions)
---

# Introduction
*Pure Farming* APIs are designed to deliver standardised and cleansed data relating to all types currently supported resource types. 

Currently supported Resource Types are: Sample analyses, Sample plans, and Load Receivals.  

**Sample Analyses-** This endpoint provides details about samples taken from a crop and the laboratory test results for those samples.  
**Sample Plans-** This endpoint provides information about  a planned sampling activity for a crop  at a geospatial feature (paddock, field, or block) level. Sample plans are typically used to coordinate sampling and analysis activities with other crop tasks.  
**Load receivals-** The Load receivals endpoint provides information about the arrival of harvested crop loads to a location. A crop may be harvested and delivered in a single load or over multiple loads. Load receivals can also record delivery of other product materials to a location (for instance, silage to a pit or fertiliser to a field).

A load receival records the details of the material, transport, source, and destination.  

The Data API is based on the REST standard, where URLs represent collections of data, and actions on the data are performed using HTTP verbs (Such as GET for retrieving data and POST for creating data). Any programming language capable of performing HTTPs requests can be used. Data returned from API uses the JSON standard.  

## Resource Types
- [Common Objects](/resource-types/common.md)  
  Items which are common across all Resource Types.
- [Core](/resource-types/core)
  Core resource types, which are common across most data-requests.
  - [Holdings](/resource-types/core/holdings.md)
    A Holding is a representation of a working Farm, whether it be comprised of multiple areas of land (contiguous or non-contiguous) or not, it is represented as a Holding. An individual Holding may have spatial information, or may not, if present it may be a centroid (point), or spatial feature (feature) or both.
  - [Plots](/resource-types/core/plots.md)
    Plots are a field or a piece of land that is used for planting and reaping crops. 
    Although it is smaller than the holdings but is a quite substantial piece of land. 
- [Crops](/resource-types/crops)  
  Resource types available for Crops.
  - [Crops - Sample Plans](/resource-types/crops/sample-plan.md)  
    Sample Plans provides information about a planned sampling activity for a crop  at a geospatial feature (paddock, field, or block) level.
  - [Crops - Sample Analysis](/resource-types/crops/sample-analysis.md)  
    Sample Analyses provide details about samples taken from a crop and the laboratory test results for those samples. 
  - [Crops - Load Receivals](/resource-types/crops/load-receival.md)  
    Load Receivals provide information about the arrival of harvested crop loads to a location.  
  - [Crops - Work Record](/resource-types/crops/work-record.md)
    Work records provide information about agricultural work and operations performed on a piece of land or crop.
- [Livestock](/resource-types/livestock)
  Resource types available for Livestock.
  - [Animals](/resource-types/livestock/animals.md)  
    Animal provides information about individual animals.
  - [Movements](/resource-types/livestock/movements)
    Provides information about Movements that can be recorded against animals.
    - [Birth Registrations](/resource-types/livestock/movements/birth-registrations.md)
      Provides information about Birth Registrations for individual Animals.
    - [Animal Arrival](/resource-types/livestock/movements/animal-arrival.md)
      Provides information about Animal Arrivals for individual Animals.
    - [Animal Departure](/resource-types/livestock/movements/animal-departure.md)
      Provides information about Animal Departures for individual Animals.
    - [Animal Death](/resource-types/livestock/movements/animal-death.md)
      Provides information about Animal Deaths for individual Animals.
    - [Consignment](/resource-types/livestock/movements/consignment.md)
      Provides information about animal movements that is common accross the other movement resource types

---

## Endpoints / Environments
The *Pure Farming* API is provided as a SaaS offering and the endpoints that you will be interested in are: 

- **Production:** https://api.purefarming.com/data  
- **Demo:** https://api.demo.purefarming.com/data 

---

## Errors
The *Pure Farming* API uses conventional HTTP response codes to indicate the success or failure of an API request.  
In general:
1. Codes in the 2XX range indicate success 
2. Codes in the 4XX range indicate an error that has failed given the information provided (e.g., a required parameter was omitted, a charge failed, etc.) 
3. Codes in the 5XX range indicate an error with *Pure Farming’s* servers.  
Some 4XX errors that could be handled programmatically include an error code that briefly explains the error reported.  

### HTTP Status Code Summary 

| Code | Description |
| ---- | ----------- |
| 200 - OK | Everything worked as expected |
| 400 - Bad Request | The request was unacceptable |
| 404 - Not Found | The requested resource doesn’t exist |
| 500 - Internal Server Error | Something went wrong on *Pure Farming’s* end |
| 504 – Gateway Timeout | The API failed to respond within the timeout period |

---

## Authentication
Before you begin making API calls, you must first authenticate to obtain a valid access token to use in subsequent requests. *Pure Farming* crop API uses OAuth 2.0 for authentication. OAuth 2.0 is the industry-standard protocol for authorization. OAuth 2.0 focuses on client developer simplicity while providing specific authorization flows for web applications, desktop applications, mobile phones, and living room devices.  

### Subsequent Requests 

Once you have an OAuth token, all subsequent API calls that you make on a given user’s behalf must have the token specified in the header of the request. Set the `Authorization` field to `Bearer <Token>`. For example: 

```
Authorization: Bearer 2v8q2bc6uvxtgggfwmwvnvcp4 
```

You should persist the OAuth token in your application, rather than making repeated calls to obtain a token for the same user. Treat the token with the same degree of care that you would a saved password.  

---

## Frequently Asked Questions
### What is an API call? 

An API call is the process of a client application submitting a request to an API and that API retrieving the requested data from the external server or program and delivering it back to the client.  

### What is the difference between an API call and an API response? 

The API call is just the request being sent to *Pure Farming* APIs. The response is the actual data being returned. A single API call can return more than 1 record. By default, the API call will return all items found. You can send additional parameters with your API call to return fewer or more records. 

### What are the common HTTP Methods? 

HTTP Methods are also known as HTTP Verbs. They form a major portion of uniform interface restriction followed by the REST that specifies what action has to be followed to get the requested resource. Below are some examples of HTTP methods: 

GET: This is used for fetching details from the server and is basically a read-only operation
POST: This is used for creation of new resources on the server
PUT: This is used to update the old/existing resource on the server or to replace the resource
DELETE: This method is used to delete the resource on the server.  

### What is a URI? 

URI, short for Uniform Resource Identifier, is a unique sequence of characters that identifies a logical or physical resource used by web technologies.  

### I am having trouble accessing data 

If you are having trouble making API calls, write to us at developer-support@purefarming.com. We will reach out to you and attempt resolve your issue within 24 hours.  

### Is there a way to check the status of the API if there is an outage or downtime? 
 
Absolutely! You can check the status of the APIs here – https://purefarming.statuspage.io/ 
