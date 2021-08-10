---
uid: BIF_InterfaceSelectionTab
---

# Interface Selection

<!-- Static topic. No modifications usually required -->

After opening **PI Event Frames Manager**, use the **Interface Selection** tab to create an instance of the [!include[interface](../includes/product-short.md)] on the host system.

Interfaces are modular. You can install one or more interface on the host system. You can also install more than one instance of the same interface on the host. Use the **Interface Selection** tab to add or remove interface instances.

## To add an interface instance

1. Open **PI Event Frames Manager** and select **Interface Selection**.

1. Click **Add interface**.

    **Step result:** The **Create new interface instance** window opens.

1. From **Select interface to configure**, select **[!include[interface](../includes/product-long.md)]**.

    **Note:** For each interface installed on the node, there is a menu item available within the drop-down.

1. From **Service ID**, enter a unique identifier for the interface. 

    **PI Event Frames Manager** defaults to a value of `1` and increments the value for each instance that you add.

1. From **Interface description (optional)**, enter a friendly description for the interface instance.

1. Click **OK**.

**Result:** A new instance of [!include[interface](../includes/product-long.md)] is created. The interface creates a new .ini file for the instance. For more information on this file, see [Instance .ini file](#instance-ini-file).
    
## To remove an interface instance

1. Open **PI Event Frames Manager** and select **Interface Selection**.

1. From the **Interface** drop-down, select the interface that you want to remove. Click **Remove interface**.

**Result:** The instance (and its .ini file) is deleted.

## Instance .ini file

When you create an interface instance using **PI Event Frames Manager**, it generates an .ini file for the instance. This file contains the instance's configuration settings.

This file is stored at [!include[interface](../includes/dir-long.md)]. The interface names each instance .ini file by combining "PI", the interface abbreviation, and the instance identifier. For example, the name of the .ini generated for your first instance of [!include[interface](../includes/product-short.md)] is  "PI[!include[interface](../includes/dir-short.md)]1".

This file can be useful during troubleshooting. You can open it and scan it for faulty settings. For more information on each setting in the file, see <xref:BIF_InitializationFileReference>.

**Important!** Do not edit .ini files directly. Editing these files manually is error-prone and may result in invalid configurations. Use the **PI Event Frames Manager** to edit configurations instead.
