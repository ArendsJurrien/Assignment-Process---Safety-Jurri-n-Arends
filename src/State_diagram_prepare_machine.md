# State diagram preparing machine
The following state diagram describes the states of the task 'preparing machine'.

```plantuml
@startdot
digraph State{

graph [bgcolor="white"] 

rankdir="LR";
node[shape="circle"]

OFF
STANDBY
WATER_FILLED  [label="WATER\nFILLED"]
POD_PLACED [label="POD\nPLACED"]
READY [label="READY"]


OFF -> STANDBY [label="Power On"] 
STANDBY -> WATER_FILLED [label="Enough water"]
WATER_FILLED -> POD_PLACED [label="Pod is placed"]
POD_PLACED -> READY [label="Amount of cups choosen"]
READY -> STANDBY [label="Preparing finished"]
STANDBY -> OFF [label="Power Off"] 

}
@enddot
```