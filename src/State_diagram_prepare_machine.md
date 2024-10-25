# State diagram preparing machine
The following state diagram describes the states of the task preparing of the machine

```plantuml
@startdot
digraph State{

graph [bgcolor="white"] 

rankdir="LR";
node[shape="circle"]

OFF
STANDBY
FILL_WATER  [label="FILL\nWATER"]
CHECK_PAD [label="CHECK\nPAD"]
PLACE_PAD [label="PLACE\nPAD"]
TASK_PREPARED [label="TASK\nPREPARED"]

OFF -> STANDBY [label="Turn machine ON"]
STANDBY -> CHECK_PAD [label="LED is ON"]   
STANDBY -> FILL_WATER [label="LED blinks, not enough water"]
FILL_WATER -> CHECK_PAD [label="Water is filled"]
CHECK_PAD -> PLACE_PAD [label="No pad placed"]
PLACE_PAD -> TASK_PREPARED [label="Pad is placed"]
CHECK_PAD -> TASK_PREPARED [label="Water is filled, pad is placed"]
TASK_PREPARED -> STANDBY
STANDBY -> OFF [label="Turn machine OFF"]

}
@enddot
```