---
title: Modularization revisited
nav_order: 4
---

Modularization is an advanced topic, that is not needed for starting your robot on a competition, yet after your initial success I strongly recommend to read, learn and use.

## Grouping code in Python - functions

In Python you can simply add the statements line-by-line and gradually grow the code.

This is quite straightforward and is a good start to explore. The downside is that you will find it very hard to fine-tune small portions of your code e.g. navigating from one mission to the next.

As in school you have lessons one-after-the-other and you do not mix your maths and literature notebooks, but rather group things to different books, and even lessons within.

In Python you can do the same with functions.

A function is a grouped line of code that we once define and can call at a later time. The definition groups the useful lines of codes by indenting them. If you select a few lines of code and press the Tab key the editor will do the trick for you.

```python
def my_code():
    print("apple")
    print("peach")
```

It is important to note that defining the function does not run it. To actually see your robot execute it you need to call the defined function at any point after the definition.

```python
my_code()
## will print 
## > apple
## > peach
```

This is a useful technique to group missions or parts of missions together and test them separately as long as they work reliably.

## Grouping code in Python - modules

While working on bigger projects you might want to group and even test your code even more separately.

Python lets you move certain pieces of code to a separate file - called module. Consider this module the same as a library of code.
This file module contains a set of functions you can include in your main application.

Since Pybricks v3.2, 2022 we have support for multi-file projects, where all the necessary files are imported and magically downloaded to the brick during the compile and download process.

Based on this logic you can group competition mission codes separately to files while keeping init and utilities together.

An sample file setup could be as follows.

### FILE: base.py
```python
import ...

hub = PrimeHub()
motor_left = Motor(Port.A, Direction.COUNTERCLOCKWISE)
motor_right = Motor(Port.B)
robot = DriveBase(motor_left, motor_right, 56, 114)
robot.use_gyro(True)
motor_attachment_left = Motor(Port.C)
motor_attachment_right = Motor(Port.D)
```

### FILE: main.py
```python
import base

def menu():
    white True:
        selected = hub_menu("1", "2", "3")

        # Based on the selection, run a program.
        if selected == "1":
            import mission1
        elif selected == "2":
            import mission2
        elif selected == "3":
            import mission3
```

### FILE: mission1.py
```python
import base
################################################
### MISSION 1
### solves: M12, M13, M08
### author: Jane
################################################
robot.straight(320)
motor_attachment_left.run_angle(130, 60)
...

```

### FILE: mission2.py
```python
import base
################################################
### MISSION 2
### solves: M05, M02
### author: Joe
################################################
robot.straight(320)
robot.turn(30)
...

``` 



---
[NEXT: Summary >>](9_summary.md)