# Sequence diagram communication
The following sequence diagram shows the communicating between the tasks, user and visualization
- User = the real person who uses the coffee machine
- PRG_Person = the programmed person 

```plantuml
@startuml


User -> Visualization: Push 'Power' button
activate Visualization #RED
Visualization -> PRG_Person: Change var 'Power'
activate PRG_Person #BLUE
PRG_Person -> GVL: Power = TRUE
PRG_Person --> Visualization: Button 'Power' pushed
deactivate PRG_Person 
Visualization --> User: Button 'Power' changes
deactivate Visualization 
Prepare_Machine -> Visualization: Indicator 'LED' turns on

Prepare_Machine -> GVL: Check Waterlevel
GVL --> Prepare_Machine: Return waterlevel


User -> Visualization: Push 'Pod' button
activate Visualization #RED
Visualization -> PRG_Person: Change var 'Pod'
activate PRG_Person #BLUE
PRG_Person -> Prepare_Machine: Pod = TRUE
PRG_Person --> Visualization: Button 'Pod' pushed
deactivate PRG_Person 
Visualization --> User: Button 'Pod' changes
deactivate Visualization 

User -> Visualization: Push 'Cups choosen' button
activate Visualization #RED
Visualization -> PRG_Person: Change var 'Cups choosen'
activate PRG_Person #BLUE
PRG_Person -> Prepare_Machine: Cups choosen = TRUE
PRG_Person --> Visualization: Button 'Cups Choosen' pushed
deactivate PRG_Person
Visualization --> User: Button 'Cups Choosen' changes
deactivate Visualization 

Prepare_Machine -> GVL: Start brewing = TRUE
Brew_Coffee -> GVL: Start brew_coffee
activate Brew_Coffee #GREEN
Brew_Coffee -> Brew_Coffee: Heating water
Brew_Coffee -> Brew_Coffee: Brewing coffee
Brew_Coffee -> GVL: Start brewing = FALSE
Brew_Coffee -> GVL: Coffee brewed = TRUE
deactivate Brew_Coffee
Prepare_Machine -> GVL: Waterlevel -1
activate Prepare_Machine #ORANGE
Prepare_Machine -> GVL: Coffee brewed = FALSE
Prepare_Machine -> Visualization: Button 'Pod' deactivated
Prepare_Machine -> Visualization: Button 'Cups choosen' deactivated
deactivate Prepare_Machine
GVL -> Visualization: Update 'waterlevel'

User -> Visualization: Push 'Power' button
activate Visualization #RED
Visualization -> PRG_Person: Change var 'Power'
activate PRG_Person #BLUE
PRG_Person -> GVL: Power = FALSE
PRG_Person --> Visualization: Button 'Power' pushed
deactivate PRG_Person #BLUE
Visualization --> User: Button 'Power' changes
deactivate Visualization 
Prepare_Machine -> Visualization: Indicator 'LED' turns off













@enduml
```
