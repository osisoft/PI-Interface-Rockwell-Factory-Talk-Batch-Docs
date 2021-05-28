---
UID: Emersonstartandstopevents
---

# Emerson start and stop events

The start and end times set by the interface depend on the type of data source and whether the "Use Batch Recipe" (UBR) option is enabled. The UBR option is provided for backward compatibility with the PI EVT File interface.) The sections below provide details about how the interface determines start and end times.

## Event Files Data Source

The interface detects start and end events by scanning the [EVENT] field for "State change" events. To determine whether the event is a start or end, the interface scans the [PVALUE] field. To determine the level that started or ended, the interface checks the [RECIPE] field.

## EVT File Default Start and Stop Events
| Recipe Level |   | [PVALUE] | Remarks |
| ------------ | - | -------- | ------- |
|  | Start | End |   |
| Batch | "CREATED" | "REMOVED" |  |
| Unit batch | "RUNNING" | "COMPLETE", "STOPPED", or "ABORTED" | Requires equipment acquisition or release event: [EVENT] = "Recipe Arbitration" and [DESCRIPT] = "Resource Acquired by recipe" or "Resource Release by recipe" . For unit batch start time, the interface uses the timestamp of the start event or equipment acquisition event, whichever is latest. For end time, it uses the timestamp of the end event or the equipment release event, whichever is earliest. The interface reads the unit name from the [PVALUE] field. |
| Operation | "RUNNING" | "COMPLETE", "STOPPED", or "ABORTED" |  |
| Phase | "RUNNING" | "COMPLETE", "STOPPED", or "ABORTED" |  |
| Phase state | "RUNNING" | n/a | The start of a phase state ends any preceding phase state. If the interface detects multiple start or end events for the same phase state, it uses the first event. |
| Phase step | n/a | n/a | To enable phase steps, specify the /RAS flag in the INI file or, using PI Event Frames Interface Manager, go to the Batch Setup page and enable Report As Step and specify start and end text. Phase steps do not create higher-level procedures, unit procedures, and so on, if a parent phase is not found. If no phase step close event is found, the phase step is closed when its parent operation is closed. The interface ignores any zero-duration phase steps. |

## EVT File "Use batch recipe" (UBR) Enabled Start and Stop Events
| Recipe Level | [EVENT] | [PVALUE] |
| ------------ | ------- | -------- |
| Batch | "System Message" | "Beginning/End of Batch" or "<level> Started/Finished" |
| Unit batch | "System Message" | "Beginning/End of Batch" or "<level> Started/Finished" |
| Operation | "System Message" | "Beginning/End of Batch" or "<level> Started/Finished" |
| Phase | "State Change" | "RUNNING", "REMOVED","COMPLETE", or "ABORTED" |
| Phase state | "State Change" | <state name> |

## SQL Batch Historian SQL Query Details

The DeltaV BES stores its batch execution history using Microsoft SQL Server. The interface retrieves history from the DVHisDB database.

## SQL Default Start and Stop Events
| Recipe Level | [EVENTTYPE] | [EVENTDESCRIPT] |   |
| ------------ | ----------- | --------------- | - |
|   |   | Start | End |
| Batch | "State Change" | CREATED | REMOVED |
| Unit batch | "State Change" | RUNNING | COMPLETE, STOPPED or ABORTED |
| Operation | "State Change" | RUNNING | COMPLETE, STOPPED or ABORTED |
| Phase | "State Change" | RUNNING | COMPLETE, STOPPED or ABORTED |
| Phase state | n/a | User-specified text | Last phase state in phase: COMPLETE, STOPPED or ABORTED, or parent level ends. Preceding phases end when next phase state starts. |

To detect start and end events, the interface queries the following views by default:
* brecipestatechangeview
* batcheventview
* batchequipmentview

By default, batch event start and end times are read from batcheventview. For recipes above phase-level recipes, unit batches require equipment acquisition and release events (unless equipment arbitration events are unavailable). For equipment arbitration events, the interface reads the [AcquireTime] and [ReleaseTime] values from batchequipmentview. For phase states, the start of a state ends any preceding state (in other words, there are no explicit end events for phase states.)

## SQL UBR Start and Stop Events
| Recipe Level | Database View | Start time column | End time column | Remarks |
| ------------ | ------------- | ----------------- | --------------- | ----- |
| Batch | batchrecipeview | [ActivateTime] | [DeactivateTime] | For "procedure" events |
| Unit batch | batchrecipeview | [StartTime] | [EndTime] | Plus [AcquireTime] and [ReleaseTime] from batchequipmentview |
| Operation | batchrecipeview | [StartTime] | [EndTime] |   |
| Phase | batchrecipeview | [StartTime] | [EndTime] |  |
| Phase state | brecipestatechangeview or batcheventview | [StartTime] | 
[EndTime] | [EventType] field = "State Change" and [EventDescr] field containing the substring <state name> |

To detect the start and end of levels when the UBR option is enabled, the interface queries the following views:

* batchrecipeview
* batchequipmentview
* brecipestatechangeview
* batcheventview

For operation- and phase-level recipes, the interface creates the parent levels (unit batch and batch).

The interface retrieves history from the DVHisDB database, primarily using a query that returns the union of the following tables:

* bactivestepchangeevent
* bmaterialchargerequestevent
* bmaterialchargeevent
* bpausestatusevent
* bequipmentselectionevent
* bphaselinkpermissiveevent
* brecipemodechangeevent
* brecipemodecommandevent
* brecipestatechangeevent
* brecipestatecommandevent
* brecipevaluechangeevent
* brecipevaluerequestevent
* breportevent
* btextmessageevent
* bphasebatchrequestevent
* brecipecomment
* unhandledbatchmsg

In addition, the interface retrieves batch-related data from the following views:

| View or Table | Contents Queried For |
| ------------- | -------------------- |
| batchview | uniqueid, batchid, start time, end time, product, uniqueid and archived flag with new archived database name for all batches. |
| brecipestatechangeview | State change events, which are used by default to detect start and end of recipe levels. |
| batchrecipeview | Recipe data, equipment linkage, start and end time for each object. |
| batchequipmentview | Equipment arbitration events |
| batcheventview | Batch-associated data. Queried only if Use original batch event view (UOBEV) option is enabled. The [DESCRIPT] column is parsed for [PVAL] and [EU]. |
| localevars | Used to convert local start and end times with DST offsets to GMT time and then to UTC seconds. |

To detect start and end events, the interface queries the following views by default:

* brecipestatechangeview
* batcheventview
* batchequipmentview

Batch event start and end times are read from batcheventview. For recipes above phase-level recipes, unit batches require equipment acquisition and release events (unless equipment arbitration events are unavailable). For equipment arbitration events, the interface reads the [AcquireTime] and [ReleaseTime] values from batchequipmentview. For phase states, the start of a state ends any preceding state (in other words, there are no explicit end events for phase states.)

To detect the start and end of levels when the UBR option is enabled, the interface queries the following views:

* batchrecipeview
* batchequipmentview
* brecipestatechangeview
* batcheventview

## OPC A&E

To detect start and end events for all recipe levels, the interface uses BATCH-EVENT events with Event Attribute [6] = "State Changed". The interface examines Event Attribute [8] to detect start and end as follows:

* Start: <batch recipe level> RUNNING
* End: <batch recipe level> COMPLETE/ABORTED/STOPPED

No phase state data is available from this data source.

## Syncade

For each level, Syncade records the start time in the [StartUtcDateTime] timestamp and end time in the [EndUtcDateTime] timestamp of the object in which the event is recorded. For phase- and operation-level recipes, the interface creates parent procedures and unit procedures, using the start and end times of the operation or phase to start and end the parent levels. Syncade does not provide phase state or phase step data. The batch ID comes from the batch object's [OrderNumber] property, and the batch recipe type is provided for each object by the data source.
