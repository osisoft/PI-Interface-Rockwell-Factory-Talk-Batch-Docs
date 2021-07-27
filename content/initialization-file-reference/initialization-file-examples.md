---
uid: BIF_InitializationFileExamples
---

# Initialization file examples

<!-- Customized for FactoryTalk. Remove DeltaV examples. -->

## Multiple EVT Sources

```text
[SOURCE TEMPLATE] 

Source[1].evtdir=c:\test\evt 
Source[2].evtdir=\\factorytalk\\journals\evt 

[GENERAL] 

Excludestates=COMPLETE, ABORTING Equipment = abs:[Unit]\[PhaseModule]\Misc 

[TAG TEMPLATE] 

// [Basic Tag template, triggered on Event=Report, aliases are created as tag name] 

Tag[1].Name = [Unit]_[PhaseModule]_Report 
Tag[1].Value = [Pval] 
Tag[1].Type = Float // [Tag template with custom aliases, triggered on Event=Owner Change] 
Tag[2].Name = [Unit]_[PhaseModule]_Owner Change 
Tag[2].Value = [time]_[Descript] 
Tag[2].Type = String 
Tag[2].unitalias = [PhaseModule] Owner Change Me 
Tag[2].phasealias = Owner Change Me 

// [Tag template with custom aliases, triggered on set of events defined as triggers] 

// [Note: Unitalias and Phasealias are NOT going to be created since there are no Unit or Phase Module 

// defined in the tag name] 

Tag[3].Name = Generic Tag 
Tag[3].Value = [time]_[Event]_[BatchID]_[pval] 
Tag[3].Type=String 
Tag[3].trigger = Report 
Tag[3].trigger = Owner Change 
Tag[3].trigger = Operator Prompt 
Tag[3].unitalias = [phasemodule] abcd 
Tag[3].phasealias = testing [PROPERTY TEMPLATE] Property[1].Value = [Time] State Change [Descript] [pval]
```

