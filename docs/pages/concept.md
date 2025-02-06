---
title: Concept
permalink: /concept/
nav_order: 3
---

# Concept
There's a wide range of uses-cases and types of variable message signs. To handle this, the concept behind the SXL is to define a set of **component types** that represent basic visual building blocks like text, icons and images. 

Components can be used alone or combined to represent a complete VMS __panel__. For example, a panel might have just an icon, or an icon at the top with a text areas below.

Each component type has a set of statuses, commands and alarms used to interact with it. For example, you can change/read the text in a text component, or change/read the icon showed by an icon component.

## Component Types
These component types are defined:
- Lamp
- Icon
- Text
- Image
- HTML

## Physical vs. Virtual components
Dedicated hardware is sometimes used for displaying a specific  type of visual element, e.g. a fixed icon shown used LEDs that can just be turned on/off, warning lamps, or a dedicated text panel that can show only text.

A pixel display is itself a physical element, and can can render **virtual components** of other types. For example, you might show an icon and a text area on a pixel display.

You use the same components types and messages to interact with your content, regardless of whether that are shown using dedicated hardware, or rendered on a pixel display.

Note that it's possible to show arbitrary images on a pixel display, by using the image component type. This can be used if you want to do you own custom rendering of content and just send the resulting image to the display.

## Layouts
The location of physical elements are fixed. Their locations can be read, but not modified. However, if the physical design of the panel is changed, the layout will change.

Virtual components rendered on a pixel display can be arranged anywhere on the display.

The arrangement of components is called a [layout](layouts.md), and is specified using HTML and CSS. Tailwind is used to simplify working with CSS.

an have multiple layouts and typically uses an HTML library to render content on the display.

## HTML and Dynamic Content
You can use HTML components to render dynamic content.

Javascript can be used to fetch data from APIs, dynamically update content, etc.

The HTML source can either be send directly, or fetched via an URL.


