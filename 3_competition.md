# Competition code

In my experience of 10 years coaching teams the recipe for robot performance success contains at least the following elements.

* reliable navigation - acceleration, deceleration, gyro based drive correction
* reliable motor control - acceleration, deceleration, stall detection and handling
* modularized code - testing a certain part of the code is easy
* easy prototyping - fast trial-and error cycles
* ability to easily and reliably copy-paste parts of code, try different versions
* reliably save and track dfferent versions
* ability to work on multiple computers parallel
* dedicated planning for strategy, grouping of missions based on distance, potentially shared or grouped attachment functions
* ability to reevaluate mission strategy, mechanical attachment strategy and navigation strategy including code
* separation of robot stages
  * reliably leaving the base
  * navigating near to the mission model
  * navigating to the mission model
  * solving the mission model - active or passive way
  * navigating away from the mission model
  * ... repeat with next model
  * arriving back to the base, minimizing operator error on re-placement and attachment change

## Boilerplate code

Here you find a a simple boilerplate code solving a multi-mission robot competition such as FIRST LEGO League Challenge.

```python
from pybricks.hubs import PrimeHub
from pybricks.pupdevices import Motor, ColorSensor, UltrasonicSensor
from pybricks.parameters import Button, Color, Direction, Port, Side, Stop
from pybricks.robotics import DriveBase
from pybricks.tools import wait, StopWatch, hub_menu
from pybricks import version

################################################
### INIT SECTION
### initializing the base pybricks objects
################################################
hub = PrimeHub()
motor_left = Motor(Port.A, Direction.COUNTERCLOCKWISE)
motor_right = Motor(Port.B)
robot = DriveBase(motor_left, motor_right, 56, 114)
robot.use_gyro(True)
motor_attachment_left = Motor(Port.C)
motor_attachment_right = Motor(Port.D)
time = StopWatch()

################################################
### MENU
### chooses the round
################################################
def menu():
    white True:
        selected = hub_menu("1", "2", "3")

        # Based on the selection, run a program.
        if selected == "1":
            mission_1()
        elif selected == "2":
            mission_2()
        elif selected == "3":
            mission_3()

################################################
### MISSION 1
### solves: M12, M13, M08
### author: Jane
################################################
def mission_1():
    robot.straight(320)
    motor_attachment_left.run_angle(130, 60)

    robot.straight(100, Stop.COAST)
    robot.drive(100, 10)
    wait(500)
    robot.drive(50, 10)

...

################################################
### MAIN CODE
################################################
menu()

```


---
[NEXT: Modularization revisited >>](4_modularization.md)