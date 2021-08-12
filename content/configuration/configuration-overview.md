---
uid: BIF_ConfigurationOverview
---

# Configuration

Following interface installation, you must create an interface instance and configure each of its settings before you can begin data collection.

You can configure your interface instance using **PI Event Frames Interface Manager**. This tool allows you to configure each interface setting from an individual tab.

## To open PI Event Frames Interface Manager

Select **Start > All Programs > PI System > PI Event Frames Interface Manager**.

**PI Event Frames Interface Manager**
![PI Event Frames Interface Manager](../images/bifconfig.png)

## Configuration Overview

This overview provides a high-level outline of each setting that you must configure during the instance configuration process.

1. <xref:BIF_InterfaceSelectionTab>

    Use the **Interface Selection** tab to create a new instance of the [!include[interface](../includes/product-short.md)]. Interfaces are modular, letting you configure multiple interfaces one a single system. You can also create multiple instances of each interface.

1. <xref:BIF_ServerInformationTab>

    Use the **Server Information** tab to choose which PI Data server that you want to use with your interface. If you want to create event frames within PI Asset Framework, you will configure that here as well.

1. <xref:BIF_SourceTab>

    Use the **Source** tab to configure the data source for your interface. You can configure your [!include[interface](../includes/product-short.md)] instance to read from one or more data sources. Reading from multiple data sources lets you handle distributed batch processing scenarios, where multiple batch execution systems cooperate in the manufacturing of a single batch.

1. <xref:BIF_TemplatesTab>

    Use the **Templates** tab to define templates. Templates map data from the data source to PI tags, batches and event frames. When defining templates, you specify the data to be written and the events that trigger the update. You can configure templates that map the source data to string, integer or float data types. For each type of template, you specify triggers, which are conditions that active the template.

1. <xref:BIF_FiltersTab>

    Use the **Filters** tab to configure the recipes, units, phases, or phase states to be excluded from processing by the interface.

1. <xref:BIF_TimeSettingsTab>

    Use the **Time Settings** tab to configure how the interface handles loss of connectivity and how it processes data.

1. <xref:BIF_BatchSetupTab>

    Use the **Batch Setup** tab to identify the elements for various batch settings.

1. <xref:BIF_MergeSetupTab>

    Use the **Merge Setup** tab to configure merging of the batch generation.

1. <xref:BIF_OperationalSettingsTab>

    Use the **Operational Settings** tab to configure the interface mode and other related settings.
