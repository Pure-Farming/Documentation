---

title: Consignment
menu_order: 1
post_status: publish
post_excerpt: Consignment
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: Consignment

- [Consignment](#consignment)

---

### Consignment

Consignment are information about the transport of the animal in this event

```json
{
  "id": "string",
  "scheme": "string",
  "origin": {...},
  "destination": {...},
  "loadingDateTime": "DateTime",
  "unloadingDateTime": "DateTime",
  "expectedDuration": "double",
  "transportOperator": "string",
  "vehicle": "string",
  "transportReference": "string",
  "isolationFacilityUsed": "boolean",
  "farmAssuranceReferenceId": "string",
  "farmAssuranceReferenceScheme": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Id** |	The Id of this consignment | String |
| **Scheme** |	The Scheme of this consignment | String |
| **Origin** |	The Origin of this consignment | Location |
| **Destination** | The Destination of this consignment | Location |
| **Loading DateTime** | A particular point in the progression of time. Shall be UTC format with Z, specified in RFC3339. | DateTimeOffset  |
| **Unloading DateTime** | A particular point in the progression of time. Shall be UTC format with Z, specified in RFC3339. | DateTimeOffset  |
| **Expected Duration** | Expected duration of transportation in hours. | Number |
| **Transport Operator** | Transport operator official name (should really be schema.org/organization).| String |
| **Vehicle** | Identification of the vehicle (for example, licence plate). | String |
| **Transport Reference** | Shipping or transporter reference.| String |
| **Isolation Facility Used** | True if an isolation facility was used for the movement. | Boolean |
| **Farm Assurance Reference Id** | A unique identification for the resource issued under the auspices of the scheme. | String |
| **Farm Assurance Reference Scheme** | The identifier (in reverse domain format) of an official scheme that manages unique identifiers. | String |

---

### Location

A Location is an Origin or Destination for a consignment

```json
{
  "id": "string",
  "scheme": "string",
  "address": {...}
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Id** | The Id of the location | String |
| **Scheme** | The Scheme of the location | Number |
| **Address** | The postal address of this location | Address |

---

### Address

A address for a location

```json
{
  "country": "string",
  "locality": "string",
  "region": "string",
  "postOfficeBox": "string",
  "postCode": "string",
  "streetAddress": "string",
  "addressString": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Country** | The country. For example, USA. You can also provide the two-letter ISO 3166-1 alpha-2 country code. | String |
| **Locality** | The locality in which the street address is, and which is in the region. For example, Mountain View. | String |
| **Region** | The region in which the locality is, and which is in the country. For example, California or another appropriate first-level Administrative division | String |
| **Post Office Box** | The post office box number for PO box addresses. | String |
| **Post Code** | The postal code. For example, 94043. | String |
| **Street Address** | The street address. For example, 1600 Amphitheatre Pkwy. | String |
| **Address String** | The complete address | String |