---
layout: project
title:  Lunar Lander Hazard Detection
description: Critical in the loop LiDAR landing sensor
image: assets/images/lidar-hd/main.png
imagewidth: 50%
order: 985
---

{:refdef: style="text-align: center;"}
_A simulation of the Griffin lunar lander over the lunar surface, with hazardous (red) and safe (blue) regions indicated._
<br>
Image Credit: Astrobotic
{: refdef}


Aboard the maiden voyage of Astrobotic's Griffin Lunar Lander - called **Griffin Mission 1 (GM1)** - several sensors are used to help the spacecraft safely touch down on the lunar surface. During the **Deorbit, Descent, and Landing (DDL)** phases of the mission, a vision-based Terrain Relative Navigation (TRN) system tracks the spacecraft's pose relative to the lunar surface and a [**LiDAR-based Hazard Detection (HD)**](https://www.astrobotic.com/stick-the-landing-astrobotics-cutting-edge-hazard-detection-lidar-system/) system scans the lunar surface for potentially dangerous features to avoid when landing. As a part of the perception and autonomy software team at Astrobotic, I've been working on the flight software for the HD system.

Lunar orbital assets have captured detailed imagery of the Moon's surface. However, the resolution of this data is insufficent to guarantee safety of a spacecraft attempting to land on the surface - multiple square meters of the terrain can be represented by just a single pixel. Thus, Griffin employs a downward-facing LiDAR, which scans the terrain below the lander to detect any potential hazards like rocks or small craters down to 15 cm in size.

{:refdef: style="text-align: center;"}
![Griffin Mission 1 (GM1) Deorbit, Descent, and Landing (DDL) diagram](/assets/images/lidar-hd/ddl-diagram.png){: width="50%"}
{: refdef}
{:refdef: style="text-align: center;"}
_The final steps of the DDL phase of landing, during which the HD LiDAR system scans the lunar surface._
<br>
Image Credit: Astrobotic
{: refdef}

During the final phase of descent, Griffin hovers about 100 m above the Moon's surface and triggers the LiDAR to scan the area below it. The raw point cloud data produced by this scan may be warped due to motion of the lander during the hover, however. To account for this, the HD system uses motion-correction algorithms to deskew the point cloud data and form an accurate representation of the features below the lander. Terrain slope and roughness metrics are then calculated and spacecraft-surface interactions are simulated. All this data is then integrated into an evaluation of the hazards present on the surface below the spacecraft. Finally, the HD system selects a site with minimal risk for landing, and sends this recommendation to the spacecraft's guidance, navigation, and control (GNC) systems. From there, the autonomous GNC systems divert the spacecraft to land at the recommended site.

{:refdef: style="text-align: center;"}
![Hazard Detection Pipeline](/assets/images/lidar-hd/hd-pipeline.png){: width="70%"}
{: refdef}
{:refdef: style="text-align: center;"}
_The pipeline for hazard detection from raw LiDAR point cloud data._
<br>
Image Credit: Astrobotic
{: refdef}

My work on the HD system has been focused at the middleware level of the flight software and the motion correction algorithms. This software needs to be both fast and reliable. The DDL phase of the mission occurs at a rate that precludes ground operator intervention, and thus must be completed entirely autonomously. On top of this, the spacecraft has limited fuel, so the powered hover over the surface cannot last forever. Thus, the software that accepts raw point cloud data from the LiDAR, deskews it, and evalutes it for safety must repeatably perform in real-time. Working with my fellow perception and flight software engineers, I was responsible for ensuring the various parts of this system could talk to eachother, dataflow was smooth and reliable, and the raw LiDAR data could be successfully deskewed to form an accurate representation of the scanned area.

My work on this system has since been proven in [suborbital rocket and helicopter flight tests](https://www.astrobotic.com/astrobotic-tech-passes-critical-tests-for-safe-moon-landings/) of the system. During these tests we were able to scan terrestrial surfaces (including a large outdoor lunar simulation surface) and evaluate them for landing safety. **Results of these tests were published in a paper you can find [here](https://doi.org/10.2514/6.2025-1119).**

I'm super excited to see this tech fly on GM1 - I'll be happy to know I helped ensure the safety of a lunar lander as it touches down on the Moon's surface!

{:refdef: style="text-align: center;"}
![Griffin Mission 1 Patch](/assets/images/lidar-hd/gm1-patch.png){: width="35%"}
{: refdef}
{:refdef: style="text-align: center;"}
_Griffin Mission 1's mission patch._
<br>
Image Credit: Astrobotic
{: refdef}