---
layout: post
title: PCB design pointers/checklist
date: 2010-12-01
categories: [Circuit Design]
---
Pointers/Checklist to keep in mind while designing a new PCB.

1. Include “Power ON” LED and LEDs for debug
1. Include critical test points and extra VCC/GND railing/points
1. Holes for Wire to hold xtal
1. One way connectors only (RMC connectors)
1. Easy access reset and other switch (check size of nearby components).
1. Check if through hole components (especially 90 degree connectors) interfere with SMD/other components.
1. Holes on corners for spacers (3mm-5mm dia)
1. Space below and above ICs for removing IC from socket (if using an IC socket). Space for soldering iron, near bigger components like inductors and capacitors of power circuit
1. 0.1uF ceramic caps between VCC and GND
1. Everything on bottom layer should be mirror image (EAGLE top view)
1. Through hole connectors offer more strength
1. The rule of thumb for trace width is .010″[.0254] per 1 Amp external (normally 1.5 oz or .0021″[.0533]) and .040″[.1016] per 1 Amp internally (for 1/2 oz of copper)
1. Check component availability before incorporating in design
1. Use filled vias for heat dissipation in power circuits
1. Are all IC inputs terminated as required?
1. Do IC/components have necessary filter caps?
1. Are main circuit and branch circuits clearly identified?
1. Define board dimensions
1. Define top and bottom board clearance for stacked/hierarchical PCB assembly
1. Draw board border using .040″ line
1. Define/determine a fixed component direction
1. Add text to plane layer and to net names (GND, +5V, etc.).
1. Board part number in copper on bottom side. Board revision (in copper or manually marking).
1. For high current circuits, note current of branch circuits.
1. Defining branch circuits and their current requirements is important if the main branch is of very high current. If the main branch requires a .050″[1.27] trace and the branches only require a .008″[.2032] width, it makes no sense to route all branches with a .050″[1.27] trace.

<div class="text-center">
{% include figure.html path="assets/img/daq-top-view.jpg" class="img-fluid rounded w-50"%}
</div>
