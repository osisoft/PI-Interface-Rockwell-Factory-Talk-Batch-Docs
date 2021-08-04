---
uid: BIF_EventFileOperation
---

# Event file operation

<!-- Customized for FactoryTalk. Removed references to SQL start/end events -->

## Event journal start/end events

### Start

For recipes that run at or above the operation level, the event containing [EVENT] = "System Message" and [DESCRIPT] = "Operation Started" and [RECIPE] = "Operation" indicates the start of an operation.

For phase-level recipes, the event containing [EVENT] = "State Change" and [PVALUE] = "RUNNING" indicates the start of an operation.

### End

For recipes that run at or above the operation level, the earlier of the following events ends the operation:

* The event containing [EVENT] = "System Message" and [DESCRIPT] field = "Operation Finished"

Or

* The event containing [EVENT] = "State Change" and [PVALUE] field = "REMOVED" and [RECIPE] = "Operation".

For phase-level recipes, the interface assigns the operation start time from the batch recipe event containing [EVENT] = "State Change" and [PVALUE] = "RUNNING".
