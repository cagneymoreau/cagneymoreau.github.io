---
layout: post
title: "Building a Brushless Motor Controller Because Robots Have No Cheap Muscles"
date: 2019-07-05
---

*Originally written in 2019 on my old blog. Revised.*

Every project I take on teaches me something new. Oddly enough, it's never humility.

## The problem: no cheap, strong actuators

If you want to build a robot, there are almost no low-cost, effective options for actuation. Hobby servos are weak and expensive for what they do.

At the same time, the quadcopter market has made powerful brushless motors very cheap. The catch is that they come with electronic speed controllers (ESCs) that do quadcopter things: spin in one direction and speed up or slow down. A robot joint needs much more. It has to hold position, reverse, move slowly under load, and know where it is.

So I set out to make one of these motors do everything I needed.

## The controller

I used an Arduino Nano instead of a dedicated motor-control chip, mostly so I wouldn't depend on sourcing specialty parts. Nanos are cheap and I buy them in bulk.

The concept is simple: switch power into and out of the three motor phases in the right sequence so the stator coils pull the rotor's magnets around in a controlled way. Six pins drive three high-side and three low-side MOSFETs:

```
PIN chart        PWR  GND  Comp/BEMF
Phase A           2    3     8
Phase B           4    5     9
Phase C           6    7    10

Six-step commutation
PWR  GND  BEMF    Step       Short-step
 A    C    B    11010000    11011100
 B    C    A    11000100    11110100
 B    A    C    01001100    01111100
 C    A    B    00011100    11011100
 C    B    A    00110100    11110100
 A    B    C    01110000    01111100
```

My first version tried to sense rotor position from back-EMF, the voltage the spinning motor generates. That works for a drone, but not for a robot joint, because the motor often isn't spinning fast enough to produce a usable signal. I switched to Hall-effect sensors, which work well.

## How the code is organized

- **Timer 1** times the steps. Each tick advances a step counter, which gives precise step timing.
- **Timer 2** runs the PWM, and also checks whether a step is due and makes the pin changes.

Everything else lives in the main loop and runs as fast as it can: reading serial commands and reading the Hall sensors. New data goes into a variable, and the timers apply the change at the right moment. Only the two timers are time-critical. It's about a thousand lines of code, but between debugging the board and debugging the code, it took a while to get there.

The Hall sensors double as position encoders. That works well on its own, and better through a 39:1 gearbox, since each sensor step becomes a much smaller movement at the output.

## The board

I'm more comfortable writing code than designing boards. Sometimes board design felt like black magic: the calculations didn't work out and I ended up guessing toward a better result. The circuit itself is straightforward: six MOSFETs, three high-side and three low-side, switching power in or out of each phase. The Hall sensors use 10k pull-up resistors, with LEDs for debugging.

## Results

The first test with a gearbox moved 1 lb at a 10-inch arm. After more work on the code and hardware, it moved 10 lb at 10 inches. That's a lot of torque from a cheap drone motor, an Arduino, and a gearbox.

I also added a strain gauge so the controller can tell when to push harder against a load and when to give up. That part was still a work in progress.

The bigger lesson: when the part you need doesn't exist at a price you can afford, it's often worth understanding the problem well enough to build it yourself.
