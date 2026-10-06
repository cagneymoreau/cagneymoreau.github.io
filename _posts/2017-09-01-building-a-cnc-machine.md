---
layout: post
title: "How I Built a CNC Machine From Aluminum Plate"
date: 2017-09-01
---

*Combined from a series of posts on my old blog, 2017–2018. Revised.*

I wanted to build things I couldn't buy, and that meant I needed a machine that could make parts. So the first real project was a CNC machine of my own design, built from aluminum plate and a kit of parts ordered online. It ended up milling wood and aluminum, cutting with a plasma torch, burning with a laser diode, and later 3D printing.

## The basics

A CNC (computer numerical control) machine moves a tool tip through 3D space with computer-controlled motors. The tool can be anything from a marker to a router bit to a laser. Mine is a three-axis machine: one motor for each direction (forward/back, left/right, up/down).

There are two common layouts:

- **Moving gantry:** the bed stays still and a gantry rolls along it. It's easier to attach hoses, sprayers and dust collection, and you get a bit more working area.
- **Moving bed:** the gantry is fixed and the bed slides. The moving part is usually smaller and lighter.

I went with a moving gantry on a frame that sits on a table.

The biggest early decision is what you'll actually cut. A machine for 3D printing or engraving can be light, and light is an advantage: smaller motors and less mass let it move faster. Milling wood or metal needs a much stiffer, heavier machine, which is harder to build and usually slower.

## Frame: stiffness over strength

Frame design is a trade-off between weight and strength. More mass resists outside forces, but it takes more power to move and it throws more weight around, which tests the table and the rails.

A lot of builders use 1/2" aluminum plate. I used 1/4" and braced it with aluminum angle. The point of the angle wasn't strength but **stiffness**: resisting deflection even under small loads. Once the angles were on, the difference was obvious. I also added cross-bracing across the top of the gantry, going from the standard two connection points to six. That added a pound or two, against the roughly 10 lb I saved with the thinner plate. I didn't measure the vibration, I judged it by sight and sound, but it's the one modification I'd recommend to anyone.

I made the base from steel, thinking the machine would be so rugged it needed it. In hindsight, the aluminum extrusion most people use would probably have gone together more accurately.

## Size and rails

Plan for the working area to end up 5–10 inches smaller than the table under it. Build a dedicated table, because there will be parts and wires hanging off everything.

Bigger isn't automatically better. Long ball screws sag. Hold your arm straight out and see how long before it droops, and a ball screw is no different. My longest screw deflected slightly, and as the motor spun it set up a wobble that made the machine shudder. The real fix is a larger screw and motor.

I bought a hobby linear-rail kit. For the price it did a good job, but I'd change two things. My rails face sideways, which loads the bearings at an angle so only part of each bearing carries the weight. And round rails with ball bearings riding directly on them collect dust. V-groove bearings running on an angled rail keep the bearings protected and the dust outside.

## Motors and electronics

I used 425 oz-in stepper motors, which came in a kit with a power supply and drivers. An oz-in is exactly what it sounds like: that many ounces of force one inch from the shaft. A rough guide for picking motors:

- ~166 oz-in: small 3D printing or engraving
- ~250 oz-in: milling wood or a larger 3D printer
- ~400 oz-in: milling non-ferrous metal

The force a ball screw can deliver works out to roughly *T = L × P / 5.65*, where *T* is the motor torque (oz-in), *L* is the screw's lead (inches per turn), and *P* is the axial load (oz).

Each motor connects to a driver, and each driver gets its step and direction signals from a breakout board. My drivers are wired active-low, switching the negative side of the circuit. I set them to 1,600 steps per revolution.

A few lessons:

- **Use a real E-stop.** I don't like the E-stop being part of the logic circuit. Put a plain 120 V switch in line so you can kill the motors and spindle instantly, without relying on electronics.
- **Don't use the breakout board's built-in relay.** Add a separate circuit to isolate it.
- **Solder connections once you know they work.** Wire nuts eventually fail.
- **A computer power supply** is an easy source of 5 V and 12 V.

## Software

I run two computers: one for design and one for machine control. Design software can bog a computer down, and you don't want that happening mid-cut. I tried LinuxCNC, but by that point I just wanted something that worked, so I used Mach3 for control (it connects through a parallel port) and Fusion 360 for design.

For the enclosure I used 1/8" acrylic sheet, plus a cheap curtain coated in liquid rubber.

## What it can do

- **Milling:** a 2 HP router as the spindle. Wood runs on a vacuum table. For aluminum I built a contained vise box, painted inside with shower waterproofing, with a sump pump spraying coolant on the bit. The first cut sprayed water everywhere, so I added walls. The bit stayed ice cold at 28k RPM.
- **Plasma:** a cheap plasma cutter on a dedicated 30-amp circuit. The big lesson: plasma throws off radio-frequency noise that can knock out your computer. Ground everything and put ferrite cores on the power and data cables so they don't act like antennas.
- **Laser:** a laser diode on the same relay setup as the other tools, for cutting or burning stencils. Black paper works best.
- **3D printing:** later I added an extruder, a fourth-axis driver, and a homemade temperature controller to turn it into a large-format printer.

## Tools you'll need

If you build the parts yourself, accuracy matters: a table saw for aluminum, a chop saw for steel, corner clamps, a drill press, center punches, digital calipers, a metal rule and square, a tap and die set, C-clamps, cutting oil, and real safety gear for your eyes, ears and lungs.

It isn't up to the standard of a commercial machine shop. But it made the parts for nearly everything I built afterward, and I learned more building it than I would have buying one.
