---
uid: BIF_RecipeTemplates
---

# Recipe templates

The interface includes a set of built-in default recipe templates that control the name assigned to each level in the batch hierarchy and the data stored at each level. To override the naming convention and data assigned to PI batches, unit batches, subbatches and event frames, you define recipe templates. To define recipe templates, launch the Event Frames Interface Manager and perform the following steps.

1. Go to the **Templates** page and navigate to the list of recipe templates.

2. Right-click the top Recipe node and choose **Add Default Templates**.

    A list of default recipe templates is displayed.

3. For the recipe levels that you want to modify, configure basic settings as follows:

    * **NAME**
    
        (Required) Defines the convention used by the interface to assign names to procedures, unit procedures, etc. You can use the advanced parsing parameters to define this field.
        
        Example: abc_[PROCEDURE].
        
        If the procedure field of the incoming event contains "Test", the resulting name is "abc_Test".
        
    * **BATCHID** 
    
        (Optional) Specifies the batch ID for the procedure or unit procedure.
    
    * **MODULEPATH**
    
        (Optional) For unit procedures (level 2) or phase (level 4), specifies where the recipe resides in the PI Module Database or PI AF element hierarchy. In the Module Database, the path specifies the location of the PIUnit for the unit batch.

    * **PRODUCT** 
    
        (Optional) Set the product for the recipe. Sets the Product field for procedures and unit procedures. To set the product field to the value read from the data source, specify the following placeholder: [PRODUCT]
    
    * **PRODUCTTRIGGER**
    
        (Optional) Sets the product for the recipe after the recipe object is created. Intended for use when the product is defined in a separate event. If a product trigger is defined, the product is defined by the event that satisfies the trigger. If no product trigger is defined, the product gets its value from the event that created the recipe, and the template is populated by the event's placeholder data.
        
        Example: 
        
        **[Parameter, Value="Recipe Header"] [Descript, value="Product Name"]**

    * **TRANSLATE**
    
        (Optional) To enable translation, set to TRUE. Default: FALSE

    * **MERGE**
    
        (Optional) To merge identically-named objects under the same parent, set to TRUE. Default: FALSE |

    The following placeholders are supported:

    * AREA
    * BATCHID
    * DESCRIPT
    * EU
    * EVENT
    * OPERATION
    * PHASE
    * PHASEMODULE
    * PHASESTATE
    * PHASESTEP
    * PROCEDURE
    * PROCESSCELL
    * PVAL
    * UNIQUEID
    * UNIT
    * UNITPROCEDURE
    * USERID
    * [*,value= "Field"]
    * [*,value= "mask"]

4. For event frames, you can configure the following additional settings.

    * **Descriptor**
    
        (Optional) Specifies the Event frame descriptor property for the particular source Recipe object.

    * **DefaultProperty[x].Name**
    
        (Optional) Name of the event frame template attribute. Valid values are Recipe, BatchID, Product and Procedure. Interface defined defaults place Recipe and BatchID at x=1, Product at x=2, and Procedure at x=3.

    * **DefaultProperty[x].Value**
    
        (Optional) Defines the event attribute expression that evaluates to a valid value.

    * **DefaultProperty[x].Trigger**
    
        (Optional) Defines the expression that specifies which event(s) to use to get the value.

        `[Event,value="Recipe Header"][descript,value="Product Code"]`

    * **DefaultProperty[x].UseFirstValue**
    
        (Optional) Use the first matching event for the event frame to get the value if set to T or True. The default behavior is to use the last matching event.

    * **Category**
    
        (Optional) For each recipe level, defines the event frame category. If the event that creates an event frame contains insufficient information, no category is assigned. To assign a category to an event frame after its creation, use Category[x].

    * **Category[x].Name**
    
        (Optional) For each recipe level, define the event frame category based on an event that is related to the particular recipe item. This setting can create as many categories as desired. The index is a positive integer that associate the Name and Trigger subproperties for the specific Category[x] property. If the AF category does not exist, the interface creates it. To use this setting, you must also specify the triggering event using the Recipe[#].Category[x].Trigger setting.

        Example: When the specified trigger event arrives, create an event frame, assigning it the SCR category.

        `Category[10].Name = SCRCategory[10].Trigger = [Descript, value="Formula Name"] [Pval, value="SCR 20051"]`

    * **Category[x].Trigger**
    
        (Optional) Defines the expression that triggers assignment of a category by the Recipe[#].Category[x] setting. There can be multiple triggers for a single Recipe[#].Category[x].Name. To use this setting, you must also specify the category to be assigned, using the Recipe[#].Category[x].Name setting.

        Example: When any of the specified trigger event arrives, create an event frame, assigning it the SCR category.

        `Category[10].Name = SCR`

        `Category[10].Trigger = [Descript, value="Formula Name"] [Pval, value="SCR 20051"]`
    
        `Category[10].Trigger = [Descript, value="Formula Name"] [Pval, value="SCR 20051_01"]`

        `Category[10].Trigger = [Descript, value="Formula Name"] [Pval, value="SCR 20051_02"]`

    * **Template**
    
        (Optional) For each recipe level, specify the event frame template. If the interface cannot find a matching event frame template, the template is left blank. To assign a template to an event frame after its creation, use the Template[x] property.

    * **Recipe[#].Template[x].Name**
    
        (Optional) For each recipe level, this dynamic property enables you to define the event frame template. Based on any event that is related to particular recipe item. This property can assign only one AF template to a particular event frame. The interface uses the first matching Recipe[#].Template[x] property to be assigned to an event frame. The index is a positive integer that associates the Name and Trigger subproperties for the Template[x] property. If you specify this property, you must specify the Trigger property.

        Example:

        `Template[10].Name = BATCH_A`

        `Template[10].Trigger = [Descript, value="Formula Name"] [Pval, value="SCR 20051"]`

    * **Recipe[#].Template[x].Trigger**
    
        (Optional) This property defines the triggering expression for the event frame template. There can be multiple triggers for a single recipe template. If you specify this property, you must specify the Name property.

        Example:

        `Template[10].Name = BATCH_A`

        `Template[10].Trigger = [Descript, value="Formula Name"] [Pval, value="SCR 20051"]`

        `Template[10].Trigger = [Descript, value="Formula Name"] [Pval, value="SCR 20051_01"]`

        `Template[10].Trigger = [Descript, value="Formula Name"] [Pval, value="SCR 20051_02"]`

5. To save your changes, click **Save Settings** in the left pane.
