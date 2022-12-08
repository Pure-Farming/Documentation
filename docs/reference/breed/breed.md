---
title: Breeds
menu_order: 1
post_status: publish
post_excerpt: Reference Data - Breeds
taxonomy:
  category:
    - root
  post_tag:
    - root
---

# Reference Data: Breeds

- [Livestock Species and Breeds API](#livestock-species-and-breeds-api)
- [Some Potential Uses of the API](#some-potential-uses-of-the-api)
- [Data Returned](#data-returned)
- [Short Code Schemes](#short-code-schemes)
- [isCross Indicator](#iscross-indicator)
- [Data Structure](#data-structure)
- [Endpoints](#endpoints)
- [Query String Parameters](#query-string-parameters)
- [Authentication](#authentication)
- [Guidance for Filtering the Results](#guidance-for-filtering-the-results)

---

# Livestock Species and Breeds API

You can use the Breeds API to generate a list of breeds for a livestock species. The list gives the standardised common name and the short codes used for each breed. Various schemes use their own sets of short codes for breeds. For example, ICAR has a 3-character code scheme. This is discussed further below.

A second endpoint lists the livestock species that are supported by the API. Currently the API supports cattle, sheep, and deer.

## Some Potential Uses of the API

You could use the list of breeds returned by the API to look up the ICAR3 short code for a particular cattle breed such as Aberdeen Angus.

If you know the BCMS short code AA, you could determine the name of the breed.

You could validate a breed name or short code entered by a user into your farm management product.

## Data Returned

A call to the Breeds API returns the following fields for each breed in the species.

| **Response item** | **Description**                                                                             | **Data type** |
| ----------------- | ------------------------------------------------------------------------------------------- | ------------- |
| **name**          | the name of the breed                                                                       | String        |
| **species**       | the name of the species (Cattle, Sheep, Deer)                                               | String        |
| **isCross**       | True if the breed is a Cross (see isCross Indicator below). Currently used for Cattle only. | Boolean       |

and an array of schema and id pairs, each giving the breed’s short code according to a scheme.

| **Response item** | **Description**                                                           | **Data type** |
| ----------------- | ------------------------------------------------------------------------- | ------------- |
| **schema**        | the scheme determining the short code (see Short Code Schemes below)      | String        |
| **id**            | the short code for the breed according to the scheme identified in schema | String        |

For example:

```json
{
  "naem": "Aberdeen Angus",
  "species": "Cattle",
  "isCross": false,
  "identifiers": [
    {
      "schema": "ICAR2",
      "id": "AN"
    },
    {
      "schema": "ICAR3",
      "id": "AAN"
    },
    {
      "schema": "BCMS",
      "id": "AA"
    }
  ]
}
```

This example shows 3 different short codes for the breed Aberdeen Angus for the schemes ICAR3, ICAR2 and BCMS.

```json
{
  "naem": "Holstein Cross",
  "species": "Cattle",
  "isCross": true,
  "identifiers": [
    {
      "schema": "BCMS",
      "id": "HOX"
    }
  ]
}
```

The breed Holstein Cross is identified as a cross. (See the discussion on the isCross indicator below.)

---

## Short Code Schemes

Livestock organisations have their own set or sets of short codes for breeds. The following short code schemes are currently supported by the Breeds API.

| **Schema** | **Description**                                                      |
| ---------- | -------------------------------------------------------------------- |
| ICAR3      | International Committee for Animal Recording (ICAR) 3-character code |
| ICAR2      | International Committee for Animal Recording (ICAR) 2-character code |
| NZ DIGAD3  | NZ Dairy Industry Good Animal Database (DIGAD) 3-character code      |
| NZ DIGAD1  | NZ Dairy Industry Good Animal Database (DIGAD) 1-character code      |
| ABRI       | Agricultural Business Research Institute (ABRI) short code           |
| BCMS       | British Cattle Movement Service (BCMS) short code                    |

---

## isCross Indicator

Some breeds may only be suitable for use in a visual assessment of breed but would not be suitable for use in describing breed distribution.

For example, Jersey is suitable in both visual assessment and breed distribution, but Jersey Cross may only be suitable for visual assessment. It would be totally unsuitable for use in breed distribution. An animal visually identified as Jersey Cross might have a breed of 75% Jersey & 25% Angus but equally could have some other combination with Jersey.

It is up to the API consumer to decide whether they wish to include cross breeds. To assist with identifying which breeds might be best suitable for visual assessment only, cross breed names have an ‘isCross’ indicator.

---

## Data Structure

The conceptual structure for the API can be represented by:

![Conceptual structure for the API](/reference/assets/img/Reference_Breeds_DataStructure.png "Conceptual structure for the API")

| **Resource Name**    | **Description**                                       |
| -------------------- | ----------------------------------------------------- |
| Livestock Species    | The livestock species supported by the API            |
| Livestock Breed      | The breeds for a species + whether a breed is a cross |
| Livestock Scheme     | The schema or short code schemes                      |
| Livestock Identifier | The short code for a breed in the specified scheme    |

---

## Endpoints

Calling the Species endpoint returns a list of the livestock species supported.

```
GET /reference/species
```

Calling the Breeds endpoint returns the full list of breeds for the nominated species.

```
GET /reference/breeds?species={species}
```

---

## Query String Parameters

| **Query string parameter** | **Required/Optional** | **Description**                                                                               | **Type** |
| -------------------------- | --------------------- | --------------------------------------------------------------------------------------------- | -------- |
| **Species**                | Required              | The name of the species you want to look up. Currently cattle, sheep, and deer are supported. | string   |

---

## Authentication

Authentication is not required.

---

## Guidance for Filtering the Results

You may want to filter the list of breeds once you have returned the list of breeds for a species.

If you do not want crosses, filter on **isCross** = False.

If you want details for a specific breed name, filter on **name**.

You could refine the list by **schema** if you only want breeds used by a specific organisation. For example, if you only need breeds used by ICAR (International Committee for Animal Recording) you can ignore breeds that do not have ICAR values in the array.

If you want a breed with a specific short code, you will search for the **schema** and **id** pair.
For example, schema = ICAR3 and id = BRM would find the Brahman.
