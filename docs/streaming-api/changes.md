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

# TODO
This page was copied from https://github.com/mimiro-io/ICAR/blob/feature-268-streamingapi/generic-data-exchange-api.md and still needs tidying up

# Changes Endpoint

The changes endpoint named in the dataset resource exposes a changes feed of resources. The response from this request is an array of JSON objects. The first object is a context that is reserved for future use. The last object is a continuation object that allows clients to consume subsequent changes. 

`/datasets/{datasetid}/changes?since={sinceToken}`

The changes endpoint returns the following JSON response:

```json
[
  {
     "id" : "@context",
     "description" : "application specific / expansion point for rdf, JSON-LD and Entity Graph Data Model" 
  },

  {
      "resourceType" : "icarAnimalCoreResource",
      "location" : {
          "id" : "a-location-id",
          "scheme" : "io.mimiro.data.locations"
      },
      "meta" : {
          "source" : "io.mimiro.data.cattle",
          "sourceId" : "some-cow-id-1"
      }
  },

  {
      "resourceType" : "icarAnimalCoreResource",
      "location" : {
          "id" : "a-location-id",
          "scheme" : "io.mimiro.data.locations"
      },
      "meta" : {
          "source" : "io.mimiro.data.cattle",
          "sourceId" : "some-cow-id-2",
          "isDeleted" : true
      }
  },

  {
      "id" : "@continuation",
      "token" : "token-issued-by-server-to-get-more-data"
  }
]
```

The first object in the response is for future use and will contain context information. Likely uses are for JSON-LD, or the Entity Graph Data Model.

The main set of objects in the response are ICAR resources. To be valid in the context of this protocol several properties are required:

`location` : Must be specified as this is the main logical grouping of resources when being exchanged.

`meta/sourceId` : The source id of the meta structure must be present and as stated, it must be a unique id related to the source server. e.g. Values of this must be unique across all resources.

`meta/source` : The source of the meta structure must be present.

`resourceType` : The value of this property must be a valid ICAR resource schema, e.g. icarAnimalCoreResource. This is also the requried discriminator property.  

When a client receives the ICAR resources it must process them in order. For each entity it MUST do the following: 

1. check if the `meta/isDeleted` flag is set to `true`. If so the local resource with the corresponding sourceId MUST be deleted or marked as deleted depending on the local system semantics.

2. If there is no local version of the resource it MUST be created and the sourceId must be associated with the local object in some way. 

3. If there is a local object with the correlating sourceId then this representation must be deleted and replaced with the one received. Implementations are free to perform deltas, but the result must be the same. 


The last object in the array is a continuation object and contains a property `token`. The token is an opaque string encoded with base64. This token is issued by the server and clients should NOT manipulate the contents. Manipulating the contents of a continuation token gives undefined behaviour when used as part of a subsequent request. 

A client is responsible for storing the continuation token and then using it as the since token in subsequent calls. e.g.

`/datasets/{datasetid}/changes?since=token-issued-by-server-to-get-more-data`

Note that the continuation token can be used by the server to provide paging. A client typically calls to the changes endpoint until no resources are returned. It then stores the token and then waits for some period before asking again. 

If a server has reloaded all data in a dataset and needs the client to resync from the beginning, then the server can return an HTTP Header:

`icar-full-sync: true`

If this is returned the client should delete all local data related to this dataset, discard any continuation tokens, then make a call to `/changes` and continue as above.

The client should only store the contiuation token if it has succesfully processed all resources returned in a response.
