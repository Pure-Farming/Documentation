---
title: Resource Types
menu_order: 1
post_status: publish
post_excerpt: Resource Types
taxonomy:
  category:
    - root
  post_tag:
    - root
---

- [Introduction](#introduction)
  - [API Reference](#api-reference) 
- [Available Resource Types](#available-resource-types)

---

# Introduction

*Pure Farming* data APIs are designed to deliver data for a range of different agricultural resources, which are standardised to a common schema regardless of the original data sources that provided the data.

The Data API is based on the REST standard, where URLs represent collections of data, and actions on the data are performed using HTTP verbs (Such as GET for retrieving data and POST for creating data). Any programming language capable of performing HTTPs requests can be used. Data returned from API uses the JSON standard. 

## API Reference
You can find the API reference for the Data API at https://developer.purefarming.com/resource-types/api-specification/

## Authentication
Most endpoints for the Data API require you to be authenticated. Find out more in the [Authentication Section](/authentication/index.md)

# Available Resource Types
Currently supported Resource Types are below:

- [Common Objects](/resource-types/common.md)  
  Items which are common across all Resource Types.
- [Core](/resource-types/core)  
  Core resource types, which are common across most data-requests.
  - [Holdings](/resource-types/core/holdings.md)  
    A Holding is a representation of a working Farm, whether it be comprised of multiple areas of land (contiguous or non-contiguous) or not, it is represented as a Holding. An individual Holding may have spatial information, or may not, if present it may be a centroid (point), or spatial feature (feature) or both.
  - [Plots](/resource-types/core/plots.md)  
    Plots are a field or a piece of land that is used for planting and reaping crops.
    Although it is smaller than the holdings but is a quite substantial piece of land.
  - [Land Covers](/resource-types/core/land-covers.md)  
    Land Covers are a representation of hedges, and other biodiversity features for a given spatial feature.
- [Crops](/resource-types/crops)  
  Resource types available for Crops.
  - [Sample Plans](/resource-types/crops/sample-plan.md)  
    Sample Plans provides information about a planned sampling activity for a crop at a geospatial feature (paddock, field, or block) level.
  - [Sample Analysis](/resource-types/crops/sample-analysis.md)  
    Sample Analyses provide details about samples taken from a crop and the laboratory test results for those samples.
  - [Load Receivals](/resource-types/crops/load-receival.md)  
    Load Receivals provide information about the arrival of harvested crop loads to a location.
  - [Work Record](/resource-types/crops/work-record.md)  
    Work records provide information about agricultural work and operations performed on a piece of land or crop.
- [Livestock](/resource-types/livestock)  
  Resource types available for Livestock.
  - [Animals](/resource-types/livestock/animals.md)  
    Animal provides information about individual animals.
  - [Animal Groups](/resource-types/livestock/animal-group.md)
    Defines a group of animals in a medium-long term sense (for instance, a mob or pen or batch or class or line)
  - [Movements](/resource-types/livestock/movements)  
    Provides information about Movements that can be recorded against animals.
    - [Birth Registrations](/resource-types/livestock/movements/birth-registrations.md)  
      Provides information about Birth Registrations for individual Animals.
    - [Animal Arrival](/resource-types/livestock/movements/animal-arrival.md)  
      Provides information about Animal Arrivals for individual Animals.
    - [Animal Departure](/resource-types/livestock/movements/animal-departure.md)  
      Provides information about Animal Departures for individual Animals.
    - [Animal Death](/resource-types/livestock/movements/animal-death.md)  
      Provides information about Animal Deaths for individual Animals.
    - [Consignment](/resource-types/livestock/movements/consignment.md)  
      Provides information about animal movements that is common across the other movement resource types
- [Dairy](/resource-types/dairy)
	Resource types available for Dairy.
	- [Milk Collection](/resource-types/dairy/milk-collection.md) 
