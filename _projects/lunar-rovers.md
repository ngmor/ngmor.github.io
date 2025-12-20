---
layout: project
title:  Lunar Rover Robotics
description: Architecture, Perception, Localization
image: assets/images/lunar-rovers/main.jpg
imagewidth: 70%
order: 984
---

{:refdef: style="text-align: center;"}
_The LunaGrid-Lite (LGL) engineering model (EM) CubeRover deploying cable across Astrobotic's MoonYard test lab._
<br>
Image Credit: Astrobotic
{: refdef}

Astrobotic's **CubeRover** platform is a modular lunar rover designed to carry payloads of different sizes and form factors across the surface of the Moon. During my time at Astrobotic, I have been heavily involved in maturing CubeRover's software. Working with a cross-disciplinary robotics team, I have helped define the rover's flight software architecture and design philosophy, implemented critical parts of its core functionality, and applied perception technologies to the data received from the system's sensors.

{:refdef: style="text-align: center;"}
![CubeRover Mission 1 (CM1) Mission Patch](/assets/images/lunar-rovers/cm1-patch.jpeg){: width="48%"}
![CubeRover Mission 1 (CM1) Flight Model Rover](/assets/images/lunar-rovers/cm1-fm.jpg){: width="40%"}
{: refdef}
{:refdef: style="text-align: center;"}
_The CubeRover Mission 1 (CM1) mission patch and flight model (FM), which will fly to the Moon aboard Astrobotic's Griffin Mission 1._
<br>
Image Credit: Astrobotic
{: refdef}

CubeRover's maiden voyage will be [**CubeRover Mission 1 (CM1)**](TODO/CubeRoverFlightReady) aboard Astrobotic's Griffin Mission 1 (GM1). The rover will be deployed to the lunar surface, where it will demonstrate several technologies key to the future development of the CubeRover line. This includes driving into shadowed regions to better understand the lunar thermal environment, performing mobility tests to understand lunar surface traversability for lightweight rovers, and testing a software-defined radio (SDR) which could be used to allow rovers that can survive the lunar night (where their lander counterparts might cease to operate) to communicate with orbital assets.

In order to prepare CubeRover for the CM1 mission, I worked with software engineers at Astrobotic to define the architecture and design philosophy around CubeRover's flight software. Our philosophy allows for modular software re-use and shared development across missions. This in turn results in lower development costs for future projects, reliable software tested thoroughly across multiple efforts, and reduction of technical debt in our codebase. Using this architecture and design philosophy, we've implemented the various functionalities required for a lunar rover, from capturing images using onboard cameras, to traversing the lunar surface, to phoning home with telemetry and collected data - and much more.

Some of my specific contributions include work on the imaging and mobility subsystems. I wrote the camera interface software for the rover, which handles capturing imagery and applying perception algorithms to ensure captured images are high quality. The harsh lighting conditions of the Moon, especially at the polar regions, can make capturing good imagery difficult. And we don't want to be downlinking bad images; the bandwidth-constrained nature of operating a rover on the Moon makes every bit we downlink count. Thus it is important our onboard systems are capable of automatically capturing high quality imagery for both operators and downstream data processing. I also heavily contributed to the motor and kinematic control systems of the rover. These systems make for an intuitive operator interface to control the rover's motion and ensure safety of the rover in the event of unexpected communications interruptions or other issues during driving.

{:refdef: style="text-align: center;"}
![CubeRover Mission 1 (CM1) EM Rover](/assets/images/lunar-rovers/cm1-em.jpg){: width="60%"}
{: refdef}
{:refdef: style="text-align: center;"}
_Yours truly working with the CM1 EM rover._
<br>
Image Credit: Astrobotic
{: refdef}

CubeRover's next flight mission will be as a part of [**LunaGrid-Lite (LGL)**](TODO/LGLCDR), a demonstration mission which will serve as a precursor to the deployment of LunaGrid, Astrobotic's solar power grid for the surface of the Moon. LGL will deploy 500 m of cable across the surface of the Moon via a CubeRover. 1 kW of power will then be transmitted through the cable, and the performance of the power transmission system will be studied in the lunar environment.

{:refdef: style="text-align: center;"}
![LunaGrid-Lite (LGL) EM Rover in the MoonYard](/assets/images/lunar-rovers/lgl-em.jpg){: width="50%"}
{: refdef}
{:refdef: style="text-align: center;"}
Image Credit: Astrobotic
{: refdef}

For the LGL mission, knowledge of the rover's location relative to the lander from which it will be deployed is important. Without this knowledge, it would be difficult to successfully complete the mission objectives, as the rover could stray from its intended trajectory and find itself in terrain it cannot traverse without a feasible method of recovery.

Thus on top of continuing CubeRover flight software development for LGL, I also developed a ground-based localization system for the rover which fuses data from onboard sensors (reported down via telemetry) into an estimate of the rover's trajectory. This system optimizes across the entire trajectory of the rover, ensuring even previous poses of the rover can be known with increasing accuracy as more data from the rover is collected. With simulations using expected sensor uncertainty parameters, this localization system has performed exceedingly well.

The team at Astrobotic continues to work on improving the functionality and autonomous capabilities of CubeRover. I look forward to seeing CM1 fly!
