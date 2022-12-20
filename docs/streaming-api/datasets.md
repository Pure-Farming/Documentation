---

title: Datasets
menu_order: 1
post_status: publish
post_excerpt: Datasets Endpoint
taxonomy:
    category:
        - root
    post_tag:
        - root

---


# Datasets Endpoint

The datasets endpoint returns a list of datasets available for consuming and publishing data.

```
GET /data/streaming/datasets
```


## Response Structure

```json
[
    {
        "name": "holdings",
        "url": "https://api.dev.purefarming.com/data/streaming/datasets/holdings",
        "changes": "https://api.dev.purefarming.com/data/streaming/datasets/holdings/changes",
        "updates": "https://api.dev.purefarming.com/data/streaming/datasets/holdings/updates",
        "containedTypes": [
          "/core/holding"
        ]
    },
    ...
]
```

This response is a list of [dataset response](#dataset-response)s


# Dataset Endpoint

The dataset endpoint returns metadata about a single dataset

```
GET /data/streaming/datasets/{datasetid}
```
where `datasetId` is the name of the dataset


## Dataset Response

```json
{
    "name": "holdings",
    "url": "https://api.dev.purefarming.com/data/streaming/datasets/holdings",
    "changes": "https://api.dev.purefarming.com/data/streaming/datasets/holdings/changes",
    "updates": "https://api.dev.purefarming.com/data/streaming/datasets/holdings/updates",
    "containedTypes": [
      "/core/holding"
    ]
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Name** | The name of the dataset (also called the dataset id) | string | 
| **URL** | A link to the dataset metadata | URI | 
| **Changes** | A link to get the latest changes to the resources within the dataset | URI |
| **Updates** | A link publish updates for a resource | URI |
| **Contained Types** |  An array of resource types contained in this dataset | Array of Strings |
