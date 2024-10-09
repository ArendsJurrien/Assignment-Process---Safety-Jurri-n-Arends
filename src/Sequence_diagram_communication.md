# Sequence diagram communication
The following sequence diagram shows the communicating between the tasks
- GVL = Controller 

```plantuml
@startuml


Prepare_Machine -> Controller: Waterlevel
Activate Prepare_Machine #BLUE 
activate Controller #RED
Prepare_Machine -> Controller: Pad inserted
Deactivate Prepare_Machine 


Brew_Coffee -> Controller: Read waterlevel
Activate Brew_Coffee #Green 
Brew_Coffee -> Controller: Read pad inserted
Controller -> Brew_Coffee: TRUE
Brew_Coffee -> Controller: Start brewing
Deactivate Controller
Deactivate Brew_Coffee

@enduml
```
