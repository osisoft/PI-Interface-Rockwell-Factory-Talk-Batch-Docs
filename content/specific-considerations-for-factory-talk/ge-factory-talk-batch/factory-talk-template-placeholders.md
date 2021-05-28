---
UID: Emersontemplateplaceholders
---


# Emerson template placeholders

The following sections list placeholders provided by the interface for defining template settings.

## DeltaV Batch Historian

| Placeholder | Relationship to Source Column | Source Column | View or Union of tables1 |
| ----------- | ----------------------------- | ------------- | ------------------------ |
| [AREA] | equivalent to | area | batcheventview |
| [BATCHID] | equivalent to | batchID | batcheventview |
| [COMMENT] | Paragraph | userComment | Union of tables |
| [DESCRIPT] | equivalent to | eventdescr | batcheventview |
| [EU] | Paragraph | engUnit | Union of tables |
| [EVENT] or [PARAMETER] | equivalent to | eventType | batcheventview |
| [OPERATION] | determined from equivalent to | action | batcheventview |
| [PHASE] | determined from equivalent to | action | batcheventview |
| [PHASEMODULE] | equivalent to | phasemodule | batcheventview |
| [PROCEDURE] | determined from equivalent to | action | batcheventview |
| [PROCESSCELL] | equivalent to | processcell | batcheventview |
| [PVAL] or [VALUE] |  | Paragraph | Union of tables2 | 
| [UNIQUEID] | equivalent to | uniqueid | batcheventview |
| [UNIT] | equivalent to | unit | batcheventview |
| [UNITPROCEDURE] | determined from equivalent to | action | batcheventview |
| [USERID] or [USER] | equivalent to | userName | batcheventview |

1 Named view or union of tables as described in the topic: Emerson start and stop events
2 Value appropriate to each table in the union of tables, for example: the value column of the BReportEvent table.

For the **VALUE** setting and for **NAME** in property templates, the additional placeholders [TAG] and [TIME] are supported.

## DeltaV Event Chronicle (Alarms & Events Historian) Placeholders

* [AREA]
* [ATTRIBUTE]
* [CATEGORY]
* [DESC1]
* [DESC2]
* [EVENT]
* [LEVEL]
* [MODULE]
* [MODULEDESC]
* [NODE]
* [STATE]
* [TIME]
* [UNIT] (If [MODULEDESC] is “Unit Module”, the [UNIT] placeholder contains the module name. Otherwise it contains the unit name.)

## Syncade Placeholders

The data source provides XML formatted messages that the interface reads. The placeholders describing the recipe hierarchy depend on the style of recipe. The following examples use terminology like: OrderInstanceSummary/@Name where @Name is the name attribute on the OrderInstanceSummary XML element.

In this release the supported batch hierarchical levels are:

![Supportedbatchhierarchallevels](../images/Supportedbatchhierarchallevels.png)

The following tables illustrate Placeholders for "Master Recipe", "Process Segment", "Procedure", and "Unit Procedure" recipe styles:

| Placeholder | Master Recipe-style recipe |
| ----------- | -------------------------- |
| [MASTERRECIPE] | OrderInstanceSummary/@Name |
| [PROCESSSEGMENT] | OrderInstanceSummary/ItemInstanceSummary/@Name |
| [PROCEDURE] | OrderInstanceSummary/ItemInstanceSummary/ItemInstanceSummary/@Name |
| [UNITPROCEDURE] | OrderInstanceSummary/ItemInstanceSummary/ItemInstanceSummary/ItemInstanceSummary/@Name |
| [OPERATION] | OrderInstanceSummary/ItemInstanceSummary/ItemInstanceSummary/ItemInstanceSummary/ItemInstanceSummary/@Name |
|  |  In this example, the name of the fifth level down in the recipe

| Placeholder | Process Segment-style recipe | 
| ----------- | ---------------------------- |
| [PROCESSSEGMENT] | OrderInstanceSummary/@Name |
| [PROCEDURE] | OrderInstanceSummary/ItemInstanceSummary/@Name |
| [UNITPROCEDURE] | OrderInstanceSummary/ItemInstanceSummary/ItemInstanceSummary/@Name |
| [OPERATION] | OrderInstanceSummary/ItemInstanceSummary/ItemInstanceSummary/ItemInstanceSummary/@Name |
|   | In this example, the name of the fourth level down in the recipe |

| Placeholder | Procedure-style recipe |
| ----------- | ---------------------- |
| [PROCEDURE] | OrderInstanceSummary/@Name |
| [UNITPROCEDURE] | OrderInstanceSummary/ItemInstanceSummary/@Name |
| [OPERATION] | OrderInstanceSummary/ItemInstanceSummary/ItemInstanceSummary/@Name |
|  | In this example, the name of the third level down in the recipe |

| Placeholder | Unit Procedure-style recipe |
| ----------- | --------------------------- |
| [UNITPROCEDURE] | OrderInstanceSummary/@Name |
| [OPERATION] | OrderInstanceSummary/ItemInstanceSummary/@Name |
|   | In this example, the name of the second level down in the recipe |

Placeholders that vary depending on whether the event occurs at the start or end of a step in the recipe:

| Placeholder | Event at start of step | Event at end of step |
| ----------- | ---------------------- | -------------------- |
| [TIME] | InstructionParameterInstance/@ActionDateTime for instruction parameters | OrderInstanceSummary/@EndDateTime or ItemInstanceSummary/@EndDateTime for events |
| | or |  |
| | OrderInstanceSummary/@StartDateTime or ItemInstanceSummary/@StartDateTime for events | 
| [TIMESTAMP] | InstructionParameterInstance/@ActionDateTime for instruction parameters |   OrderInstanceSummary/@EndDateTime or ItemInstanceSummary/@EndDateTime for events   |
|  | or |
|  | OrderInstanceSummary/@StartDateTime or ItemInstanceSummary/@StartDateTime for events |  |

Placeholders for events that do not depend on recipe style or temporal relationship to step:

| Placeholder | Example |
| ----------- | ------- |
| [AREA] | constant string "AREA_CS" |
| [BATCHID] | OrderInstanceSummary/@OrderNumber |
| [DESCRIPT] | InstructionParameter/@Description |
| [HIGH] | InstructionParameterInstance/@High |
| [LOW] | InstructionParameterInstance/@Low |
| [PARAMETER] | InstructionParameter/@Name |
| [PHASE] | InstructionParameter/@Name |
| [PROCESSCELL] | constant string "PROCESSCELL_CS" |
| [PVAL] | InstructionParameterInstance/@CV |
| [SET] | InstructionParameterInstance/@Set |
| [UNIQUEID] | OrderInstanceSummary/@OrderNumber |
| [UNIT] | ItemInstanceSummary/@ActualUnitName |
| [VALUE] | InstructionParameterInstance/@CV |