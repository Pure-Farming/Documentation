---

title: Common Objects
menu_order: 1
post_status: publish
post_excerpt: Common Data Objects
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Common Objects

- [Classification](#classification)
- [Metadata](#metadata)
- [Feature](#feature)
- [Identifier](#identifier)
- [Link](#link)
- [Total Area](#total-area)
- [Total Length](#total-length)

---

## Classification

Data can be classified in different ways. Primary classification is the highest level, followed by a Secondary sub-category, and a Tertiary sub-category under that.
For example:  
Primary: Rural  
Secondary: Tracks and Pathways  
Tertiary: Four-Wheel Drive Track  

```json
{
  "primary": "string",
  "scheme": "string",
  "secondary": "string",
  "tertiary": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Primary** | The primary level of classification under the scheme. | String |
| **Scheme** | The scheme for this classification. This should be reverse DNS notation. | String |
| **Secondary** | The secondary level of classification under the scheme | String |
| **Tertiary** | The tertiary level of classification under the scheme. | String |

---

## Metadata

This provides metadata about a given object, including information about the creator, provenance and timestamps relating to its creation and modification.

```json
{ 
  "created": "2022-07-06T10:11:21.460Z", 
  "creator": "string", 
  "modified": "2022-07-06T10:11:21.460Z", 
  "sourceId": { … }, 
  "validFrom": "2022-07-06T10:11:21.460Z", 
  "validTo": "2022-07-06T10:11:21.460Z" 
} 
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Created** | The date on which it was created | Date |
| **Creator** | The person responsible for creating the data | String |
| **Modified** | The date on which the data was updated | Date |
| **SourceId** | The identifier of the source that originated the data | Identifier |
| **Valid From** | The timestamp from which this data is valid | Date/Time |
| **Valid To** | The date to which the data is valid (or `null` for always valid) | Date/Time |

---

## Feature

Provides information about a Feature, which can may be another entity in *Pure Farming* such as a Holding, Enterprise etc.

```json
{ 
   "contentType": "string", 
   "identifier": { 
     "id": "string", 
     "scheme": "string" 
   }, 
   "name": "string", 
   "uri": "string" 
} 
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Content Type** | The content type of this Feature | String |
| **Identifier** | The identifier for this Feature | Identifier |
| **Name** | The name of this Feature | String |
| **URI** | The Uniform Resource Identifier for this Feature | String |

---

## Identifier

Represents an identifier, which is a combination of a scheme and an ID value.

```json
{ 
  "id": "string", 
  "scheme": "string" 
} 
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Id** | The value of the Identifier | String |
| **Scheme** | The Scheme for which this identifier belongs to | String |

---

## Link

Represents an individual Link for an object.

```json
{ 
  "contentType": "string", 
  "related": "string", 
  "relationship": "string" 
} 
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Content Type** | The content type of the link | String |
| **Related** | The actual URI of this Link | String |
| **Relationship** | The relationship of this link to its parent | String |

---

## Total Area

It is the total area of the geospatial object. 

```json
{
    "measurement": 0,
    "units": "MTK"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Measurement** | The total area of the spatial feature. | Number |
| **Units** | The unit of measurement. | Enumeration |

---

## Total Length

It is the total Length of all Boundaries.

```json
{
    "measurement": 0,
    "units": "FT"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Measurement** | The total length of all line strings, or total perimeter of all polygons. | Number |
| **Units** | The unit of measurement. | Enumeration |
