---
title: Highways
permalink: /use-cases/highways/
parent: Use-cases
nav_order: 2
---

# Highways
## Tunnel warning sign
A combined  sign with warning lights, a large icon and some text. It's placed outside the tunnel and is used when the tunnel is closed.
- 1 icon (warning icon)
- 1 text (warning message, two lines)
- 1 lamp (set of blinking warning lights)

## Motorway control system
Typically above the lanes of the motorway.
For each lane a few things can be shown:
- speed limit (number inside a ring)
- lane closure (cross)
- directions to switch lane (arrow)

Some of these icons include yellow flashers in the corners. Either as part of the display or as separate lamps.
The flasher are control by logic in the VMS, e.g. if the speed limit is reduced, then the flashers are activated.
This would normally be enforced by the VMS, but it should be possible to override this. It should also be possible to read the status of the flashers and the displays.

If the logic and enforcement of rules is done in the central system, it's very important that you can change every display simultanously, and that nothing is changed if some display would not be able to shown what you request, since that might result in an invalid status of displays.

This type of use-case could be handled by having an icon display and a lamp (set of flashers) per lane.

## Speed limit sign
![speed limit](/assets/images/speed_limit_sign.png)
![speed limit 40](/assets/images/speed_limit_40.png)

Looks essentially like a tradional static sign, but is variable. A circle or box with a number inside, and some text underneath.
- 1 icon (showing 40/50/60/70)
- 1 lamp (optional, bright border around the sign)
- 1 text (optional, message below icon)

## Warning sign
![warning sign](/assets/images/triangular_warning_sign.png)

Triangular warning sign
- Icon
- Optional text

## Animal crossings
Warns when animals are crossing the road. Usually just a warning icon, without any blinking lamps.
- Icon

## Dynamic speed bumps
Bumps that are activated if speed is too high. Includes the bump in the road, but also a VMS.
- Icon

## Ghost driver warning
Warn drivers if they are avbout to drive the wrong way on the highway. No variable content, except 
- Warning lamps
- Lane-lights

## Dynamic information
Can be used to provide info about e.g. traffic, travel times, weather, incidents, etc.
- Text
- Symbol (optional)
