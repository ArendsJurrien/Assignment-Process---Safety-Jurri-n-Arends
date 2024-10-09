# Sequence diagram calling
The following sequence diagram shows the calling of the function by the tasks



Function call voorbeeld:

Elevator ask to controller: Open door
Controller returned: Doors open

```plantuml
@startuml
participant User

User -> Controller: Start up 
activate Controller #RED
Controller -> Standby: Start up
activate Standby #BLUE
Standby --> Controller: Started up
Controller --> User: Led goes on



@enduml
```