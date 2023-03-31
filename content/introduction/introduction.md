---
uid: BIF_Introduction
---

# Introduction 

PI Interface for Rockwell FactoryTalk Batch [!include[version](../includes/product-version.md)] is an event-based interface that collects data from [Rockwell FactoryTalk Batch System](#what-is-factorytalk) <!-- TU: Link is broken -->. The interface performs the following actions:

* **Collects** batch data from Event Journals (EVT files).
  
* **Converts** the data to PI tags and PI batch properties.

* **Stores** the collected data as event frames and elements within a supported database: PI Batch Database or PI Asset Framework (PI AF) Database.

    You can use tag templates to control PI point creation and event population. All modules, tags, tag aliases, and health tags are automatically created on the PI server. 

PI Interface for Rockwell FactoryTalk Batch processes data using the following rules:

* The flow of data in the interface is unidirectional. The interface reads data from a source you define and then writes it the PI Server. 
* The interface can read data from multiple batch data sources simultaneously. 
* The interface does not edit or delete source data.

**Note:** PI Interface for Rockwell FactoryTalk Batch does not use the PI API Buffering Service, because batch and tag data is already buffered by the source historian databases. To maximize performance, the interface writes events to PI tags in bulk; it writes all events per interface scan.

## What is Rockwell FactoryTalk Batch?

Rockwell FactoryTalk Batch software is used in advanced industrial applications. FactoryTalk systems manage formulas, automate plant floors, and leverage the integration of Enterprise Resource Planning (ERP) systems used in the manufacture of specialty chemicals, pharmaceuticals, and packaged goods, among other industrial uses.
