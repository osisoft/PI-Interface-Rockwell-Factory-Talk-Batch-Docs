---
uid: BIF_StartAndStopEvents
---

# Start and stop events

<!-- Customized for FactoryTalk. Removed heading related to Microsoft SQL Server, as FactoryTalk does not support SQL as a data source. Additionally, Use Batch Recipe is enabled only in RFT (by default). Unlike other interfaces, there is no option in the batch settings tab to disable. Confirmed by Gotham team (03/2023) that this is by design Opening paragraph is different than other interfaces. -->

Since the Rockwell Factory Talk interface enables the Use Batch Recipe option by default, the start and end times set by the interface depend upon the type of data source.

**Note**: You cannot disable the Use Batch Recipe option through the Batch Setup Tab in the Rockwell Factory Talk interface. We do not recommend disabling it through the .ini file. 

The sections below provide details about how the interface determines start and end times.

## Event Files Data Source

The interface detects start and end events by scanning the [EVENT] field for `State change` events. To determine whether the event is a start or end, the interface scans the [PVALUE] field. To determine the level that started or ended, the interface checks the [RECIPE] field.

## EVT File Default Start and Stop Events

| Recipe Level |  | [PVALUE] | Remarks |
|--|--|--|--|
|  | Start | End |  |
| Batch | "CREATED" | "REMOVED" |  |
| Unit batch | "RUNNING" | "COMPLETE", "STOPPED", or "ABORTED" | Requires equipment acquisition or release event: [EVENT] = "Recipe Arbitration" and [DESCRIPT] = "Resource Acquired by recipe" or "Resource Release by recipe" . For unit batch start time, the interface uses the timestamp of the start event or equipment acquisition event, whichever is latest. For end time, it uses the timestamp of the end event or the equipment release event, whichever is earliest. The interface reads the unit name from the [PVALUE] field. |
| Operation | "RUNNING" | "COMPLETE", "STOPPED", or "ABORTED" |  |
| Phase | "RUNNING" | "COMPLETE", "STOPPED", or "ABORTED" |  |
| Phase state | "RUNNING" | n/a | The start of a phase state ends any preceding phase state. If the interface detects multiple start or end events for the same phase state, it uses the first event. |
| Phase step | n/a | n/a | To enable phase steps, specify the [/RAS flag](xref:BIF_CommandLineParameterReference#ras-startstr-stopstr) in the INI file or, using PI Event Frames Interface Manager, go to the [Batch Setup page](xref:BIF_BatchSetupTab#report-as-step) and enable Report As Step and specify start and end text. Phase steps do not create higher-level procedures, unit procedures, and so on, if a parent phase is not found. If no phase step close event is found, the phase step is closed when its parent operation is closed. The interface ignores any zero-duration phase steps. |

## EVT File "Use batch recipe" (UBR) Enabled Start and Stop Events

| Recipe Level | [EVENT] | [PVALUE] |
| ------------ | ------- | -------- |
| Batch | `System Message` | `Beginning/End of Batch` or `<level> Started/Finished` |
| Unit batch | `System Message` | `Beginning/End of Batch` or `<level> Started/Finished` |
| Operation | `System Message` | `Beginning/End of Batch` or `<level> Started/Finished` |
| Phase | `State Change` | `RUNNING`, `REMOVED`, `COMPLETE`, or `ABORTED` |
| Phase state | `State Change` | `<state name>` |


