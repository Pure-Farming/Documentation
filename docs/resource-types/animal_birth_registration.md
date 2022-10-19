# Resource Type: Livestock - Movement - Animal Birth Registration 

 - [URLs](#URLs)
 - [Response Structure](#response-structure)


## URLs

Get all animal birth registrations that you have access to.

    Get /data/livestock/movement/animal-birth-registrations
    
Get an individual animal birth registration for a given **AnimalBirthRegId**, the Id of the animal birth registration is required.

    Get /data/livestock/movement/animal-birth-registrations/{AnimalBirthRegId}

Get all animal birth registrations for a given holding, the **HoldingId** is required.

    Get /data/holdings/{HoldingId}/livestock/movement/animal-birth-registrations

Get an individual animal birth registration with a given **HoldingId** and **AnimalBirthRegId**, both Ids are required.

    Get /data/holdings/{HoldingId}/livestock/movement/animal-birth-registrations/{AnimalBirthRegId}

## Response Structure

A call to the Livestock Animal Birth Registration endpoint returns the following fields:
```json
{
	"self": "string",
	"id": "string",
	"meta": { ... },
    "resourceType": "/livestock/movement/animal-birth-registration",
    "eventDateTime": "string",
    "traitLabel": { ... },
    "responsible": "string",
    "remark": "string",
    "contemporaryGroup": "string",
    "registrationReason": "string",
    "location": { ... },
    "animal": { ... },
    "animalDetail": { ... }
}
```

|Response Item   |Description                    |Data Type                    |
|----------------|-------------------------------|-----------------------------|
|**Self**        |A link to the specific Animal Birth Registration.         |URL             |
|**Id**          |The Pure Farming Id of this Animal Birth Registration.    |UUID            |
|**Meta**        |Meta data for the resource.                               |Metadata        |
|**Resource Type**|The fixed discriminator for the Animal Birth Registration resource type. <br/>Value: ***/livestock/movement/animal-birth-registration***    |String|
|**Event DateTime** |The datetime when the event happened. Shall be UTC format with Z, specified in RFC3339 (see https://ijmacd.github.io/rfc3339-iso8601/ for format guidance).|Date/Time|
|**Trait Label**|If the event represents a formal trait, this identifies the recording system and trait. |Identifier|
|**Responsible**|Use if an observation is manually recorded, or an event is carried out or authorised by a person. SHOULD be a person object.    |String |
|**Remark**|A comment or remark field for additional user-specified information about the event.|String |
|**Contemporary Group**|For manually recorded events, record any contemporary group code that would affect statistical analysis. |String |
|**Registration Reason**|Enumeration for registration reason: **Born**, or **Registered** (induct existing animal).|Enumeration|
|**Location**|An identifier for the location of the Animal Birth Registration. |Identifier|
|**Remark**|A comment or remark field for additional user-specified information about the event.|String |
|**Animal**|Unique animal scheme and identifier combination.|Identifier|
|**Animal Detail**|Core schema for representing animal. [See the Animal definition](/animal). |AnimalDetail|
