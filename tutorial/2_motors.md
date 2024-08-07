---
title: Motors
nav_order: 2
---

On this section we will learn how to deal with motors.

## Controlling a motor

To control a motor we need to tell the system about the fact that we do have a motor connected to the hub.

In the template we have already imported all that is needed to connect our motor. For completeness let's include the import statement, yet it is not really needed to duplicate this line in your complete code.

```python
from pybricks.pupdevices import Motor
motor1 = Motor(Port.A)
```

In the second line we simply define the motor instance variable by calling a function like structure we imported. Obviously we need to state at least to which port this motor is connnected to.

From this point we can simply drive the motor by time, target angle, relative angle.

```python
## run the motor with a low speed for 1 second
motor1.run_time(100, 1000)

## run the motor with a low speed for a clockwise 180 degree turn
motor1.run_angle(100, 180)
```

## Controlling two driving motors

To control each motor individually, we inform the system that there are indeed motors involved. Here, we specify where we have connected the motor and its rotation direction.

```python
motor_left = Motor(Port.E, Direction.COUNTERCLOCKWISE)
motor_right = Motor(Port.F, Direction.CLOCKWISE)
```

This way we can start moving our robot - one motor at a time.

```python
motor_left.run_angle(100, 90)
motor_right.run_angle(100, 90)
```

## Smarter pair of motors

Two motors themselves are still "dumb" capable only of rotating for a certain time, angle, or to a target value. To make our robot more efficient, PyBricks helps us by creating a theoretical "robot" — in this case, one with two wheels, where we only need to specify their size and distance apart.

```python
## left and right motors
## using small blue diameter 5.6 cm wheels and 11.4 cm axle track
robot = DriveBase(motor_left, motor_right, 56, 114)
```

After this, navigating on the field becomes quite easy as the system calculates how much the motors need to rotate for the operations below.

Normally you would need to use math, and trigonometry  to calculate the degree of wheel rotation for 10cm drive or using the wheel size and axle track the rotation to pivot turn 90 degrees.

```python
robot.turn(90) # turn right 90 degrees
robot.straight(100) # go forward 10 centimeter
robot.curve(114, 60) # turn in a curve 60 degrees
```

What's brilliant about this is that it accelerates and decelerates for advanced reliability, measures, and corrects to ensure the motors have turned the exact amount we requested.

Of course, wheel slippage can affect accuracy. One very good and recommended option is still aligning to walls and objects.

This firmware also supports using the gyro. From here, the same instructions can be used with more precision, with corrections based on the built-in gyro sensor.

```python
robot.use_gyro(True)
robot.turn(90) # turn right 90 degrees
robot.straight(100) # turn in a curve 60 degrees
```

---
[NEXT: Competition robot >>](3_competition.md)