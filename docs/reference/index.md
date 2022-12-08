---
title: Reference Data
menu_order: 1
post_status: publish
post_excerpt: Reference Data - Reference Data Overview
taxonomy:
  category:
    - root
  post_tag:
    - root
---

- [Overview](#overview)
- [Purpose](#purpose)
- [Endpoints available](#endpoints-available)

---

# Overview

Provides lists of reference information with standardised codes and names. Current or planned content includes:

- Animal breeds for livestock species
- Crops classified by type with common and botanical names
- Livestock feeds by category with common and scientific names
- Agricultural compounds and veterinary medicines.

---

## Purpose

You may wish to use the Reference API to:

- Generate a list of standardised names eg. a list of breeds for a livestock species.
- Determine the short code of an item for a particular scheme given the item name.
- Determine the standardised common name given a short code.
- Determine the botanical name for a common name.
- Validate a name or short code.

---

## Endpoints available

The _Pure Farming_ API is provided as a SaaS offering and the endpoints that you will be interested in are:

- [Breed](/reference/breed/breed.md)  
  The Breed Endpoint of the Reference API enables the user to retrieve a list of animal breeds and short codes for one or more species.
- [Treatment](/reference/treatment)
  Animal health treatment, like medication or procedure
  - [Medicine Products](/reference/treatment/medicine-products.md) The Medicine Products Endpoint of the Reference API enables the user to retrieve a list of animal medicine products.

**Note:** Authentication is not required for the Reference API
