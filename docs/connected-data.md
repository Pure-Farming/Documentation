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
- [Endpoints & Environments](#endpoints--environments)
- [Errors](#errors)
- [Authentication](#authentication)
- [Frequently Asked Questions](#frequently-asked-questions)
---

# Introduction
*Pure Farming* APIs are designed to deliver standardised and cleansed data relating to all currently supported resource types. 

You can see a list of all currently supported resource types on our [Resource Types](/resource-types/index.md#available-resource-types) page.

We have three different types of APIs:
- [REST API](/resource-types/index.md)  
  A typical JSON REST API
- [OGC API](/ogc-api/index.md)  
  An OGC compliant API for use with geospatial programs and overlaying data on maps
- [Streaming API](/streaming-api/index.md)  
  An API that allows you to push in large streams of data and pull all changes to a particular dataset
  
---

## Endpoints & Environments
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
Before you begin making API calls, you must first authenticate to obtain a valid access token to use in subsequent requests. *Pure Farming* APIs uses OAuth 2.0 for authentication. OAuth 2.0 is the industry-standard protocol for authentication. OAuth 2.0 focuses on client developer simplicity while providing specific authorization flows for web applications, desktop applications, mobile phones, and living room devices.  

Find out how to authenticate against our APIs in the [Authentication Section](authentication).

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
