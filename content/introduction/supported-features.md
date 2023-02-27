---
uid: BIF_SupportedFeatures
---

# Supported features

<!-- TU: This is missing an introductory paragraph. It should describe what the table is doing -->
<!-- Default Framework topic -->


| Feature | Support |
| ------- | ------- |
| Part Number | PI-IN-RW-FTB-NTI |
| Auto-creates PI points and equipment assets? | Yes |
| Point Builder Utility | No |
| Stores batch data in PI Batch Database and PI Module Database | Yes |
| Stores batch data in PI AF | Yes |
| Supports equipment arbitration events | No |
| ICU control | No (use PI Event Frame Interface Manager configuration tool) |
| PI point data types | Int32/ Float32/ String |
| Sub-second timestamps | Yes |
| Sub-second scan classes | No |
| Automatically incorporates changes to PI point attributes | No |
| Exception reporting | No |
| Outputs from PI | No |
| Inputs to PI | Event-based |
| Supports questionable bit | No |
| Supports multi-character pointsource | Yes |
| Maximum point count | No maximum |
| Uses PI SDK | Yes: version 1.3.4.333 or higher required|
| Uses AF SDK | Yes: version 2.5.x or higher required |
| PINet string support | N/A |
| Source of timestamps | BES (not system time on interface node) |
| History recovery | Yes |
| UniInt-based | No |
| Disconnected startup | No |
| SetDeviceStatus | Yes |
| Failover | Yes |
| Vendor software required on PI Interface node | No |
| Vendor hardware required | No |
| Additional PI software included with interface | Yes  |
| Device point types | The interface receives data from source as strings and coerces the data into numerical types according to tag templates, if defined.|
| Serial-based interface | No |

## Equipment arbitration events

Rockwell FactoryTalk Batch supports equipment arbitration events. These events provide precise time stamps for the start and end times of unit batches. Individual installations of Rockwell FactoryTalk Batch that support equipment arbitration events may not be configured to provide such events. If your current instance of Rockwell FactoryTalk Batch supports equipment arbitration events but is configured not to provide them, use the following command line parameter: [/noarbitration](xref:BIF_CommandLineParameterReference#noarbitration). 

Using `/noarbitration` ensures that the interface:

* Sets the start time of unit batches using the timestamp of the "Unit Procedure Started" event or the start of the next operation or phase for the unit, whichever is later.

* Sets the end time of unit batches using the timestamp of the "Unit Procedure Finished" event or the end of the last operation or phase for the unit, whichever is earlier.

* For operation-level recipes, the interface uses the start time of the first phase as the start time for the parent operation and unit batch, and the timestamp of the "Operation Finished" message as the end time of the phase, operation and unit batch.

## History recovery

You can stop the interface without losing any data because the data is persistent in the data source. Data recovery is limited by the history available from the BES, the number of licensed PI tags, and the size and time frame of the PI archives into which data is recovered.

## Device status tag

This string tag contains information about communication between the interface and the data source. This tag is evaluated only while the heartbeat tag is updating. The tag is updated on startup, change, and shutdown.

During normal operation, the tag contains the digital state set value "Good", indicating that the interface is communicating properly with the data source. Otherwise, the tag contains a string indicating status.

The following table lists standard status strings.

| Message | Description |
|--|--|
| `1 Starting` | The interface is starting. |
| `2 Connected / No Data` | The interface is connected to the data source but is not capable of reading or writing data to the foreign device. |
| `3 n device(s) in error` | The interface is not able to communicate with the specified number of devices. Usually includes additional interface-specific details. |
| `4 Intf Shutdown` | The interface is shutting down. |
| `5 interface_specific_message` | Message specific to the interface. |
