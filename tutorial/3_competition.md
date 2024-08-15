---
title: Competition code
nav_order: 3
---

In my experience of 10 years coaching teams, the recipe for robot performance success contains at least the following elements.

# Keys to success 

## 1. Reliable navigation
Acceleration, deceleration, gyro-based drive correction for the driving motors.

## 2. Reliable motor control
Acceleration, deceleration, stall detection, and handling when using actuator motors for interacting with models.

## 3. Modularized code
You must be able to test a certain part of the code easily.

## 4. Easy prototyping
Fast trial-and-error cycles.

## 5. Ability to try different versions
Easily and reliably copy-paste parts of code, and try different versions.

## 6. Versioning
Reliably save and track different versions.

## 7. Multiple computers
Ability to work on multiple computers in parallel

## 8. Dedicated planning for strategy
Dedicated planning for strategy, grouping of missions based on distance, potentially shared or grouped attachment functions

## 9. Reevaluate mission strategy
Ability to reevaluate mission strategy, mechanical attachment strategy, and navigation strategy including code.

## 10. Separate robot stages

You must be able to separately plan and program the following stages.

1. reliably leaving the base
2. navigating near the mission model
3. navigating to the mission model
4. solving the mission model - active or passive way
5. navigating away from the mission model
6. ... repeat with the next model
7. arriving back to the base, minimizing operator error on re-placement and attachment change

# Boilerplate code

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