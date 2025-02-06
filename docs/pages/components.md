---
title: Components
permalink: /components/
nav_order: 5
---

# Components
The following compoent types are defined.

## Lamp
One or more lamps controlled together as a single entity, e.g.:

- a set of warning lamp
- a frame around text or icon
- a green/red indicator on a parking space
  
### Interface
- turn on/off

## Icon
An icon. Optionally you can switch between different icons.

### Interface
- turn on/off
- select icon
- set blinking

## Text display
Used for showing one or more lines of text. Text is UTF-8 encoded.

A fixed-width text display is the simplest. The display consists of blocks, each with a fixed width. Each block can show a single character. A fixed numbers of characters fit per line.
Only fixed-width fonts can be shown.

A variable-width text display is not divided into horizonal blocks and is essentially a type of pixel display. Different characters take up different amount of horizonal space. The number of characters that fit on what characters are shown, depends font and the font-size.

### Interface
- set text
- set font
- set horizonal and vertical alignment
- read fixed/variable type
- read dimensions in characters and pixels
- set paging/scrolling

## Image
Used to display arbitrary images. Can only be shown on a pixel display.
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
Used for displaying dynamic content using JavaScript, e.g. by fetching data from APIs and updating content. However, there is no user input.

RSMP is used to control what HTML is shown, and whether the display is on or off.
The HTML source be be send directly, or fetched from an URL.

### Interface
- turn on/off
- set HTML source/URL
- reload
- set scaling
- read web console
