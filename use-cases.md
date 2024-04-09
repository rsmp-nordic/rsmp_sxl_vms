# Use-cases
This file lists real-world use-cases that we we want our VMS SXL to support. This list is by no means exhaustive, rather it's examples of use-cases that we know we want to support. The display types can be combined to support an wide range of use-cases.

For each use-case we list the displays (components) by type.

European requirements for VMS signs is defined in [EN 12966:2014+A1:2019 - Road vertical signs - Variable message traffic signs](https://standards.iteh.ai/catalog/standards/cen/e1ca2f41-d234-450e-b158-f0104ff1ad82/en-12966-2014a1-2018).

## Highways
### Tunnel warning sign
A combined  sign with warning lights, a large icon and some text. It's placed outside the tunnel and is used when the tunnel is closed.
- 1 icon (warning icon)
- 1 text (warning message, two lines)
- 1 lamp (set of blinking warning lights)

### Motorway control system
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

### Speed limit sign
![speed limit](img/speed_limit_sign.png)
![speed limit 40](img/speed_limit_40.png)

Looks essentially like a tradional static sign, but is variable. A circle or box with a number inside, and some text underneath.
- 1 icon (showing 40/50/60/70)
- 1 lamp (optional, bright border around the sign)
- 1 text (optional, message below icon)

### Warning sign
![warning sign](img/triangular_warning_sign.png)

Triangular warning sign
- Icon
- Optional text

### Animal crossings
Warns when animals are crossing the road. Usually just a warning icon, without any blinking lamps.
- Icon

### Dynamic speed bumps
Bumps that are activated if speed is too high. Includes the bump in the road, but also a VMS.
- Icon

### Ghost driver warning
Warn drivers if they are avbout to drive the wrong way on the highway. No variable content, except 
- Warning lamps
- Lane-lights

### Dynimic information
Can be used to provide info about e.g. traffic, travel times, weather, incidents, etc.
- Text
- Symbol (optional)

## Urban
### Parking space sign
Shows free spaces left at different parking spots. Text is monochrome, but can sometimes change color depending on whether there are free spots, or not:
- 3 texts (showing only integers)

### Text sign
![text sign](img/text_sign.png)

Text information. Can be part of another sign or stand alone.

### Bicycle VMS
![bicycle vms](img/bicycle_vms.png)

One large pixel display, which can shown different things.
- 1 bitmap (messages, icons, etc)

### School Sign
![school sign](img/school_sign.png)

One large pixel display, which usually display a standard "school ahead" sign, but can also show speed limit.
- 1 bitmap (messages, icons, etc)

### Your Speed
![your speed](img/your_speed.png)

A sign that shows your speed when you drive by, and flashes if the speed is too high.
- 1 text (your speed, typically two digits)
- 1 lamp (set of blinking warning lights)


## Public Transport
### Bus stop information
![warning sign](img/bus_stop.png)
- 2 text displays stacked vertically, one with larger text, the other with smaller text
Page 59:
https://www.vejdirektoratet.dk/sites/default/files/2023-07/Projektering%20af%20variable%20vejtavler%20og%20vognbanesignaler%20webtilgængelig.pdf
Some use-cases include hardware that is very limited, and sometimes on battery. In these cases, you might want a very simple interface to just monitor the health of the device, and have all logic in the device using custom logic and custom handling of the display.
Or you could opt for a more generel device that is more flexible, where you use the vms sxl functions to change content.
