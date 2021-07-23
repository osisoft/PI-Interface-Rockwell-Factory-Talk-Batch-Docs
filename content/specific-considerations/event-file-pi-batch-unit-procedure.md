---
uid: BIF_EventFilePIBatchUnitProcedure
---

# Event file PIUnitBatch unit procedure

<!-- Customized for FactoryTalk. SQL start/end events removed -->

## Event journal start/end events

### Start

For procedure- and unit procedure-level recipes, the interface requires both a start event and an "equipment acquired" event, as follows:

* [EVENT] = "System Message" and [DESCRIPT] field = "Unit Procedure Started"

And

* [EVENT] field = "Recipe Arbitration", [DESCRIPT] field = "Resource Acquired by recipe" and [EU] field = "Unit". The [PVALUE] field contains the actual unit name.
The latest timestamp is used as the start time for the unit batch.

Operation and phase-level recipes create parent batches and unit batches automatically. Operation-level recipes require a start event and an "equipment acquired" event. Phase-level recipes set the unit batch start time from the event that starts the phase; no equipment acquisition event is required.

### End

For procedure- and unit procedure-level recipes, the interface requires both an end event and an "equipment released" event, as follows:

* [EVENT] = "System Message" and [DESCRIPT] field = "Unit Procedure Finished".

And

* [EVENT] = "System Message" and [DESCRIPT] field = "Unit Procedure Finished".

And

* [EVENT] field = "Recipe Arbitration", [DESCRIPT] field = "Resource Released by recipe" and [EU] field = "Unit". The [PVALUE] field contains the actual unit name.
The earliest timestamp is used as the end time.

Operation-level recipes require an end event and an "equipment released" event. Phase-level recipes set the unit-batch end time from the event that ends the phase; no equipment release event is required.
