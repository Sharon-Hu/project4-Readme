Read Me

Author: Ying Hu
Subject ID: COMP90048
Date: 24/05/2018

This file is to describe the strategy used for COMP90048 project 4 in detail.

The strategy is to add a new instruction to the guess list each time the guess
function is called. The new instruction is chosen based on the previous feedback of
previous movement. 

1. Previous feedback is empty, wall, pit
   The next instruction is to choose a direction to explore the map. If the feedback
   is empty or wall, the robot will choose a direction based on where it is. If the
   feedback is pit, the robot will choose a direction based on its former position
   which could not be a pit.

2. Previous feedback is smell
   The feedback before smell will be checked. If feedback is stench, which means the 
   wumpus is in the reversed direction of the previous position, the robot will make
   a reversed direction and shoot the rumpus. If not, the robot will shoot the wumpus
   immediately.

3. Previous feedback is miss
   It means the wumpus is not along the last direction the robot went. The robot
   will change another direction and go again.

4. Previous feedback is wumpus
   The previous visited positions before wumpus will be checked to see whether any 
   of them can shoot the wumpus. If there is no such position, the robot will go to 
   explore the map until such position was found.

5. Previous feedback is damp
   In case of wumpus hidding behind the pit, the robot will shoot immediately.

In updateState function, the legitimate position to travel in the map will be decided
by the feedback. If the feedback is not wall, pit, wumpus, the position is free to go
and will be used as next starting position. 



 