---
uid: RFTReleaseNotes
---

# Release Notes

PI Interface for Rockwell Factory Talk Batch

**Version 5.1.4.10**

## Overview

PI Interface for Rockwell FactoryTalk Batch 5.1.4 is an event-based interface that collects data from Rockwell FactoryTalk Batch System . The interface collects batch data from Event Journals, converts the data to PI tags and PI batch properties, and stores the collected data as event frames and elements within PI Asset Framework (PI AF). You can use tag templates to control PI point creation and event population. All modules, tags, tag aliases, and health tags are automatically created on the PI server.

The 5.1.4.10 release of PI Interface for Rockwell FactoryTalk Batch internally replaces PI SDK with AF SDK - this improves the security, robustness, and communication capabilities of the interface. As a result, this interface only writes Event Frames to a PI AF Server, and disallows creating PI Batches in the PI Batch Database.

Users creating PI Batches in the PI Batch Database need to migrate to Event Frames in order to utilize this version of the interface.

## Enhancements

There are no enhancements for this release.

## Fixes

This section lists items that were resolved or added in this release of PI Interface for Rockwell Factory Talk Batch.

| Work Item | Description                                                                     |
| :-------- | :------------------------------------------------------------------------------ |
| 22127     | Interface now properly creates Aliases for tag templates under AF. |
| 22132     | History recovery is fixed to prevent infinite loop scenario when querying for SQL data. In addition, fixed time as double to sting time conversions - There was a millisecond precision error converting the time stored as doubles to a time string. |
| 22133     | Attribute values referencing other event frames are captured regardless of the order event frames that are created. |
| 22137     | Constraint issues during a "Delayed Start" no longer happen. |
| 22140     | Unirecord data sources are now included in unirecord imports and exports. | 
| 22153     | Restore DESCRIPT handling in phase step logic. |
| 22156     | Cache start and end times can no longer be permanently altered by arbitration events. |
| 22158     | Debug messages should be logged correctly based on the configuration file. |
| 22162     | Non-PISDK communication/network errors do not attempt to retry the connection and no longer disrupt program flow. |
| 22166     | Running the interface second time in recovery mode resets the Event Frame's Attributes value timestamps. The Event frame attributes are processed differently during updates. |
| 22172     | When removing an interface from PI Event Frames Interface Manager, it will also remove any associated services. |
| 22178     | Event frames are now merged properly within the cache time. |
| 22181     | When adding an interface to PI Event Frames Interface Manager, the instance ID will be initialized as the same value of interface ID. |
| 22185     | Batch Interface events are sorted based on timestamputc. If two events have the same timestamputc, property events are processed last. |
| 22197     | The Auto generated Attribute names("Event_1", "Event_2" etc) are in proper sequential order (e.g., 1,2,3 etc.) |
| 22205     | Property templates are now assigned to the correct batch when there are multiple Procedures/Batches with the exact same name. |
| 22208     | PI EFIM now handles any differences in specifying module database Module Paths and event frames Element Paths correctly. |
| 22209     | Interface no longer has a delay in processing a batch when the local time is greater than GMT. |
| 22211     | MONITORTAGWINDOW now defaults to 0. This means that monitor tag counts do not get trimmed to the most recent <MONITORTAGWINDOW> days of activity and roll over at INT_MAX (unless MONITORTAGWINDOW is deliberately set). |
| 22216     | Interface ID has been added to the message logs in order to uniquely identify log message. |
| 22217     | UNDEFINED RecipeEvents with the same timestamputc are pushed to the end of the processing order to prevent issues regarding missing attributes. |
| 22218     | All generated unirecords will have the placeholder [TIMESTAMP] have the format "YYYY-MM-DD" for a SQL source and "YYYY/MM/DD" for non SQL source like EVT files. |
| 22219     | Unit procedure level event frames using different units are no longer merged. |
| 22221     | Monitor tags now accurately reflect the number of batches and their child events. |
| 22224     | Bifconfig properly creates new default virtual user service without errors. |
| 22235     | Interface configuration for RST and RET reads UnitedStates format standard. |
| 22245     | The unit procedure batch id attribute is controlled by the unit procedure recipe template batchid. |
| 22246     | BifConfig does not allow older interfaces to edit health tags. |
| 22249     | All batch interfaces remove passwords from INI file regardless of parameter capitalization. |
| 22250     | Merging issue causes unit procedure and operation not to close. |
| 22251     | Empty UniRecord dump files are no longer generated. |
| 22253     | History recovery using RST get the correct file based on the last line of the EVT file and recovers only the relevant EVT files. |
| 22260     | Batch event frames no longer merge event frames when merging is disabled and unique ids do not match. |
| 22268     | All RST and RET within the configuration will be parsed as US format. Fix in current development branch and in 4.3.x.x Branch. |
| 22275     | A check that verifies that a Procedure Event Frame and a Unit Procedure Event Frame are both generated by the same interface instance before linking them together. |
| 22283     | The Event log source is created during the interface install step. |
| 22299     | Rockwell FactoryTalk Batch installer works as expected, allowing for multiple batch interfaces to be installed on the same computer. Customer needs to uninstall existing Rockwell FactoryTalk Batch Interface before upgrading to latest version. | 
| 22301     | All health tags listed in the FTBInt user guide are created. |
| 22313     | Alarm and Event data is now queried by using the Ord Identity column instead of a mix of dates and the Ord Identity column Other than the initial interface start up and history recovery, this updated method does not rely on the date to query the A&E data. |
| 22326     | Upgrading from FTBInt 4.0 x to 4.1.x no longer creates duplicate entries in Programs and Features. |
| 22464     | For interfaces with a version 5.0.0 or greater, PI Event Frames Interface manager nows tail the windows event viewer instead of PI Message log. 
| 23099     | Linking can always be configured in BifConfig, if needed. | 
| 23177     | BifConfig now stores RST and RET as UTC Note that they can be edited in a local friendly time string and read into the interface correctly. When written by the configuration program, they will write the times out as UTC and a local time string as a comment. |
| 23811     | Change to PI interface for Batch message logging: We will not be using PI Message logging for the interface in version 5.0.0 x or higher. All message logging for the Batch interfaces will be in the Windows Event Viewer. Documentation on use and functionality of message logging for batch interfaces are in the user guide. |
| 24552     | BifConfig now updates the server information icon correctly. | 
| 24661     | Boost is no longer used for JSON processing. Microsoft Net library replaces it. |
| 25136     | BifConfig will display different options based on the installed interface version. |
| 25642     | Interface status tags that are automatically created by the interface can now be individually enabled/disabled. |
| 25811     | PI data server collectives and PI buffering to multiple PI data servers is now supported. |
| 26466     | Batch Interfaces now support an AF Interface Statistics element that stores the values of the PI tags recorded during interface execution. The location of the newly created element can be configured using the Batch Interface Configuration Manager and passed through the INI file. |
| 26756     | With the release of version 5, if you have a batch interface supported batch database, it will no longer be able to write to PIBatch Database. Version 5  only supports Event Frames Customers who need to write to PIBatch. The database needs to stay with Version 4.x.x.x Batch Interfaces. |
| 27053     | Added new logging level 3 (DB) to include Unirecord diagnostics messages into the message log. |
| 27091     | Extra emphasis on ensuring AF checkin is performed before disconnecting, as well as the addition of the AFAutoCheckin feature. |  
| 67289     | UniRecord exports now include all UniRecord fields. |
| 67298     | Event sorting is faster and memory consumption is better managed during event queuing. |
| 67926     | Interface will not allow Batch events with a zero start time. |
| 68207     | BifConfig will now store SCAN values as low as one second without complaint. |
| 68907     | Default account to setup interface service is now Default Virtual User (NT Service/<Interface Instance Name>). |
| 69287     | Updated the BIFConfig utility to only allow TagPath properties to be set on Asset Templates and Property Templates. Fixed issue where the TAGPATH value was not being saved properly. |
| 69486     | All attributes are now created on the correct event frame. |
| 69854     | Interface supports failover and includes a health tag that can be monitored. |
| 70398     | Float tag values are now evaluated correctly. |
| 70403     | Message logging includes exception data. |
| 70471     | Very long log messages are successfully logged. |
| 72522     | Interface stability improvements. |
| 73489     | Interface no longer hangs due to locale thread lock issue. |
| 73498     | Setup kit creates the event source name under application logs to match with Interface application name, which is used by logging framework. | 
| 75880     | Procedure level recipe events are processed correctly and have no missing end times.  |
  
## Known Issues

There are no known issues for release 5.1.4.10

## System Requirements

### Operating Systems

This interface is a 64-bit application.

| Platform  | 64-bit Application  |
| :-------- | :------------------ |
| Windows Server 2022 (64-bit) | Yes |
| Windows Server 2019 (64-bit) | Yes | 
| Windows Server 2016 (64-bit) | Yes | 
| Windows 11 (64-bit) | Yes | 
| Windows 10 (64-bit) | Yes | 
  
## Distribution Kit Files

| Product   | Software Version  |
| :-------- | :------------------ |
| Microsoft Visual C++ 2019 Redistributable (x86) | 14.21.27702 |
| Microsoft Visual C++ 2019 Redistributable (x64) | 14.21.27702 |
| PI AF Client 2018 SP3 Patch 4 | 2.10.10.2539 |
| PI Interface for Rockwell Factory Talk Batch (FTBInt) | 5.1.4.10 |
| PI Network Subsystem Support (PINS)* | 3.4.435.538 |
  
*The PI Network Subsystem Support (PINS) component is not displayed on the installation welcome screen if the PI Data Archive is installed already.

### Installation and Upgrade

The PI Interface for Rockwell Factory Talk Batch can be installed or upgraded using the PI Interface for Rockwell Factory Talk Batch installation kit (FTBInt_5.1.4.10_.exe). This installation kit can be obtained by using the How to Download Products link listed in the OSIsoft Customer Portal How To's list. This list is located on the [OSIsoft Customer Portal](https://my.osisoft.com/).

For additional information regarding the PI Interface for Rockwell Factory Talk Batch installation, please see the Installation instructions portion of the PI Interface for Rockwell Factory Talk Batch User Guide. This user guide is available for download from the [OSIsoft Customer Portal](https://my.osisoft.com/).

### Uninstalling the PI Interface for Rockwell Factory Talk Batch

The PI Interface for Rockwell Factory Talk Batch Interface can be uninstalled using the *Programs and Features* list accessible from the *Windows Control Panel*. After accessing the Programs and Features list, select the entry named *PI Interface for Rockwell Factory Talk Batch (FTBInt)* and then select *Uninstall* from the menu.

## Security information and guidance

We are [committed to releasing secure products](https://docs.osisoft.com/bundle/security-commitment-and-disclosure-standards/page/securitycommitmentanddisclosurestandards.html). This section is intended to provide relevant security-related information to guide your installation or upgrade decision.  

We [proactively disclose](https://docs.osisoft.com/bundle/security-commitment-and-disclosure-standards/page/securitycommitmentanddisclosurestandards.html#vulnerability-communication) aggregate information about the number and severity of security vulnerabilities addressed in each release. The tables below provide an overview of security issues addressed and their relative severity based on [standard scoring](https://docs.osisoft.com/bundle/security-commitment-and-disclosure-standards/page/securitycommitmentanddisclosurestandards.html#vulnerability-scoring). 

There are no security vulnerabilities in this release. 
