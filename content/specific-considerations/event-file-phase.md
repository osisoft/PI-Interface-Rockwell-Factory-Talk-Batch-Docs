---
uid: BIF_EventFilePhase
---

# Event file Phase

<!-- Customized for FactoryTalk. Removed headings about SQL start/end events -->

<!-- Needs introductory sentence -->

## Event journal start/end events

<!-- Needs introductory sentence, but the real question is if this heading is needed because there is no second heading 2 -->

### Start

For recipes that run at or above the phase level, the event containing [EVENT] = "State Change" and [PVALUE] field = "RUNNING".

### End

For recipes that run at or above the phase level, the event containing [EVENT] = "State Change" and [PVALUE] field = "COMPLETE" / "STOPPED" / "ABORTED" / "REMOVED" ends a phase.
