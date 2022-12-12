---

title: Datasets
menu_order: 1
post_status: publish
post_excerpt: Datasets
taxonomy:
    category:
        - root
    post_tag:
        - root

---

# TODO
This page was copied from [https://github.com/mimiro-io/ICAR/edit/feature-268-streamingapi/generic-data-exchange-api.md](https://github.com/mimiro-io/ICAR/blob/feature-268-streamingapi/generic-data-exchange-api.md)
and needs tidying up

# Datasets Endpoint

The datasets endpoint returns a list of datasets that it is exposing. 

`/datasets` 

The following Schema is used to represent a single dataset in the list:

```json
{
    "description": "Dataset Resource.",
    
    "type": "object",
    
    "required": [
        "name", "url", "changes"
    ],

    "properties": {
        "name": {
            "type": "string",
            "description": "Unique dataset name exposes by this service endpoint."
        },
        "url": {
            "type": "string",
            "description": "Dataset url"
        },
        "changes": {
            "type": "string",
            "description": "Url that exposes the changes for this dataset"
        },
        "containedTypes": {
            "type": "array",
            "description": "An array of strings. Each value is the name of a resource type exposed in this dataset.",
            "items" : {
                "type" : "string"
            }
        }
    }
}
```

An example response from a compliant endpoint could look like the following:

```json
[
    {
        "name" : "animals",
        "url" : "/datasets/animals",
        "changes" : "/datasets/animals/changes",
        "containedTypes" : [ "icarAnimalCoreResource"]
    },
    {
        "name" : "everything",
        "url" : "/datasets/everything",
        "changes" : "/datasets/everything/changes"
    }
]
```

# Dataset Endpoint

The dataset endpoint allows a client to retrieve a single dataset. 

`/datasets/{datasetid}`

The schema of the dataset resource is the same as the dataset resource when returned in the list. An example response is shown below.

```json
{
    "name" : "animals",
    "url" : "/datasets/animal",
    "changes" : "/datasets/animals/changes",
    "containsTypes" : [ "icarAnimalCoreResource"]
}
```
