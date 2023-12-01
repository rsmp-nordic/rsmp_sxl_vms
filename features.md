# Variable Message Sign (VMS) SXL

## About
This document outlines what should go into a standardized RSMP SXL for Variable Message Signs.
The document is work-in-progress, and will be expanded and structured as the working group continues discussions.

The SXL aims to support most VMS types commonly used by road authorities, including speed limits signs, bicycle barometers, motorway control systems, bus stops, etc.

## Displays (components)
- A VMS can have either a single display, or multiple displays.
- Each component is an RSMP component.
- Each display can of type lamp, text, image or html.

All displays have a physical width/heigh.

### Lamp
A type of lamp, or set of lamps, eg:
- warning lamps
- a ring around a speed limit
- a frame around a text or icon
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
- inverse (white on black, vs. black on white)
- colors?
- scrolling?
- bold/italic/underlined?

Fixed-width vs. variable-width?

A fixed-width font is the simplest. The display consists of blocks, each with a fixed width. Each block can show a single character. Blocks does not neccessarily have to be pixel-based, but can also use some fixed set of characters shown using e.g. split flaps. UTF-8 would have to be translated if there's a lmited set of possible characters that be be shown. Eg. é, ê and ë could be show as e by the device.

A variable-width text display would essentially be a pixels display, but would use a text-based api for setting the text. Since a variable-width font is used, the number of characters that fit depends on the characters used. The readability can be better that a fixed-width font.

## Image display
- has a width and height in pixels
- based on physical size and pixels, it has a pixel resolution in ppcm (pixels per cm)
- can be monochrome (1 bit), multichrome (2-8 bit?), or full color rgb (24 bit)
- can be set/read as a single image.

Image displays should support common lossless formats like PNG, BMP or GIF.

It would also be good to support vector graphics with SVG. (This would be an argument to use the name image display, rather than bitmap display.)

Compressed formats like JPG could also be used, and might be useful if you use an VMS more like an info/ad screen and show a large photo/artwwork/ad. But usually we would probably  be better off with a lossless or vector format because displays typically have rather limited resolution.

All image displays can potentially use the same api - but a depending on the capabilities, the result might be different. Ie. if you show a color image on a monochrome or multichrome display, the nearest possible color might be used. If you send an image with a size different from the image, it can be resized.

## Display arrangements
Displays can be mounted in various ways (e.g. stacked vertically or horizontally). Displays can also be rotated. The VSM must have a config reflecting (much like you setup multiple screens on a PC).

Multiple displays can potentially be treated as a single larger display. Eg. if you have three stacked text displays, you could interact with them as a single text display with a height of 3. Two pixels displays side-by-side can be treated as a single wide image display. But this could perhaps be handled by device, so it just presents a single display (component).

## Blinking
The simplest is to alternative between content and a blank screen at some configurable interval. This could be supported for all types of display.

Making part of the display blink could be done for text displays. Pixel-displays could do it using GIFs.

## Animation
Animation could also be supported on text displays, although there are no common format for this (?).
Animation of image display could potentially be done by allowing GIFs (but is this desired?)
HTML displays would be well suited for animation, as they can show any image or vidoe format, or animate content using Javascript.

## Live data
Sometimes you want to show live data, e.g. number of cyclists today or a motorist's speed. This requires that you can plug a live data stream into the message. You can either:
- do the rendering on a central system and push it to the VMS whenever there's a change. This is probably the easiers if updates are not that frequent (e.g. minutes, not seconds). A downside is that it doesn't work if the network is down.

- do the rendering on the VMS. This requires some sort of markup or template language (See below about HTML) to define how and where the data is displayed. Local rendering on the VMS is required if you need fast updates. e.g. in response to a cyclist or motorist passing the VMS. A benefit is that it can work withouh network connection.

We should support both models.

## Templates
Suppose we want to display live data on a VMS, e.g. "Number of cyclists today: 4323". The number must update dynamically as cyclists pass a sensor.
If HTML is used, this could be handled with Javascript. If not, we need some kind of template language to define where dynamic data goes.

## Slots
The VMS should be able to store a  number of different slots, which is simply the content shown on all displays. It should be easy to switch which is currently shown. You should also be able to read/delete these slots.

## Introspection
It must be possible to read the capabilities of the VMS, including a list of displays and the size, colors, etc of each.

It must be possible to read the curent content of the displays. You should be able to subscribe to the content so you show a live view e.g. in yout supervisor system.

## Alarms and errors
A suiteable set of alarms must be defined, so you can get notified whenever there are failed pixels/displays, or other types of malfunctions.

Common types of alarms could later be factored out into a generalized SXL module related to system status.

## Disconnects
It must be possible to configure what happens if the network is lost. For example, you might want the VMS to return to a default image, or go blank, after 10 minutues without network connection.
