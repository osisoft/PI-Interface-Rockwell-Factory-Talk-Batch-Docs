---
uid: BIF_TemplatesForMappingDataSourceEvents
---

# Templates for mapping data source events

<!-- Customized for FactoryTalk -->

Templates enable you to capture data from the data source, specifying the format for the desired data and the events that cause the interface to capture the data. To configure templates, go to the PI Event Frame Interface Manager Templates tab. You can define the following types of templates:

| Template Type | Description |
|--|--|
| Property | Create and update event frame attributes using data from data source. |
| Recipe | Override the data source recipe level names. |
| Tag | Create and update PI tags using data from data source. |
| Link | Identify the value from event frame attributes that contain the batch ID of the batch that we want to link to as a child object. |

You can configure templates that map the source data to **string**, **integer** or **float** data types and configure the format of the information to be written to the target. The precise format of the events coming from the data source depends on the BES vendor. For detailed information, refer to the vendor-specific topic.
