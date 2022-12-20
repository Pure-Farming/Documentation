---

title: Group Weight Event
menu_order: 1
post_status: publish
post_excerpt: Livestock - Group Weight Event 
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: Livestock - Group Weight Event 
- [URLs](#urls)
- [Response Structure](#response-structure)

---

## URLs

Get all Group Weight Events that you have access to.
```
GET /data/livestock/weight/group-weight-events
```

Get a single Group Weight Events for the specified **GroupWeightEventId**, the Id is required. 
```
GET /data/livestock/weight/group-weight-events/{GroupWeightEventId}
```

Get all Group Weight Events that are linked to the provided **HoldingId**, holding Id is required. 
```
GET /data/holdings/{holdingId}/livestock/weight/group-weight-events
```

Get a single Group Weight Events with a given **HoldingId** and **GroupWeightEventId**, both Ids are required. 
```
GET /data/holdings/{holdingId}/livestock/weight/group-weight-events/{GroupWeightEventId}
```

---

## Response Structure

A call to the Group Weight Event endpoints returns the following fields:

```json
{
    "self": "string",
    "location": {...},
    "meta": {...},
    "resourceType": "/livestock/weights/group-weight-event",
    "contemporaryGroup": "string",
    "eventDateTime": "2022-12-14T01:52:01.454Z",
    "id": "string",
    "remark": "string",
    "responsible": "string",
    "traitLabel": {...},
    "animalSetReference": {...},
    "countObserved": 10,
    "embeddedAnimalSet": {...},
    "groupMethod": "string",
    "inventoryClassification": {...},
    "animalWeights": [{...}],
    "device": {...},
    "method": "string",
    "resolution": 0.5,
    "statistics": [{...}],
    "timeOffFeed": 12.3,
    "units": "string",  
}
```

| Response Item | Description | Data Type |
|-|-|-|
| **Self** | A link to this specific Group Weight Event. | URI |
| **Location** | An identifier for the location of the Group Weight Event. | [Identifier](/resource-types/common.md#identifier) |
| **Meta** | Meta data for the resource. | [Metadata](/resource-types/livestock/common.md#metadata) |
| **Resource Type** | The fixed discriminator for the Group Weight Event resource type.<br/>Value: /livestock/weights/group-weight-event | String |
| **Contemporary Group** | For manually recorded events, record any contemporary group code that would affect statistical analysis. | String | 
| **Event Date Time** | A particular point in the progression of time. | DateTimeOffset | 
| **Id** | The *Pure Farming* Id of this Group Weight Event. | UUID |
| **Remark** | A comment or remark field for additional user-specified information about the event. | String |  
| **Responsible** | Use if an observation is manually recorded, or an event is carried out or authorised by a person. | String |
| **Trait Label** | Represents a formal trait, identifies the recording system and trait. | [Identifier](/resource-types/common.md#identifier) | 
| **Animal Set Reference** | Reference an existing animal set by ID and optionally URI. | [Animal Set Reference](#animal-set-reference) |
| **Count Observed** | Summarises the number of animals observed in the event. | Integer |
| **Group Method** | Indicates whether the event references an existing animal set, has an embedded animal set, or an inventory classification.</br>(Valid values: ExistingAnimalSet, EmbeddedAnimalSet, InventoryClassification, EmbeddedAnimalSetAndInventoryClassification)| Enumeration | 
| **Embedded Animal Set** | Specifies the set of animals as a list of member animal identifiers. | [Embedded Animal Set](/resource-types/livestock/common.md#embedded-animal-set) |
| **Inventory Classification** | Describe the group of animals by their characteristics rather than animal identifiers. | [Inventory Classification](/resource-types/livestock/common.md#inventory-classification) |
| **Animal Weights** | The Animal-Weight entity records a liveweight for an individual animal in a Group Weight. | Array of [Animal Weight Type](#animal-weight-type) |
| **Device** | Optional information about the device used for the measurement. | [Device](#device) |
| **Method** | The method of observation.</br>(Valid values: LoadCell, Girth, Assessed, WalkOver, Predicted, Imaged, FrontEndCorrelated, GroupAverage) | Enumeration |
| **Resolution** | The smallest measurement difference that can be discriminated given the current device settings. | Number |
| **Statistics** | The statistics that have been calculated. | Array of [Statistics Type](#statistics-type) |
| **Time Off Feed** | Hours of curfew or withholding feed prior to weighing to standardise gut fill. | Number |
| <span id = "unit">**Units**</span> | Units specified in UN/CEFACT 3-letter form.</br>(Valid values: KGM, GRM, LBR, TNE, MC, MGM, ONZ, PN) | Enumeration |

---

### Animal Set Reference 
Reference an existing animal set by ID and optionally URI.

Animal Set Reference object returns the following properties: 
```json
{
    "identifier": {...},
    "context": "string",
    "id": "string",
    "type": "string",
    "href": "string",
    "reltype": "string"
}
```

| Response Item | Description | Data Type |
|-|-|-|
| **Identifier** | Identifies a resource. | [Identifier](/resource-types/common.md#identifier) |
| **Context** | Tells us the type of the referenced Animal Set object  | String |
| **Id** | Uniform resource identifier (URI) of the referenced Animal Set. | URI |
| **Type** | Specifies whether this is a single Animal Set a Link or a Collection. | Enumeration |
| **Href** | Where provided, this is the URI to the referenced resource. | URI |
| **Reltype** | Defines the relationship between the current resource and the referenced resource. | String | 

---

### Animal Weight Type
The Animal-Weight entity records a liveweight for an individual animal in a Group Weight.

Animal Weight Type object returns the following properties: 

```json
[
    {
        "animal": {...},
        "weight": 7.6 
    }
]
```
| Response Item | Description | Data Type |
|-|-|-|
| **Animal** | Animal defined using an identifier and scheme | [Identifier](/resource-types/common.md#identifier) | 
| **Weight** | The weight measurement. | Number |
>The units of all **weight** measurement are specified at the root level. See [Units](#unit) for reference. 

---

### Device
Optional information about the device used for the measurement.

Device object returns the following properties:

```json
{
    "context": "string",
    "id": "string",
    "type": "string",
    "href": "string",
    "identifier": {...},
    "reltype": "string",
    "model": "string",
    "serial": "string"
}
```
| Response Item | Description | Data Type |
|-|-|-|
| **Context** | Tells us the type of the referenced Device object. | String |
| **Id** | Uniform resource identifier (URI) of the referenced Device.| URI | 
| **Type** | Specifies whether this is a single Device a Link or a Collection. | Enumeration | 
| **Href** | Where provided, this is the URI to the referenced resource. | URI |
| **Identifier** | Device defined using an identifier and scheme. | [Identifier](/resource-types/common.md#identifier) |
| **Reltype** | Defines the relationship between the current resource and the referenced resource. | String | 
| **Model** | ICAR registered device model, which represents manufacturer, model, hardware and software versions. | String |
| **Serial** | Optionally, the serial number of the device. | String |

---

### Statistics Type
The statistics that have been calculated.

Statistics object returns the following properties:
```json
[
    {
        "aggregation": "string",
        "metric": {...},
        "unit": "string",
        "value": 55.8
    }
]
```
| Response Item | Description | Data Type |
|-|-|-|
| **Aggregation** | The type of aggregation.</br>(Valid values: Average, Sum, StDev, Min, Max, Count) | Enumeration |
| **Metric** | The metric code for a specific statistic. | [Identifier](/docs/resource-types/common.md#identifier) | 
| **Unit** | Mass units for weight from UN/CEFACT trade facilitation.</br>(Valid values: KGM, GRM, LBR, TNE, MC, MGM, ONZ, PN) | Enumeration|
| **Value** | The value of the metric. | Number |
