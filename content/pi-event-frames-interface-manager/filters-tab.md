---
uid: BIF_FiltersTab
---

# Filters tab

<!-- Topic requires customization for specific interface -->

You use the **Filters** tab to configure the recipes, units, phases, or phase states to be excluded from processing by the interface. <!-- TU: Maybe add something like "The following filters are available" -->

* **Skip Phases (/SKIPPHASES)**

    The interface ignores any event that contains the specified phases in the [Phase] or [Phasemodule] column. 

* **Skip Units (/SKIPUNITS)**

    The interface ignores any event containing the specified units in the [Unit] column. 

* **Skip Recipes (/SKIPRECIPES)**

    The interface ignores any event containing the specified recipe in the appropriate column ([Procedure] for a procedure recipe, [UnitProcedure] for a unit procedure recipe, and so on.) 

* **Exclude Phase States (/EXCLUDESTATES**

    The interface ignores phase state events that contain the specified phase states in the [PhaseState] column. 
