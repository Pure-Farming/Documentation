---

title: Load Receival
menu_order: 1
post_status: publish
post_excerpt: Crops - Load Receival
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: Crops – Load Receival

- [URLs](#urls)
- [Response Structure](#response-structure)

---

## URLs

Get all load receivals that you have access to for a given Holding, the HoldingId is required in this case.

```
GET /data/holdings/{HoldingId}/crops/load-receivals
```

Get an individual load receival for a given holding, both the HoldingId and the Id of the load receival are required.

```
GET /data/holdings/{HoldingId}/crops/load-receivals/{Id}
```

---

## Response Structure

A call to the Load receivals endpoint returns the following fields:

```json
{
  "loads": [ … ],
  "operation": "string",
  "priority": 0,
  "status": 0,
  "feature": { … },
  "featureId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "holding": { … },
  "holdingId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "observationDate": "2022-07-08T07:24:20.250Z",
  "phenomenonTime": "string",
  "remark": "string",
  "responsible": "string",
  "id": "string",
  "meta": { … },
  "self": "string",
  "identifiers": [ … ],
  "links": [ … ],
  "name": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Loads** | This provides information about the load receival | Array of load receival data |
| **Operation** | The operation of the load receivals | String |
| **Status** | The status of the load receivals | Enumeration |
| **Feature** | The feature that this load receival is linked to | [Feature](/resource-types/common.md/#feature)  |
| **Feature Id** | The identifier for the Feature that this load receival is linked to | UUID |
| **Holding** | The Holding that this load receival is linked to | [Feature](/resource-types/common.md/#feature)  |
| **Holding Id** | The Identifier for the Holding | UUID |
| **Phenomenon Time** | The time when the load receival was received or recorded | Date/Time |
| **Remark** | Any remarks recorded against this load receival | String |
| **Responsible** | The person responsible for this load receival | String |
| **Id** | It is the ID of the load receival | String |
| **Meta** | Metadata about the load receival | Metadata |
| **Self** | A link to the specific Load receival | URI |
| **Identifiers** | Any identifiers for this Load receival | Array of [Identifiers](/resource-types/common.md/#identifier) |
| **Links** | Any links relevant to this Load receival | Array of Links |
| **Name** | The name of the Load receival | String |

---

### Load

This represents an individual load that has been received.

```json
{
  "analysis": [ … ],
  "crops": [ … ],
  "destination": { … },
  "identifiers": [ … ],
  "internalId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "id": "string",
  "links": [ … ],
  "logisticUnit": "string",
  "meta": { … },
  "name": "string",
  "quantity": 0,
  "rawUnits": "string",
  "rawQuantity": 0,
  "self": "string",
  "source": { … },
  "status": 0,
  "units": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Analysis** | The details of the load receivals. | Array of Analysis |
| **Crops** | The crop that is being received or being recorded that they have gone somewhere. | Array of [Crops](/resource-types/crops/index.md#crop) |
| **Destination** | This is the destination of the load | Destination |
| **Logistic unit** | This shows the unit of the load receival. It can be Bale, Field, Module, Tank, Truck, Unknown | Enumeration |
| **Quantity** | It is the standardised quantity of the load receival | Numeric |
| **Raw quantity** | The raw quantity of the load receival | Numeric |
| **Raw units** | The unit of the load receival | Numeric |
| **Source** | It shows the place from where the load came from | Source |
| **Status** | It shows the status of the load receival. It can be InTransit, Loading, ReadyForTransportation, Received, Refused, Waiting. | Enumeration |
| **Units** | The standardised unit. For instance, tons. | String |
| **ID** | The ID of the load receival | String |
| **Self** | A link to the specific load receival | URI |
| **Identifiers** | These are any identifiers for this load receival | Array of [Identifiers](/resource-types/common.md/#identifier) |
| **Name** | This is the name of the load receival | String |
| **Links** | Any links to other relations for this receival | Array of Links |

---

### Destination

This provides all the details about the destination of the load.

See the definition in [load resource common objects](/resource-types/load-resource.md#destination).

---

### Organisation

This provides all the information about the organisation including the organisation’s name, global location number among others.

```json
{
  "gln": "string",
  "leiCode": "string",
  "name": "string",
  "registration": {
    "id": "string",
    "scheme": "string"
  },
  "uri": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Gln** | The global location number of the organisation | String |
| **Leicode** | This is the legal entity identifier code | String |
| **Name** | The name of the organisation	| String |
| **Registration** | It is any additional property that relates to the registration. It can be `{ “hello”: “world”, “bob”: “smith”, “value”: -1 }` for example | Object |
| **URI** | The uniform resource identifier for this organisation | URI |

---

### Source

This provides all the information about the place where the load came from.

See the definition in [load resource common objects](/resource-types/load-resource.md#source).
