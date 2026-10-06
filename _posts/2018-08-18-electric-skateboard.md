---
layout: post
title: "My Electric Skateboard Build"
date: 2018-08-18
---

*Originally written in 2018 on my old blog. Revised.*

I built an electric skateboard. When I wrote this I'd only ridden it seven miles, so I couldn't tell you the range, but I could tell you it was scary fast and a lot of fun.

## The electronics

The electrical side was the easy part: a battery, a brushless motor, an electronic speed controller, an Arduino and a Bluetooth module, all screwed and glued into a waterproof case on the underside of the deck.

## The controller

I wrote the control system myself. An Android app sends commands over Bluetooth, and the Arduino reads them and gradually raises or lowers the value the speed controller responds to. Ramping gently instead of jumping straight to a value keeps it from launching you off the board. The app had a speed slider plus buttons for brake, coast, cruise and fine adjustments.

## What I'd do differently

- **Bigger wheels and more clearance.** It's fast, and I wished it sat higher off the ground on larger inflatable tires.
- **More gear reduction.** Electric motors have weak torque at low RPM, so starting from a stop was the board's weak point. I'd pick a kit with a lower gear ratio.
- **Check that the drive gear fits your wheel before you order.** That was the hardest part of the build. My belt ended up at maximum tension, and I added idler bearings on each side to keep it tight.

Small as it was, it was one of the first projects where I wrote the firmware, the app and the hardware integration all myself, and saw it work in the real world at speed.
