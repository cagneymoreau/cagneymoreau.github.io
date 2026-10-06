---
layout: post
title: "Making Custom Parts Without a Machine Shop"
date: 2019-07-24
---

*Combined from several posts on my old blog, 2017–2019. Revised.*

Custom parts are hard to come by, and off-the-shelf parts rarely fit what you're actually trying to build. I wanted to make my own: worm drives, cams and gearbox parts for robot joints. My constraints were simple:

- **Time:** I didn't want to spend ten hours milling one part.
- **Money:** I didn't want to buy a pile of new machines.
- **Space:** my shop was full. A lathe wouldn't fit, and I wanted one badly.

## Three levels of tolerance

It helped to sort parts by how precise they need to be:

- **Low:** toys, exterior panels, frames and structure.
- **Medium:** low-speed gearboxes, actuators, machine internals.
- **High:** engine internals, high-speed gearboxes.

Most of what I needed was medium tolerance.

## First try: foam, plaster and sand

My first idea was to mill a pattern out of $5 foam insulation board, make a plaster mold from it, and cast aluminum. The foam milled quickly but not cleanly. The plaster stuck to the rough surface, the paraffin wax I used didn't release, and cutting the foam halves out threw off the alignment.

Next I tried sand casting in Delft clay, my first ever aluminum pour, using an oven I built. The result wasn't bad for a first attempt, but sand and lost-foam casting are really only good for low-tolerance parts, or parts you'll finish by machining anyway.

## What worked: wax, silicone and vacuum

I needed pressure to get detail into the metal, which led me to vacuum casting:

1. Mill each half of the part in **machinable wax**, with alignment keys so the halves mate.
2. Pour a two-part **silicone** (A45, harder than most) into each cavity, degassing it in a vacuum chamber I built, both in the cup and again in the mold.
3. Inject **jewelers' wax** into the silicone mold. To the naked eye it was identical to the original.
4. Invest the wax in **refractory plaster** (degassed twice), burn the wax out, then pour molten aluminum and switch on the vacuum immediately.

The milling marks on the original wax showed up perfectly in the aluminum. After three pours I had a list of fixes (thicker mold walls, better sprue joints, fewer bubbles in the plaster, a formula for size change), but it was clearly heading toward parts good enough for moderate mechanical work.

## Faster: lost-PLA casting

Once I had a 3D printer, I switched to printing the patterns in PLA and burning them out. It's much faster, and the shrinkage turned out to be predictable. I tracked the printed, wax and aluminum dimensions of each part against the target. For parts that fit in your hand, scaling the model to about 103–105% landed close to target size.

I also rebuilt the oven, since my original wiring didn't account for wattage and wire length and wore out quickly. I added an Arduino controller so I could program the heat-up and cool-down. One test part got whacked with a hammer to see if it would crack. It didn't.

## Circuit boards too

The same mindset applied to electronics. Hand-wiring prototype boards is tedious and error-prone, so I started milling my own circuit boards on the CNC:

- Design in Eagle with traces and spacing sized for your bit (I used 30-mil traces and 40-mil spacing).
- Use FlatCAM to turn the Gerber and drill files into G-code. Your tool has to be smaller than your spacing or it skips sections.
- **Float the Z-axis.** Even slight unevenness ruins a board. Instead of probing the whole surface, I spring-loaded the spindle on small slide rails so it rides over the board. Before that, traces tore and lifted. After, they came out clean.

With the process tuned, I could go from a solderless breadboard to a finished board in two to four hours.

## The takeaway

None of these methods replace a real machine shop. But together they let one person in a crowded garage turn an idea into a working part in days instead of weeks, and that changed what I was willing to try building.
