# VMS messages
Messages for VMS, including commands, statues and alarms.

## System
- SetDisconnectTimeout: define what to show when network connection is lost, and how soon.

## Arrangement
- GetDisplays: get info on all displays (arrangement, size, resolution, colors, type, functionality, etc.)
- GetArrangement: get relative positions of displays, in cm
- SetArrangement: change relative positions of displays, in cm

## All display types
- GetFeatures: get info about what features are available
- SetVisible: turn display on/off
- SetBrightness: set brightness
- SetBlink: set on/off tiems, eg. 1s on, 0.5s off, or disable blinking

## Lamp
- SetColor: set color
- SetBlinking: set blinking pattern

## Icon Display
- SelectIcon: choose which icon to show, using key (eg. 'warning')
- GetIcons: get a list of icons that can be shown, by keys (eg. 'warning', 'ok', 'stop')

## Text Display
- SetText: set text
- SetMarkdown: set markdown, use tags for bold, italics, etc.
- SetMode: if there is more text than can be shown, should we truncate, scroll or paginate, étc?

## Pixel display
- SetBitmap: upload lossless image as PNG, BMP or GIF
- SetHTML: show HTML (raw HTML with inline CSS) 
- SetURL: show a web page, referenced by a URL. network from vsm to url is required
- GetPixelErrors: Get total, percentage and list of failed pixels
- GetBitmap: download previsouly uploaded bitmap
- GetSnapshot: download currently displayed content as PNG
- GetStreamingLink: get link to rtsp stream that showns the live content of display.

## Alarms
- Temperature: temperature is too high
- Humidity: humnidity is too high
Door open: door is open
Legibility: display is hard to read, due to failed pixel or characteres failing


