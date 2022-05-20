---
uid: BIF_TemplatesTab
---

# Templates tab

<!-- Customized for FactoryTalk -->

Templates map data from the data source to PI tags, batches and event frames. When defining templates, you specify the data to be written and the events that trigger the update. To define templates using PI Event Frame Interface Manager, go to the Templates page and navigate to the desired type of template. You can configure templates that map the source data to string, integer or float data types. For each type of template, you specify triggers, which are conditions that active the template.

You can define the following types of templates:

<!-- Added "Link" to list, removed "Alarm tag" -->

* **Property:** Maps data to batch properties in the PI Batch Database or event frame attributes in PI AF.
* **Recipe:** Defines the information stored and the naming convention used at each level in the generated batch hierarchy.
* **Tag:** Creates and updates PI tags, specifying how they are named and what data is written to them.
* **Link:** Associates event frames from one interface to another.

**Note:** When multiple property and recipe templates are defined that can set the same event frame attribute value using the same event, property templates take precedence. The following precedence order is observed for conflicting properties that set the same event frame attribute value:

1. Property templates
2. Default Recipe Property templates
3. Recipe Property templates

The following sections provide details about the specific types of templates.
