---
uid: BIF_RecipeDefaultProperties
---

# Recipe templates default properties

<!-- Topic requires customization for specific interface (Rockwell FTB) -->

## Batch Level
The following are the recipe template default values for the BATCH level:

| Template | Default
| ----- | ----- |
| Name | [Procedure] 
| Batch ID | [BatchID]
| Product | [pval] |
| Product Trigger | [Event,value=\"Recipe Header\"][descript,value=\"Product Code\"]) |
| Category | OSIBatch |
| Template | Procedure |

**Default Properties**

[RECIPE]

The index in the recipe template heirarchy corresponds to the RECIPE item default property (1).

      Recipe[1].DEFAULTPROPERTY[1].NAME = Recipe
      Recipe[1].DEFAULTPROPERTY[1].VALUE = [PROCEDURE|UNITPROCEDURE|OPERATION|Phase|PhaseState|PhaseStep]

[PRODUCT]

The index in the recipe template heirarchy corresponds to the PRODUCT item default property (2).

      Product[2].DEFAULTPROPERTY[2].NAME = Product
      Product[2].DEFAULTPROPERTY[2].VALUE = [pval]
      Product[2].DEFAULTPROPERTY[2].TRIGGER = [Event,value="Recipe Header"][descript,value="Product Code"]

## Unit Batch Level
The following are the recipe template default values for the UNIT BATCH level:

| Template | Default
| ----- | ----- |
| Name | [UnitProcedure] 
| Batch ID | [BatchID]
| Product | [pval] |
| Product Trigger | [Event,value=\"Recipe Header\"][descript,value=\"Product Code\"]) |
| SearchByStartTime | true |
| SearchByEndTime | true |
| Category | OSIBatch |
| Template | UnitProcedure |
| Module Path | [AREA]\\[PROCESSCELL]\\[UNIT])

**Note** - Unitbatches can have the same name when SearchByStartTime and SearchByEndTime equal true.

**Default Properties**

[PROCEDURE] = 3

      .NAME = PROCEDURE
      .VALUE = [UNITPROCEDURE|OPERATION|Phase|PhaseState|PhaseStep]

[PRODUCT] = 2

      .NAME = Product
      .VALUE = [pval]
      .TRIGGER = [Event,value=\"Recipe Header\"][descript,value=\"Product Code\"]

[RECIPE] = 1

      .NAME = BatchID
      .VALUE = [BatchID]

## Operation Level
The following are the recipe template default values for the OPERATION level:

| Template | Default
| ----- | ----- |
| Name | [Operation] 
| Category | OSIBatch |
| Template | Operation |

## Phase Level
The following are the recipe template default values for the PHASE level:

| Template | Default
| ----- | ----- |
| Name | [Phase] 
| Category | OSIBatch |
| Template | Phase |
| Module Path | [AREA]\\[PROCESSCELL]\\[UNIT]\\[PHASEMODULE])

## Phase State Level
The following are the recipe template default values for the PHASE STATE level:

| Template | Default
| ----- | ----- |
| Name | [PhaseState] 
| SearchDirection | Reverse |
| SearchByStartTime | true | 
| SearchByEndTime | false |
| Category | OSIBatch |
| Template | PhaseState |

## Phase Step Level
The following are the recipe template default values for the PHASE STEP level:

| Template | Default
| ----- | ----- |
| Name | [PhaseStep] |
| Merge | false |
| SearchDirection | Reverse |
| Category | OSIBatch |
| Template | PhaseStep |

