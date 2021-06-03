---
uid: FactoryTalkBatchDataSources
---

# FactoryTalk Batch data sources

The interface can process data coming from multiple sources simultaneously. This parallel processing is designed primarily for processing data from distributed-control Batch Execution Systems (BES). For example, the control logic of a manufacturing process can be split between upstream and downstream segments, with each segment controlled by a separate FactoryTalk Batch Executive system. Even though the logical batch is the same, the actual batch-related data is split between two batch historians. This interface can merge data for such batches and store it in a single PI batch. Refer to Merging Multiple Source batches (xref:Mergingmultiplesourcebatches) into a Single PIBatch for more details.

Parallel data processing also solves the problem of shared unit control, where overlapping batch recipes access same unit in different stages of their production cycles. This solution is achieved by acquiring data for the same time frame from multiple sources and combining time-ordered data using a single interface instance.

Data source(s) are configured in the INI file associated with the interface instance. The full path to the directory with EVT files is sufficient to configure a data source.

For example: MySyncadeHost.int.
	
You only need to specify the hostname and not the hostname and protocol combination. 