
**This is based on xx979xx & Neokii's fork and is tuned for Genesis other HKG cars, but not tested..**

OpenPilot 0.8.4

This fork has Long control if you move scc to bus 1 with harness MSG johnpr#5623 for help with making a harness or to buy one.

Dash cam recording from ui

Long control is radar + vision 

Slow down for curves option

MAD mode for no disengae on brake or gas (Disables Logging)

Auto Lane Change with Blind spot monitoring (No Nudge)

Super Smooth SCC with SCC smoother

SCC sync set speed on gas press.

Run nTune after 30 - 50 miles of driving you should autotune lateral control. use this command cd selfdrive && python ntune.py (make sure your not driving!) 

Make sure to reboot.

Then give it a spin.

https://github.com/xx979xx/openpilot

It is open source and inherits MIT license. It is open source and inherits MIT license.  By installing this software you accept all responsibility for anything that might occur while you use it.  All contributors to this fork are not liable.  <b>Use at your own risk.</b>


------------------------------------------------------


[![](https://i.imgur.com/UelUjKAh.png)](#)

Table of Contents
=======================

* [What is openpilot?](#what-is-openpilot)
* [Integration with Stock Features](#integration-with-stock-features)
* [Supported Hardware](#supported-hardware)
* [Supported Cars](#supported-cars)
* [Community Maintained Cars and Features](#community-maintained-cars-and-features)
* [Installation Instructions](#installation-instructions)
* [Limitations of openpilot ALC and LDW](#limitations-of-openpilot-alc-and-ldw)
* [Limitations of openpilot ACC and FCW](#limitations-of-openpilot-acc-and-fcw)
* [Limitations of openpilot DM](#limitations-of-openpilot-dm)
* [User Data and comma Account](#user-data-and-comma-account)
* [Safety and Testing](#safety-and-testing)
* [Testing on PC](#testing-on-pc)
* [Community and Contributing](#community-and-contributing)
* [Directory Structure](#directory-structure)
* [Licensing](#licensing)

---

What is openpilot?
------

[openpilot](http://github.com/commaai/openpilot) is an open source driver assistance system. Currently, openpilot performs the functions of Adaptive Cruise Control (ACC), Automated Lane Centering (ALC), Forward Collision Warning (FCW) and Lane Departure Warning (LDW) for a growing variety of supported [car makes, models and model years](#supported-cars). In addition, while openpilot is engaged, a camera based Driver Monitoring (DM) feature alerts distracted and asleep drivers.

<table>
  <tr>
    <td><a href="https://www.youtube.com/watch?v=mgAbfr42oI8" title="YouTube" rel="noopener"><img src="https://i.imgur.com/kAtT6Ei.png"></a></td>
    <td><a href="https://www.youtube.com/watch?v=394rJKeh76k" title="YouTube" rel="noopener"><img src="https://i.imgur.com/lTt8cS2.png"></a></td>
    <td><a href="https://www.youtube.com/watch?v=1iNOc3cq8cs" title="YouTube" rel="noopener"><img src="https://i.imgur.com/ANnuSpe.png"></a></td>
    <td><a href="https://www.youtube.com/watch?v=Vr6NgrB-zHw" title="YouTube" rel="noopener"><img src="https://i.imgur.com/Qypanuq.png"></a></td>
  </tr>
  <tr>
    <td><a href="https://www.youtube.com/watch?v=Ug41KIKF0oo" title="YouTube" rel="noopener"><img src="https://i.imgur.com/3caZ7xM.png"></a></td>
    <td><a href="https://www.youtube.com/watch?v=NVR_CdG1FRg" title="YouTube" rel="noopener"><img src="https://i.imgur.com/bAZOwql.png"></a></td>
    <td><a href="https://www.youtube.com/watch?v=tkEvIdzdfUE" title="YouTube" rel="noopener"><img src="https://i.imgur.com/EFINEzG.png"></a></td>
    <td><a href="https://www.youtube.com/watch?v=_P-N1ewNne4" title="YouTube" rel="noopener"><img src="https://i.imgur.com/gAyAq22.png"></a></td>
  </tr>
</table>

Integration with Stock Features
------

In all supported cars:
* Stock Lane Keep Assist (LKA) and stock ALC are replaced by openpilot ALC, which only functions when openpilot is engaged by the user.
* Stock LDW is replaced by openpilot LDW.

Additionally, on specific supported cars (see ACC column in [supported cars](#supported-cars)):
* Stock ACC is replaced by openpilot ACC.
* openpilot FCW operates in addition to stock FCW.

openpilot should preserve all other vehicle's stock features, including, but are not limited to: FCW, Automatic Emergency Braking (AEB), auto high-beam, blind spot warning, and side collision warning.

Supported Hardware
------

At the moment, openpilot supports the [EON DevKit](https://comma.ai/shop/products/eon-dashcam-devkit) and the [comma two](https://comma.ai/shop/products/comma-two-devkit). A [car harness](https://comma.ai/shop/products/car-harness) is recommended to connect the EON or comma two to the car. For experimental purposes, openpilot can also run on an Ubuntu computer with external [webcams](https://github.com/commaai/openpilot/tree/master/tools/webcam).


Community Maintained Cars and Features
------

| Make      | Model (US Market Reference)   | Supported Package | ACC              | No ACC accel below | No ALC below |
| ----------| ------------------------------| ------------------| -----------------| -------------------| -------------|
| Hyundai   | Elantra 2017-19               | SCC + LKAS        | Stock            | 19mph              | 34mph        |
| Hyundai   | Genesis 2015-16               | SCC + LKAS        | Stock            | 19mph              | 37mph        |
| Hyundai   | Kona 2020                     | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Hyundai   | Kona EV 2019                  | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Hyundai   | Santa Fe 2019-20              | All               | Stock            | 0mph               | 0mph         |
| Hyundai   | Sonata 2018-2019              | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Hyundai   | Veloster 2019                 | SCC + LKAS        | Stock            | 5mph               | 0mph         |
| Kia       | Forte 2018-2021               | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Kia       | Niro EV 2020                  | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Kia       | Optima 2017                   | SCC + LKAS        | Stock            | 0mph               | 32mph        |
| Kia       | Optima 2019                   | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Kia       | Seltos 2021                   | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Kia       | Sorento 2018-19               | SCC + LKAS        | Stock            | 0mph               | 0mph         |
| Kia       | Stinger 2018 (Best for this Fork) | SCC + LKAS        | Stock & SCC Harness| 0mph               | 0mph         |
| Kia       | Ceed 2019                     | SCC + LKAS        | Stock            | 0mph               | 0mph         |

<sup>1</sup>Requires an [OBD-II car harness](https://comma.ai/shop/products/comma-car-harness) and [community built ASCM harness](https://github.com/commaai/openpilot/wiki/GM#hardware). ***NOTE: disconnecting the ASCM disables Automatic Emergency Braking (AEB).*** <br />
<sup>2</sup>Only includes the MQB Passat sold outside of North America. The NMS Passat made in Chattanooga TN is not yet supported.

Community Maintained Cars and Features are not verified by comma to meet our [safety model](SAFETY.md). Be extra cautious using them. They are only available after enabling the toggle in `Settings->Developer->Enable Community Features`.

To promote a car from community maintained, it must meet a few requirements. We must own one from the brand, we must sell the harness for it, has full ISO26262 in both panda and openpilot, there must be a path forward for longitudinal control, it must have AEB still enabled, and it must support fingerprinting 2.0

Although they're not upstream, the community has openpilot running on other makes and models. See the 'Community Supported Models' section of each make [on our wiki](https://wiki.comma.ai/).

Installation Instructions
------

Install openpilot on an EON or comma two by entering ``https://openpilot.comma.ai`` during the installer setup.

Follow these [video instructions](https://youtu.be/lcjqxCymins) to properly mount the device on the windshield. Note: openpilot features an automatic pose calibration routine and openpilot performance should not be affected by small pitch and yaw misalignments caused by imprecise device mounting.

Before placing the device on your windshield, check the state and local laws and ordinances where you drive. Some state laws prohibit or restrict the placement of objects on the windshield of a motor vehicle.

You will be able to engage openpilot after reviewing the onboarding screens and finishing the calibration procedure.

Limitations of openpilot ALC and LDW
------

openpilot ALC and openpilot LDW do not automatically drive the vehicle or reduce the amount of attention that must be paid to operate your vehicle. The driver must always keep control of the steering wheel and be ready to correct the openpilot ALC action at all times.

While changing lanes, openpilot is not capable of looking next to you or checking your blind spot. Only nudge the wheel to initiate a lane change after you have confirmed it's safe to do so.

Many factors can impact the performance of openpilot ALC and openpilot LDW, causing them to be unable to function as intended. These include, but are not limited to:

* Poor visibility (heavy rain, snow, fog, etc.) or weather conditions that may interfere with sensor operation.
* The road facing camera is obstructed, covered or damaged by mud, ice, snow, etc.
* Obstruction caused by applying excessive paint or adhesive products (such as wraps, stickers, rubber coating, etc.) onto the vehicle.
* The device is mounted incorrectly.
* When in sharp curves, like on-off ramps, intersections etc...; openpilot is designed to be limited in the amount of steering torque it can produce.
* In the presence of restricted lanes or construction zones.
* When driving on highly banked roads or in presence of strong cross-wind.
* Extremely hot or cold temperatures.
* Bright light (due to oncoming headlights, direct sunlight, etc.).
* Driving on hills, narrow, or winding roads.

The list above does not represent an exhaustive list of situations that may interfere with proper operation of openpilot components. It is the driver's responsibility to be in control of the vehicle at all times.

Limitations of openpilot ACC and FCW
------

openpilot ACC and openpilot FCW are not systems that allow careless or inattentive driving. It is still necessary for the driver to pay close attention to the vehicle’s surroundings and to be ready to re-take control of the gas and the brake at all times.

Many factors can impact the performance of openpilot ACC and openpilot FCW, causing them to be unable to function as intended. These include, but are not limited to:

* Poor visibility (heavy rain, snow, fog, etc.) or weather conditions that may interfere with sensor operation.
* The road facing camera or radar are obstructed, covered, or damaged by mud, ice, snow, etc.
* Obstruction caused by applying excessive paint or adhesive products (such as wraps, stickers, rubber coating, etc.) onto the vehicle.
* The device is mounted incorrectly.
* Approaching a toll booth, a bridge or a large metal plate.
* When driving on roads with pedestrians, cyclists, etc...
* In presence of traffic signs or stop lights, which are not detected by openpilot at this time.
* When the posted speed limit is below the user selected set speed. openpilot does not detect speed limits at this time.
* In presence of vehicles in the same lane that are not moving.
* When abrupt braking maneuvers are required. openpilot is designed to be limited in the amount of deceleration and acceleration that it can produce.
* When surrounding vehicles perform close cut-ins from neighbor lanes.
* Driving on hills, narrow, or winding roads.
* Extremely hot or cold temperatures.
* Bright light (due to oncoming headlights, direct sunlight, etc.).
* Interference from other equipment that generates radar waves.

The list above does not represent an exhaustive list of situations that may interfere with proper operation of openpilot components. It is the driver's responsibility to be in control of the vehicle at all times.

Limitations of openpilot DM
------

openpilot DM should not be considered an exact measurement of the alertness of the driver.

Many factors can impact the performance of openpilot DM, causing it to be unable to function as intended. These include, but are not limited to:

* Low light conditions, such as driving at night or in dark tunnels.
* Bright light (due to oncoming headlights, direct sunlight, etc.).
* The driver's face is partially or completely outside field of view of the driver facing camera.
* The driver facing camera is obstructed, covered, or damaged.

The list above does not represent an exhaustive list of situations that may interfere with proper operation of openpilot components. A driver should not rely on openpilot DM to assess their level of attention.

User Data and comma Account
------

By default, openpilot uploads the driving data to our servers. You can also access your data by pairing with the comma connect app ([iOS](https://apps.apple.com/us/app/comma-connect/id1456551889), [Android](https://play.google.com/store/apps/details?id=ai.comma.connect&hl=en_US)). We use your data to train better models and improve openpilot for everyone.

openpilot is open source software: the user is free to disable data collection if they wish to do so.

openpilot logs the road facing camera, CAN, GPS, IMU, magnetometer, thermal sensors, crashes, and operating system logs.
The driver facing camera is only logged if you explicitly opt-in in settings. The microphone is not recorded.

By using openpilot, you agree to [our Privacy Policy](https://my.comma.ai/privacy). You understand that use of this software or its related services will generate certain types of user data, which may be logged and stored at the sole discretion of comma. By accepting this agreement, you grant an irrevocable, perpetual, worldwide right to comma for the use of this data.

Safety and Testing
----

* openpilot observes ISO26262 guidelines, see [SAFETY.md](SAFETY.md) for more details.
* openpilot has software in the loop [tests](.github/workflows/test.yaml) that run on every commit.
* The safety model code lives in panda and is written in C, see [code rigor](https://github.com/commaai/panda#code-rigor) for more details.
* panda has software in the loop [safety tests](https://github.com/commaai/panda/tree/master/tests/safety).
* Internally, we have a hardware in the loop Jenkins test suite that builds and unit tests the various processes.
* panda has additional hardware in the loop [tests](https://github.com/commaai/panda/blob/master/Jenkinsfile).
* We run the latest openpilot in a testing closet containing 10 EONs continuously replaying routes.

Testing on PC
------
For simplified development and experimentation, openpilot can be run in the CARLA driving simulator, which allows you to develop openpilot without a car. The whole setup should only take a few minutes.

Steps:
1) Start the CARLA server on first terminal
```
bash -c "$(curl https://raw.githubusercontent.com/commaai/openpilot/master/tools/sim/start_carla.sh)"
```
2) Start openpilot on second terminal
```
bash -c "$(curl https://raw.githubusercontent.com/commaai/openpilot/master/tools/sim/start_openpilot_docker.sh)"
```
3) Press 1 to engage openpilot

See the full [README](tools/sim/README.md)

You should also take a look at the tools directory in master: lots of tools you can use to replay driving data, test, and develop openpilot from your PC.


Community and Contributing
------

openpilot is developed by [comma](https://comma.ai/) and by users like you. We welcome both pull requests and issues on [GitHub](http://github.com/commaai/openpilot). Bug fixes and new car ports are encouraged.

You can add support for your car by following guides we have written for [Brand](https://medium.com/@comma_ai/how-to-write-a-car-port-for-openpilot-7ce0785eda84) and [Model](https://medium.com/@comma_ai/openpilot-port-guide-for-toyota-models-e5467f4b5fe6) ports. Generally, a car with adaptive cruise control and lane keep assist is a good candidate. [Join our Discord](https://discord.comma.ai) to discuss car ports: most car makes have a dedicated channel.

Want to get paid to work on openpilot? [comma is hiring](https://comma.ai/jobs/).

And [follow us on Twitter](https://twitter.com/comma_ai).

Directory Structure
------
    .
    ├── cereal              # The messaging spec and libs used for all logs
    ├── common              # Library like functionality we've developed here
    ├── installer/updater   # Manages auto-updates of NEOS
    ├── opendbc             # Files showing how to interpret data from cars
    ├── panda               # Code used to communicate on CAN
    ├── phonelibs           # Libraries used on NEOS devices
    ├── pyextra             # Libraries used on NEOS devices
    └── selfdrive           # Code needed to drive the car
        ├── assets          # Fonts, images and sounds for UI
        ├── athena          # Allows communication with the app
        ├── boardd          # Daemon to talk to the board
        ├── camerad         # Driver to capture images from the camera sensors
        ├── car             # Car specific code to read states and control actuators
        ├── common          # Shared C/C++ code for the daemons
        ├── controls        # Perception, planning and controls
        ├── debug           # Tools to help you debug and do car ports
        ├── locationd       # Soon to be home of precise location
        ├── logcatd         # Android logcat as a service
        ├── loggerd         # Logger and uploader of car data
        ├── modeld          # Driving and monitoring model runners
        ├── proclogd        # Logs information from proc
        ├── sensord         # IMU / GPS interface code
        ├── test            # Unit tests, system tests and a car simulator
        └── ui              # The UI

Licensing
------

openpilot is released under the MIT license. Some parts of the software are released under other licenses as specified.

Any user of this software shall indemnify and hold harmless comma.ai, Inc. and its directors, officers, employees, agents, stockholders, affiliates, subcontractors and customers from and against all allegations, claims, actions, suits, demands, damages, liabilities, obligations, losses, settlements, judgments, costs and expenses (including without limitation attorneys’ fees and costs) which arise out of, relate to or result from any use of this software by user.

**THIS IS ALPHA QUALITY SOFTWARE FOR RESEARCH PURPOSES ONLY. THIS IS NOT A PRODUCT.
YOU ARE RESPONSIBLE FOR COMPLYING WITH LOCAL LAWS AND REGULATIONS.
NO WARRANTY EXPRESSED OR IMPLIED.**

---

<img src="https://d1qb2nb5cznatu.cloudfront.net/startups/i/1061157-bc7e9bf3b246ece7322e6ffe653f6af8-medium_jpg.jpg?buster=1458363130" width="75"></img> <img src="https://cdn-images-1.medium.com/max/1600/1*C87EjxGeMPrkTuVRVWVg4w.png" width="225"></img>

[![openpilot tests](https://github.com/commaai/openpilot/workflows/openpilot%20tests/badge.svg?event=push)](https://github.com/commaai/openpilot/actions)
[![Total alerts](https://img.shields.io/lgtm/alerts/g/commaai/openpilot.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/commaai/openpilot/alerts/)
[![Language grade: Python](https://img.shields.io/lgtm/grade/python/g/commaai/openpilot.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/commaai/openpilot/context:python)
[![Language grade: C/C++](https://img.shields.io/lgtm/grade/cpp/g/commaai/openpilot.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/commaai/openpilot/context:cpp)
[![codecov](https://codecov.io/gh/commaai/openpilot/branch/master/graph/badge.svg)](https://codecov.io/gh/commaai/openpilot)
