---

title: Changes Endpoint
menu_order: 1
post_status: publish
post_excerpt: Changes Endpoint
taxonomy:
    category:
        - root
    post_tag:
        - root

---

# Changes Endpoint

The changes endpoint for a dataset returns the latest version of any item that has changed.  
The response from this request is an array of JSON objects. The first object is a context that is reserved for future use. The last object is a continuation object that allows clients to consume subsequent changes. 

```
/datasets/{datasetid}/changes?since={sinceToken}
```

The changes endpoint returns the following JSON response:

```json
[
  {
     "id" : "@context",
     "description" : "application specific / expansion point for rdf, JSON-LD and Entity Graph Data Model" 
  },
  {
      "resourceType" : "/core/plot",
      "name": "Holding1",
      "id": "4dd345e8-c91b-4bf2-a102-a9f86b01c46b"
  },
  {
      "resourceType" : "/core/holding",
      "name": "Holding2",
      "id": "ef5beba4-ed61-43af-b258-026a45062b95"
  },
  {
      "id" : "@continuation",
      "token" : "token-issued-by-server-to-get-more-data"
  }
]
```

The response has three parts to it:
- The @context
- The items
- The @continuation token

## The @context
The first object in the response is for future use and will contain context information. Likely uses are for JSON-LD, or the Entity Graph Data Model.

## The items
The main set of objects in the response are _Pure Farming_ resources. There can be 0 or more resources. 

For example, the following response is valid:

GET /data/streaming/datasets/plots/changes?since=aabbcc
```json
[
  {
     "id" : "@context",
     "description" : "application specific / expansion point for rdf, JSON-LD and Entity Graph Data Model" 
  },
  {
      "id" : "@continuation",
      "token" : "xxyyzz"
  }
]
```

The above response indicates there were no changes to any plots since the last time the API was called (indicated by the `?since=aabbcc`).

When a client receives the _Pure Farming_ resources it must process them in order. For each entity it must do the following: 

1. Check if the `meta/isDeleted` flag is set to `true`
   If so, the local resource with the corresponding id must be deleted or marked as deleted.

2. If there is no local version of the resource it must be created and the id must be associated with the local object in some way

3. If there is a local object with the correlating id then this representation must be deleted and replaced with the one received
   Implementations are free to perform deltas, but the result must be the same


## The @continuation token
The last object in the array is a continuation token and contains a property `token`. The token is an object encoded with base64. This token is issued by the server and clients must not manipulate the contents. Manipulating the contents of a continuation token gives undefined behaviour when used as part of a subsequent request. 

A client is responsible for storing the continuation token and then using it as the since token in subsequent calls. e.g.

```
GET /data/streaming/datasets/{datasetid}/changes?since=token-issued-by-server-to-get-more-data
```

Note that the continuation token can be used by the server to provide paging. A client typically calls to the changes endpoint until no resources are returned. It then stores the token and then waits for some period before asking again. 

The client should only store the contiuation token if it has succesfully processed all resources returned in a response.
