---
uid: BIF_ConfigureSecurityForPIDataArchive
---

# Configure security for PI Data Archive

<!-- Static topic. No modifications usually required -->

If you are installing [!include[interface](../../../includes/product-short.md)] on a node other than the PI Data server, you must create PI trusts so that the following applications can access the server:

* PI Event Frames Interface Manager 
* [!include[interface](../../../includes/product-short.md)]

## PI Data Archive 3.4.380.36 or later

If you are using PI Data Archive 3.4.380.36 or later, [!include[interface](../../../includes/product-short.md)] can access PI Server using Windows Integrated Security. To use Windows Integrated Security, use PI System Management Tools to define a mapping that assigns the Windows user (or group) a PI identity that has the required permissions.

## PI Data Archive before 3.4.380.36

If you are using a version of the PI Data Archive before version 3.4.380.36, you must **create a PI trust** for the user who runs the interface. For tightest security, limit the trust to the hostname or IP address of the interface node and the application name.

### To create a PI trust

1. Open **PI System Management Tools** and connect to the target server.

1. Select **Security > Mappings & Trusts**.

1. Select the **Trusts** tab. 

1. Create a trust for PI Event Frame Interface Manager.

    Click the **Trust** icon and complete the wizard. For each page, enter the parameters detailed in the table below:

    Page | Parameters
    -----|-------------
    **Specify Trust Name and Server** | Enter a **Trust Name** (something like "PI Event Frames Interface Manager"). **Trust Description** is optional.
    **Select Type of Trust to Add** | Select **PI-API application**.
    **Application Name** | Enter `BIFConfig.exe`.
    **Specify Client Connection Information** | Enter either the host name or IP address for the interface node.
    **Select PI User** | Select the PI User that you are configuring the trust for.

1. Create a trust for [!include[interface](../../../includes/product-short.md)].    

    Click the **Trust** icon and complete the wizard. For each page, enter the parameters detailed in the table below:

    Page | Parameters
    -----|-------------
    **Specify Trust Name and Server** | Enter a **Trust Name** (something like "[!include[interface](../../../includes/product-short.md)]"). **Trust Description** is optional.
    **Select Type of Trust to Add** | Select **PI-SDK application**.
    **Application Name** | In **Application Name**, enter [!include[exe](../../../includes/product-exe.md)]. In **Windows Domain** and **Windows Username**, enter the credentials of the user running the application.
    **Specify Client Connection Information** | Enter either the host name or IP address for the interface node.
    **Select PI User** | Select the PI User that you are configuring the trust for.
