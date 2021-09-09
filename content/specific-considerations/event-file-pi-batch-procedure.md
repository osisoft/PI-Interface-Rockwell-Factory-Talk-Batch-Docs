---
uid: BIF_EventFilePIBatchProcedure
---

# Event file PIBatch Procedure

<!-- Needs introductory sentence -->

## Event journal start/end events

<!-- Needs introductory sentence, but the real question is if this heading is needed because there is no second heading 2 -->

### Start

[EVENT] = "System Message" and [PVALUE] = "Beginning Of BATCH"

### End

Either of these events end a batch:

* [EVENT] = "System Message" and [PVALUE] = "End Of BATCH"

Or

* [EVENT] = "State Change" and [PVALUE] field = "REMOVED", "COMPLETE" or "ABORTED"
