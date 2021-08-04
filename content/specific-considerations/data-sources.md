---
uid: BIF_DataSources
---

# Data sources

<!-- Customized for Factory Talk -->

[!include[interface](../includes/interface-name.md)] can process data from multiple distributed-control Batch Execution Systems (BES) sources simultaneously, a process known as _parallel data processing_. For example, you can split the control logic of a manufacturing process split between upstream and downstream segments, with each segment controlled by a separate FactoryTalk BES. Although the logical batch is identical, the interface splits the batch-related data between two batch historians. 

This interface can merge data for such batches and store it in a single PI batch. For more details, see <xref:BIF_HowToMergeMultipleSourceBatches>.

Parallel data processing also solves the problem of shared unit control, where overlapping batch recipes access the same unit in different stages of their production cycles. The interface resolves this problem by acquiring data for the same time frame from multiple sources and combining time-ordered data using a single interface instance.

You can configure data sources for the [!include[interface](../includes/interface-name.md)] by updating its .ini file. To configure a data source, enter the full path to the directory containing .evt files.

For example: MyFactoryTalkHost.int.
    
**Note:** You only need to specify the hostname. You can omit the protocol.
