---
title: Component Types
permalink: /component-types/
nav_order: 5
---

# Component Types

## Lamp
One or more lamps controlled together as a single entity, e.g.:

- a set of warning lamp
- a frame around text or icon
- a green/red indicator on a parking space
  
### Interface
- turn on/off

## Icon
An icon area that can show an icon. Optinally you can switch between different icons, e.g.:

- roadworks
- animals on the road
- speed limit

### Interface
- turn on/off
- select icon
- set blinking

## Text display
Used for showing one or more lines of text.

It has a width and height measured in characters.
Text is UTF-8 encoded, to make it easy to handle international characters, as well as emoji.

A fixed-width text display is the simplest. The display consists of blocks, each with a fixed width. Each block can show a single character. A fixed numbers of characters fit per line.
Only fixed-width fonts can be shown.

A variable-width text display is not divided into horizonal blocks and is essential ly a type of pixel display. Different characters take up different amount of horizonal space.
The number of characters that fit on what characters are shown, the font and the font-size. The readability can be better that a fixed-width font.
Fixed-width font can be shown on a variable-width display.

### Interfact
- set text
- set font
- set horizonal and vertical alignment
- read fixed/variable type
- read dimensions in characters and pixels
- set paging/scrolling


## Image display
Used for display arbitrary images. Can only be shown on a pixel display.
It has a dimension is cm and in pixels, and a corresponding pixel resultion in ppcm (pixels per cm).
It can be monochrome (1 bit), multichrome (2 or more bits), or full color rgb (24 bit)

Images can be set using common lossless formats like PNG, BMP or GIF, compressed formats like JPG or vector formats like SVG.

Compressed formats are useful if you use an VMS more like an info/ad screen and show a large photo/artwwork/ad.

Images will be converted/rescaled to match the hardware capabiltiy resultion and number of colors.

### Interface
- read dimensionsin pixels and cm
- read bit depth
- set image


## HTML display
Used for displaying content with advanced layout or dynamic content. Javascrip can be used to handle dynamic aspeects, e.g. fetch data from APIs and update content.

HTML is a flexible solutions for complex or dynamic content, or when you want control over layout.
An HTML display would typically run a browswer in full-screen kiosk mode with no user input.

RSMP is used to control what page is loaded, and whether the display is on or off.

There is no user input.

The HTML source be be send directly, or fetched from an URL.

### Interface
- turn on/off
- set HTML source/URL
- reload
- set scaling
- read web console
