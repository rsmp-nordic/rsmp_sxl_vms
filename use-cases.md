# Use-cases
This file lists real-world use-cases that we we want our VMS SXL to support.
For each use-case we list the displays (components) by type.

European requirements for VMS signs is defined with:
- EN 12966:2014+A1:2019 - Road vertical signs - Variable message traffic signs

## Tunnel warning sign
A combined sign with warning lights, a large icon and some text
- 1 icon (warning icon)
- 1 text (warning message, two lines)
- 1 lamp (set of blinking warning lights)

## Parking space sign
Shows free spaces left at a few different parking spots. Text is monochrome
- 3 texts (showing ony integers)

## Speed limit sign

![speed limit](img/speed_limit_sign.png)

Looks essentially a tradional static sign, but is variable. A circle with a number inside, and some text underneath.
- 1 icon (showing 50/60/70)
- 1 text (optional)
- 1 lamp (ring around the sign)

## Warning sign

![warning sign](img/triangular_warning_sign.png)

Triangular warning sign
- Icon
- Optional text

## Text sign

![text sign](img/text_sign.png)

Text information. Can be part of another sign or stand alone.

## Bicycle VMS
One large pixel display, which can shown different things.
- 1 bitmap (messages, icons, etc)
