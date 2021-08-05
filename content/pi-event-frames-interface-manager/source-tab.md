---
uid: BIF_SourceTab
---

# Source tab

<!-- Customized for FactoryTalk -->

<!-- Content below applies to all interfaces -->

Configure the data sources that you want the interface to read. To add a data source, right-click the top **Sources** node and choose the **Add** option for the type of source you are configuring. Complete the form to enter authentication information for the data source.

**Note:** [!include[interface](../includes/product-short.md)] stores the data source credentials you enter in Windows Credential Manager. For details, see <xref:BIF_WindowsCredentialManagerAuthentication>.

<!-- Custom content for interface below. This content may need removal due to DeltaV content. -->

You can configure the interface to collect real-time data from an OPC Alarms and Events server. If the interface loses connectivity to the specified OPC Alarms and Events server, it switches to the specified SQL server and continues to collect data until it is able to reconnect to the OPC Alarms and Events server.

<!-- To configure a DeltaV Event Chronicle (alarms & events) data source, you must specify mappings that ensure that process cell data is recorded correctly, because DeltaV Event Chronicle does not emit process cell information. -->
    
**Note:** To use explicit logins for an SQL data source, ensure that the user running the interface and the user configuring the interface are the same user. Database user name and Password are encrypted and stored in Windows Credential Manager. For details, see <xref:BIF_WindowsCredentialManagerAuthentication>.  