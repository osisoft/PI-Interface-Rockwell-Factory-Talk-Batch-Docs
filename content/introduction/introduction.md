---
uid: BIF_Introduction
---

# Introduction

PI Interface for Rockwell FactoryTalk Batch is a scan-based interface that collects batch data from the Rockwell FactoryTalk system. It reads Event Journals (EVT files) and stores that data as event frames and elements in a PI Batch Database or a PI Asset Framework (PI AF) Database. 

The interface also collects associated batch data in the form of PI Tags and PI Batch properties.

In addition to collecting batch data, the interface populates the PI Point Database. 

PI Point creation, commonly known as tag creation and event population, is controlled by using tag templates. All modules, tags, tag aliases, and health tags are automatically created on the PI server. The Interface does not use the PI API Buffering Service, because batch and tag data is already buffered by the source historian databases. To maximize performance, the interface writes events to PI tags in bulk; that is, it writes all events per interface scan.

The flow of data in the interface is unidirectional: data can only be read from the specified data source and written to the PI Server.  This interface can read data from multiple batch data sources simultaneously.  By design, the interface does not edit or delete source data.

PI Interface for Rockwell FactoryTalk Batch is an event-based interface designed to collect data from the FactoryTalk&reg; software used in advanced industrial applications. These systems manage formulas, automate plant floors, and leverage the integration of Enterprise Resource Planning (ERP) systems used in the manufacture of specialty chemicals, pharmaceuticals, and packaged goods, among other industrial uses.

The interface collects batch events from event journal files created by FactoryTalk, which are based on an OpenBatch technology using the latest Microsoft technologies for integrating industrial operations. For additional information on batch interfaces, see <xref:BIF_HowBatchInterfacesWork>.