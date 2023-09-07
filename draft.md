# Variable Message Sign (VMS) SXL

## About
This document outlines what should go into a standardized RSMP SXL for Variable Message Signs.
The document is work-in-progress, and will be expanded and structured as the working group continues discussions.


## Displays
- A VMS can have either a single display, or multiple displays.
- Each display can of type pixels, text or fixed.

All displays have a physical width/heigh.

### Lamp
A type of lamp, or set of lamps, eg:
- warning lamps
- a ring around a speed limit
- a green/red light indicating free parking spaces
  
### Icon display
- has one or more fixed messages/icon
- can either show only one icon (single), or more than one at the same time (multi)
- can be turned on/off
- blinking

### Text display
- shows text characters
- has a width/heigh (in characters). how would width be measured if a variable-width font is used?
- text is UTF-8 encoded, to make it easy to handle all international characters, as well as emoji.
- colors?
- scrolling?
- bold/italic/underlined?

Fixed-width vs. variable-width?

A fixed-width font is the simplest. The display consists of blocks, each with a fixed width. Each block can show a single character. Blocks does not neccessarily have to be pixel-based, but can also use some fixed set of characters shown using e.g. split flaps. UTF-8 would have to be translated if there's a lmited set of possible characters that be be shown. Eg. é, ê and ë could be show as e by the device.

A variable-width text display would essentially be a pixels display, but would use a text-based api for setting the text. Since a variable-width font is used, the number of characters that fit depends on the characters used. The readability can be better that a fixed-width font.

### Pixel display
- has a width and height in pixels
- based on physical size and pixels, it has a pixel resolution
- can be monochrome (1 bit), multichrome (2-8 bit?), or full color rgb (24 bit)
- can be set/read as a single image.

Pixel displays should support common lossless formats like PNG, BMP or GIF.

It would also be good to support vector graphics with SVG.

Compressed formats like JPG could also be used, although you would probably often be better off with a lossless or vector format because displays typically have rather limited resolution.

All pixels display can potentially use the same api - but a depending on the capabilities, the result might be different. Ie. if you try to show colors on a monochrome or multichrome display, the nearest possible color will be used. If you send an image with a size different from the image, it can be resized.

## Display arrangements
Displays can be mounted in various ways (e.g. stacked vertically or horizontally). Displays can also be rotated. The VSM must have a config reflecting (much like you setup multiple screens on a PC).

Multiple displays can potentially be treated as a single larger display. Eg. if you have three stacked text displays, you could interact with them as a single text display with a heigh of 3. Two pixels displays side-by-side can be treated as a single wide pixel display.

## Introspection
It must be possible to read the capabilities of the VMS, including a list of displays and the size, colors, etc of each.

It must be possible to read the curent content of the displays. You should be able to subscribe to the content so you show a live view e.g. in yout supervisor system.

## Alarms and errors
A suiteable set of alarms mus be defined, so you can get notified whenever there are failed pixels/displays, or other types of malfunctions.

Common types of alarms could later be factored out into a generalized SXL module related to system status.

## Blinking
The simplest is to alternative between content and a blank screen at some configurable interval. This could be supported for all types of display.

Making part of the display blink could be done for text displays. Pixel-displays could do it using GIFs.

## Animation
For a pixel display the easiest would probably be to support GIF images, which can contain animation.

Animation could also be supported on text displays, although there are no common format for this (?).

## Live data
Sometimes you want to show live data, e.g. number of cyclists today or a motorist's speed. This requires that you can plug a live data stream into the message. You can either:
- do the rendering on a central system and push it to the VMS whenever there's a change. This is probably the easiers if updates are not that frequent (e.g. minutes, not seconds). A downside is that it doesn't work if the network is down.

- do the rendering on the VMS. This requires some sort of markup or template language (See below about HTML) to define how and where the data is displayed. Local rendering on the VMS is required if you need fast updates. e.g. in response to a cyclist or motorist passing the VMS. A benefit is that it can work withouh network connection.

## Template system
Suppose we want to display live data on a VMS, e.g. "Number of cyclists today: 4323". The number must update dynamically as cyclists pass a sensor.

If HTML is used, this could be handled with Javascript.

In case HTML is not used, we need a way to reference dynamic data that comes from e.g. a detector logic. One idea is to use string interpolation, like it's done in programming languages:

```
Today's date: #{date}
Cyclists today: #{detector_logic(DL001_CAMERA_DAILY_COUNTER).total}
```

Stuff inside #{} is not shown directly, but is instead an expression interpreted using eg. Javascript or LUA. The output of the expression is what will be shown on the display.

We would require certain functions to be present, that allows you to fetch data from dynamic sources, like detector_logic() used above.

In this example above DL001_CAMERA_DAILY_COUNTER would be detector logic consisting of a counter that resets nighty. You would get an object with specific fields, perhaps things like total, current, status, name, etc.

The VMS would be responsible for updating the display whenever the expression changes (ie. the counter changes).

Common things like date(), now() and string operations might be supported.

## Slots
The VMS should be able to store a  number of different slots (eg. 256), which is simply the content shown on all displays. It should be easy to switch which is currently shown. You should also be able to read/delete these slots.

## Display Rules
Different countries (or authorities) might have different rules for what can be display, font size, colors, etc. This could either be enforced by the VMS, or it could be handled by the supervisor system?

## Disconnects
It must be possible to configure what happens if the network is lost. For example, you might want the VMS to return to a default image, or go blank, after 10 minutues without network connection.
