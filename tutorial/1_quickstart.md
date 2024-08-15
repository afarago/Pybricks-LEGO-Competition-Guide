---
title: Hands-on tutorial
nav_order: 1
---

Pybricks provides a programmable interface directly from a browser [code.pybricks.com](http://code.pybricks.com), which requires neither installation nor registration. The interface assists in creating a starter program, but we won't delve into that now.

# Changing the core

To use Pybricks you need to change the core hub program, called firmware that sits between and connects the hardware pieces to your user program.

This is an easy 2-3 minute process even at your first go, so there is nothing to worry about, just make sure you pay attention to the instructions.

Firmware is programming that's written to a hub hardware device's permanent memory. This memory is where the content is saved when the hub is turned off or the battery is removed or depleted. Pybricks serves as firmware or even as an operating system much like Windows, Linux, or MacOS on your laptop.
You can find awesome tutorials on firmware and operating systems over the internet like [this](https://www.techtarget.com/whatis/definition/firmware) or [that](https://en.wikipedia.org/wiki/Firmware).

{: .highlight }
For changing the firmware on your hub follow the [install-pybricks](https://pybricks.com/learn/getting-started/install-pybricks) tutorial (2-3 mins).\
Note: You can always get easily back to the official LEGO firmware.

# Creating your first program

Step-by-step:
1. Navigate to the [code.pybricks.com](http://code.pybricks.com) site
2. Create a new file using the plus sign
3. Select "python" as program type
4. Keep the "use template" switch on
5. Select your hub - SPIKE and Mindstorms Robot Inventor hubs are practically the same

```python
from pybricks.hubs import InventorHub
from pybricks.pupdevices import Motor, ColorSensor, UltrasonicSensor
from pybricks.parameters import Button, Color, Direction, Port, Side, Stop
from pybricks.robotics import DriveBase
from pybricks.tools import wait, StopWatch

hub = InventorHub()
```

# How to use Python

Python is suitable for writing quite complex programs, but our focus has been on the simplest usage. In the Pybricks environment, we program in Python, and the microcontroller at the heart of the hub communicates with us primarily in Python (MicroPython).

To make the hub understand our intentions the creators of Pybricks (Laurens Valk and David Lechner) categorized the available features into groups, much like organizing our drawings by theme into boxes. These groups are structured around physically tangible devices: hub, motor, color sensor, etc. Within each group, there are further subdivisions for easier management, separated by a dot (e.g., `hub.display`). Finally, we typically invoke a specific function, also separated by a dot and always ending with parentheses.

{: .task }
> 1. Find the PrimeHub `.display.icon()` in the [documentation](https://docs.pybricks.com/en/latest/hubs/primehub.html){:target="_blank"}
> 2. Use `Icon.HAPPY` as a parameter of the call
> 3. Replace the icon with another one
> 4. Using the `wait()` function display 3 different images with a 3 second delay.\  
>    NOTE: `wait(1000)` delays 1000 milliseconds, that is 1 second.
> 5. Clear the display after showing the last image

{: .task_solution }
> ```python
> hub.display.icon(Icon.HAPPY)
> wait(3000)
> hub.display.icon(Icon.DOWN)
> wait(3000)
> hub.display.icon(Icon.ARROW_UP)
> wait(3000)
> hub.display.off()
> ```

![tutorial_display](assets/tutorial_display.svg){:width="50%" .program_code}

# Playing with the hub

You can further play around with the key functions of the hub below `hub.buttons., hub.lights., hub.speaker.`.

```python
hub.system.beep()                           # hub beeps once.
```

Function calls can be more complex when we aim to achieve similar but not identical functionality. Here, we provide parameters within the parentheses to specify our intentions.

```python
hub.display.number(42)                      # hub displays number 42
hub.display.number(99)                      # hub displays number 99
hub.display.text("Hello FLL, Hello WRO")    # hub displays this text
hub.display.icon(Icon.HAPPY)                # display a happy icon
```



---
[NEXT: Simple motors >>](2_motors.md)