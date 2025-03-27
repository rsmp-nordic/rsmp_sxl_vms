---
title: Messages
permalink: /messages/
nav_order: 6
---

# Messages
[preliminary]

Messages for VMS, including commands, statues and alarms.

## System
- SetDisconnectTimeout: define what to show (show specific content, or turn off) when network connection is lost, and how soon. is this relevant for all vms types?

Are these needed? Or is this just defined once for all in the hardware?
- SetTemperatureThreshold: set temperature alarm threshold (low, high)
- SetHumidityThreshold: set humidity alarm threshold
- SetDoorThreshold: set duration alarm threshold

## Sensors
- Temperature: temperature status
- Temperature: humidity status
- Door: door status
- PixelErrors: pixel error status

## Alarms
- Temperature: temperature is too high
- Humidity: humidity is too high
- Door open: door is open
- Legibility: display is hard to read, due to failed pixel or characteres failing

## Arrangement
- GetDisplays: get info on all displays (arrangement, size, resolution, colors, type, functionality, etc.)
- GetArrangement: get relative positions of displays, in cm
- SetArrangement: change relative positions of displays, in cm

## All display types
- GetFeatures: get info about what features are available
- SetVisible: turn display on/off
- SetBrightness: set brightness
- SetBlink: set on/off tiems, eg. 1s on, 0.5s off, or disable blinking
- SetMinInterval: The minimum time between changes, e.g. off, 1s, 20s or 1m. 

## Lamp
- Activate: turn on/off
- Color: set color
- Blinking: set blinking pattern

## Icon
- Select: choose which icon to show, using key (eg. 'warning')
- List: get a list of icons that can be shown, by keys (eg. 'warning', 'ok', 'stop')
- Upload/Rename/Delete: manage icons on device

## Text
- Text: set text

## Image
- Select
- Upload/Rename/Delete

## HTML
- HTML: set HTML either as code or from link
- Snapshot: download currently displayed content as PNG
- Reload: reload the HTML display
- Console: get the web console of the HTML engine, e.g. to check errors
- Zoom: control zoom level of HTML renderer

## Pixel Display
- Dimensions: get physical size and pixels
- PixelErrors: Get total, percentage and list of failed pixels
