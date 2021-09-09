---
uid: BIF_EventFileOperation
---

# Event file Operation

<!-- Customized for FactoryTalk. Removed references to SQL start/end events -->

<!-- Needs introductory sentence -->

## Event journal start/end events

<!-- Needs introductory sentence, but the real question is if this heading is needed because there is no second heading 2 -->

### Start

For recipes that run at or above the operation level, the event containing [EVENT] = "System Message" and [DESCRIPT] = "Operation Started" and [RECIPE] = "Operation" indicates the start of an operation.

For phase-level recipes, the event containing [EVENT] = "State Change" and [PVALUE] = "RUNNING" indicates the start of an operation.

### End

For recipes that run at or above the operation level, the earlier of the following events ends the operation:

* The event containing [EVENT] = "System Message" and [DESCRIPT] field = "Operation Finished"

Or

* The event containing [EVENT] = "State Change" and [PVALUE] field = "REMOVED" and [RECIPE] = "Operation".

For phase-level recipes, the interface assigns the operation start time from the batch recipe event containing [EVENT] = "State Change" and [PVALUE] = "RUNNING".
