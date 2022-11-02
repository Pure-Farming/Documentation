---

title: Animal Arrival
menu_order: 1
post_status: publish
post_excerpt: Animal - Arrival
taxonomy:
    category:
        - api
        - data
    post_tag:
        - api

---

# Resource Type: Animal-Arrival

- [URLs]()
- [Response Structure]()

---

## URLs

Get all Arrivals that you have access to

```
GET /data/livestock/movement/animal-arrivals
```

Get the Arrival for the specified id

```
GET /data/livestock/movement/animal-arrivals/{ArrivalId}
```

Get all Arrivals that are linked to the provided holding id

```
GET /data/holdings/{HoldingId}/livestock/movement/arrivals
```

Get the Arrival for the specified id that is linked to the provided holding id

```
GET /data/holdings/{HoldingId}/livestock/movement/arrivals/{ArrivalId}
```

---

## Response Structure

A call to the Arrivals endpoints returns the following fields.

```json
{
  "self": "string",
  "location": {...},
  "meta": {...},
  "resourceType": "/livestock/movement/animal-arrivals",
  "consignment": {...},
  "responsable": "string",
  "contemporaryGroup": "string",
  "remark": "string",
  "animalId": "string",
  "animalScheme": "string",
  "animalDetail" : {...},
  "arrivalReason": "string",
  "id": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
|**Self** | A link to this specific Arrival | URI
|**Location** | An identifier for the location of the Arrival | Identifier
|**Meta** | Meta data for the resource | Metadata
|**Resource Type** | The fixed discriminator for the animal arrival resource type.<br/>Value: /livestock/movement/arrival  | String
|**Consignment** | The consignment for this movement event | Consignment
|**Responsable** | Whos responsable for this arrival | String
|**ContemporaryGroup** | The Contemporary Group for this arrival | String
|**Remark** | A Remark for this arrival | String
|**Animal Id** | The main identifier for the animal | String
|**Animal Scheme** | The scheme for the main identifier | String
|**Animal Detail** | The details of the animal | Animal Detail
|**Arrival Reason** | The Reason for the arrival (Valid values: Purchase, Internal Transfer, Imported, Stud Service, Stud Service Return, Slaughter, Agistment, Agistment Return, Show, Show Return, Sale, Sale Return, Other) | Enumeration
|**Id** | The Pure Farming Id of this Arrival | UUID |

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
| **Loading DateTime** | The time that the animals were loaded for this consignment | Date/Time |
| **Unloading DateTime** | The time that the animals were unloaded for this consignment | Date/Time |
| **Expected Duration** | The expected transport duration | Number |
| **Transport Operator** | The operator doing this consignment | String |
| **Vehicle** | The vehicle used for this consignment | String |
| **Transport Reference** | The Reference for this consignment | String |
| **Isolation Facility Used** | If an Isolation Facility was used as part of this consignment | Boolean |
| **Farm Assurance Reference Id** | The Farm Assurance Reference Id | String |
| **Farm Assurance Reference Scheme** | The Farm Assurance Reference Scheme | String |

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
| **Country** | The country part of the sdress | String |
| **Locality** | The locality part of the address | String |
| **Region** | The region for the address | String |
| **Post Office Box** | The post office box | String |
| **Post Code** | The post code | String |
| **Street Address** | The street address | String |
| **Address String** | The complete address | String |

---

## Animal Detail

A call to the Animals endpoints returns the following fields.

```json
{
  "self": "string",
  "location": {...},
  "meta": {...},
  "resourceType": "/livestock/animal",
  "alternativeIdentifiers": [{...}],
  "birthDate": "string",
  "breedFractions": {...},
  "coatColor": "string",
  "coatColorIdentifier": {...},
  "gender": "string",
  "healthStatus": "string",
  "identifier": {...},
  "lactationStatus": "string",
  "managementTag": "string",
  "name": "string",
  "officialName": "string",
  "parentage": [{...}],
  "primaryBreed": {...},
  "productionPurpose": "string",
  "reproductionStatus": "string",
  "specie": "string",
  "status": "string",
  "id": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
|**Self** | A link to this specific Animal | URI
|**Location** | An identifier for the location of the Animal | Identifier
|**Meta** | Meta data for the resource | Metadata
|**Resource Type** | The fixed discriminator for the animal resource type.<br/>Value: /livestock/animal  | String
|**Alternative Identifiers** | Any identifier of this Animal | Array of Identifiers
|**Birth Date** | The date of birth of this Animal | Date/Time
|**Breed Fractions** | The breed fractions for this Animal | Breed Fractions
|**Coat Color** | The color of this Animal’s coat | String
|**Coat Color Identifier** | The color of this Animal’s coat using a national or breed-defined scheme and identifier | Identifier
|**Gender** | The gender of this Animal. (Valid values: Female, FemaleNeuter, Male, MaleCryptorchid, MaleNeuter, Unknown) | Enumeration
|**Health Status** | The health status of this Animal. (Valid values: Healthy, Suspicious, Ill, InTreatment, ToBeCulled) | Enumeration
|**Identifier** | The identifier of this Animal | Identifier
|**Lactation Status** | The lactation status of this Animal. (Valid values: Dry, Lead, Fresh, Early, Lactating) | Enumeration
|**Management Tag** | The identifier used by the farmer in day-to-day management of this Animal. | String
|**Name** | Name for given by the farmer for this Animal | String
|**Official Name** | Official herdbook name for this Animal | String
|**Parentage** | The parents, grandparents, ancestors of this Animal | Array Parentage
|**Primary Breed** | ICAR breed code for this Animal. For example:<br/>`{ "scheme": "ICAR2", "id": "AN" }`<br/>For more details, see also Reference Data Breeds - PureFarming DevHub | Identifier |
|**Production Purpose** | Primary production purpose for which this Animal was bred. (Valid values: Meat, Milk, Wool) | Enumeration |
|**Reproduction Status** | The reproduction status of this Animal. (Valid values: Open, Inseminated, Pregnant, NotPregnant, Birthed, DoNotBreed, PregnantMultipleFoetus) | Enumeration |
|**Specie** | The species of this Animal. (Valid values: Buffalo, Cattle, Deer, Elk, Goat, Horse, Pig, Sheep) |Enumeration |
|**Status** | On-farm status of this Animal (Valid values: Alive, Dead, OffFarm, Unknown) | Enumeration |
|**Id** | The Pure Farming Id of this Animal | UUID |

---

### Breed Fractions

Breed Fractions are …

```json
{
  "denominator": 0,
  "fractions": [{...}]
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Denominator** |	The denominator of breed fractions for this Animal. This specifies the number of fractions there are. | Number |
| **Fractions** | The several fractions’ details of the breed for this Animal | Fraction |

---

### Fraction

A Fraction is …

```json
{
  "breed": {...},
  "fractionFraction": 0
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Breed** | Identifies a breed using scheme and id | Identifier |
| **Fraction** | Fraction	The proportion of the denominator that this breed comprises. This could be for example 5. That would mean, by a given denominator of 16 that this animal is a blend of breeds and consists to 5 parts (of 16) of the specified breed. | Number |

---

### Parentage

A description of the parents of this Animal

```json
{
  "gender": "string",
  "identifier": {...},
  "officialName": "string",
  "parentOf": {...},
  "relation": "string"
}
```

| Response Item | Description | Data Type |
| ------------- | ----------- | --------- |
| **Gender** | The gender of this Animal. (Valid values: Female, FemaleNeuter, Male, MaleCryptorchid, MaleNeuter, Unknown) | Enumeration |
| **Identifier** | The identifier of this Animal | Identifier |
| **Official Name** | Official herd-book name for this Animal | String |
| **Parent Of** | The identifier for the child of the Animal | Identifier |
| **Relation** | Identifies the type of parent. (Valid values: Genetic, Recipient, Adoptive) | Enumeration |
