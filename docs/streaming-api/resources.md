---

title: Resources Endpoint
menu_order: 1
post_status: publish
post_excerpt: Resources Endpoint
taxonomy:
    category:
        - root
    post_tag:
        - root

---

# TODO
This was copied from https://github.com/mimiro-io/ICAR/blob/feature-268-streamingapi/generic-data-exchange-api.md and still needs tidying up


# Dataset Push 

The datasets concept can also be used in a push based scenario. In this model a client POSTs resources to the dataset's `resources` endpoint. 

POST `/dataset/{datasetid}/resources`

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
  }
]
```

The semantics for PUSH are the same as for the pull semantics described above with the following exceptions:

1. Full sync is not accepted as header in the push scenario. 
2. The payload for push MUST include only a context followed by resources. i.e no continuation token json object.

The server returns a 200 OK if the new resource representations are correctly processed. 

Any other response code and the client MUST assume that the server has not received and stored the latest state. 

Use cases for push is typically small on site devices that are pushing data up to a cloud location which then collects resources from many clients before sharing them further or processing them. It is best practice to have different dataset endpoints for Push and Pull. 
