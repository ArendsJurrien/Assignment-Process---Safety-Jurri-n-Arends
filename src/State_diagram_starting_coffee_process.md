# State diagram starting coffee process

The following state diagram describes the states of the task starting the coffee process

```plantuml
@startdot
digraph State{

graph [bgcolor="white"] 

rankdir="LR";
node[shape="circle"]

STANDBY
HEATING_WATER [label="HEATING\nWATER"]
CHOOSE_AMOUNT_OF_CUPS [label="CHOOSE\nAMOUNT\nOF\nCUPS"]
WAIT
COFFEE_FINISHED [label="COFFEE\nFINISHED"]

STANDBY -> CHOOSE_AMOUNT_OF_CUPS [label="Enough water and pad is placed"]
CHOOSE_AMOUNT_OF_CUPS -> HEATING_WATER [label="Amount of cups is choosen"]
HEATING_WATER -> WAIT [label="Water is heated"]
WAIT-> COFFEE_FINISHED [label="Coffee is brewed"]
COFFEE_FINISHED -> STANDBY


}
@enddot
```