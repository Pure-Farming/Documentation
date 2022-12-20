---

title: Streaming API
menu_order: 1
post_status: publish
post_excerpt: Streaming API
taxonomy:
    category:
        - root
    post_tag:
        - root

---

- [Introduction](#introduction)
  - [Motivation](#motivation)
  - [Supported Resource Types](#supported-resource%20types)
- [Protocol Definition](#protocol-definition)
  - [Control](#control)
  - [Datasets](#datasets)
  - [Changes](#changes) (GET)
  - [Resources](#resources) (POST)
- [Data Point Keys](#data-point%20keys)
- [Security](#security)

---

# Introduction
*Pure Farming*'s Streaming API defines a protocol for how a client can consume data from a server and update a local database or store; 
or push data to a remote endpoint and modify a collection of resources.

We expose a number of datasets (resource types). Each dataset contains resources of one or more type and exposes a feed of changes. 
Each change is represented as the latest representation of a resource that has been created, modified or deleted. 
Each resource has unique identity across all resources in all datasets. This is known as the data point key.

It is based off the Mimiro Universal Data API standard which you can find here: https://open.mimiro.io/specifications/uda/latest.html#api

The PureFarming Streaming API has two notable differences from the Mimiro standard:
1. The addition of a [control endpoint](/streaming-api/control.md)
2. The `entities` endpoint has been renamed to [resources endpoint](/streaming-api/resources.md)

## Motivation
The main motivation of this API is to enable the synchronisation of *Pure Farming* resources between our system and yours in a generalised manner
and without you needing to be timezone aware.

Because the API is generic and not bound by resource type the Streaming API lets us, on the *Pure Farming* side, add more resource type capability without
publishing new versions of the API.

The API is designed to be super simple and bring a low bar of entry to any software to enable it to participate in a data sharing eco-system. 
There are just 4 endpoints defined in this API yet that is enough to enable the exchange of any *Pure Farming* resource.

## Supported Resource Types
Currently the following resource types are supported:

| Section | Resource Type Name | Short Code                                                                  | Dataset       |
| ------- | ------------------ | --------------------------------------------------------------------------- | --------------|
| Core    | Holdings           | [/core/holdings](/resource-types/core/holdings.md#response-structure)       | `holdings`    |
| Core    | Land Covers        | [/core/land-covers](/resource-types/core/land-covers.md#response-structure) | `land-covers` |
| Core    | Plots              | [/core/plots](/resource-types/core/plots.md#response-structure)             | `plots`       |

# Protocol Definition

Our Streaming API has a single entry point and is consistently structured to allow introspection and dynamic navigation. 
You can find the datasets in the [Supported Resource Types](#supported-resource%20types) section above.
A compliant server exposes the following endpoints:

## Control
The Control endpoint allows you to see which holdings and which resource types you are allowed to publish data for using the Resources endpoint.

```
GET /data/streaming/control
```

See further information in the [Control Endpoint](/streaming-api/control.md) page

## Datasets
The dataset endpoints give you up-to-date information about what datasets (resource types) the API supports.

```
GET /data/streaming/datasets
```

```
GET /data/streaming/datasets/{dataset}
```

See further information in the [Dataset Endpoints](/streaming-api/datasets.md) page

## Changes
Gets the latest version of all resources of a particular dataset. 
You can specify a continuation token which will only return resources that have changed since the last time you called the API.

```
GET /data/streaming/datasets/{dataset}/changes
```

See further information about the endpoint and continuation token in the [Changes Endpoint](/streaming-api/changes.md) page

## Resources
Publishes new data or updates to existing data for a dataset. This allows you to publish large streams of data into the *Pure Farming* platform.

```
POST /data/streaming/datasets/{dataset}/resources
```

See further information in the [Resources Endpoint](/streaming-api/resources.md) page

# Data Point Keys
Sometimes you will need to identify data in a way that is unique to you.
This can help you determine if a piece of data in *Pure Farming* is the same piece of data in your own system.

This is done using a field called a "data point key". It is a string value. 
You could store the ID of the data row, or a hash of the object, or some other string that makes it unique to you.

Data point keys must be unique per *Pure Farming* entity.

## An Example

In your system you have a plot with an ID of `1398e88c-4521-4e82-9974-9ae5ff8fea4d`.

When inserting the plot using the [resources endpoint](/streaming-api/resources.md) you set the dataPointKey to the ID in your system...
```json
{
    "totalArea": {
      "measurement": 20.0,
      "units": "MTK"
    },
	"totalLength": {
	  "measurement": 5.0,
	  "units": "MTK" 
	},
    "identifiers": [
      {
        "id": "1e3af36f-7e3c-4afd-86f5-23a84be0da7f",
        "scheme": "com.purefarming.holdingId"
      },
    ],
    "name": "my plot",
    "resourceType": "/core/plot",
    "dataPointKey": "1398e88c-4521-4e82-9974-9ae5ff8fea4d"
}
```

You could also hash the object, and set the dataPointKey to the hash:
```json
{
    "totalArea": {
      "measurement": 20.0,
      "units": "MTK"
    },
	"totalLength": {
	  "measurement": 5.0,
	  "units": "MTK" 
	},
    "identifiers": [
      {
        "id": "1e3af36f-7e3c-4afd-86f5-23a84be0da7f",
        "scheme": "com.purefarming.holdingId"
      },
    ],
    "name": "my plot",
    "resourceType": "/core/plot",
    "dataPointKey": "7a4a6ed4c958268f2bd5bac5485e9e8a6939a35f4632be908c9aaa4e8b1bb7cf"
}
```

# Security
All communication is done over HTTPs. 

Any endpoint that returns or adds data must be authenticated. See the [Authentication section](/authentication/index.md).

You can see what *Pure Farming* entities you are able to publish data for using the [control endpoint](/streaming-api/control.md)
