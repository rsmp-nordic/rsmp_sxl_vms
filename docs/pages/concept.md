---
title: Concept
permalink: /concept/
nav_order: 3
---

# Concept
There's a wide range of uses-cases and types of variable message signs. To handle this, the concept behind the SXL is to define a set of **component types** that represent basic visual building blocks like text, icons and images. 

Components can be used alone or combined to represent a complete VMS __panel__. For example, a panel might have just an icon, or an icon at the top with a text areas below.

Each component type has a convenient set of statuses, commands and alarms (i.e. an API) used to interact with the content. For example, you can change/read the text in a text component, or change/red the icon showed by an icon component

## Component Types
These component types are defined:
- Lamp
- Icon
- Text
- Image
- HTML

## Physical vs. Virtual components
Dedicated hardware is sometimes used for displaying a specific  type of visual element, e.g. a fixed icon shown used LEDs that can just be turned on/off, a warning lamp, or a text panel that can show text, but not icons.

A pixel display is itself a physical elemeent, but can can render **virtual components** of other types. For example, you might show an icon and a text area on a pixel display.

You use the same components types and message APIs to interact with you content, regardless of whether that are shown using dedicated hardware, or rendered on a pixel display.

The device will maintain a logical representation so you can interact with the content, e.g. read the current values. This is similar to HTML which defines content which is then rendered by the browser. You can Javascript to interact with the content, e.g. to read/write a text area. In fact, some signs might choose to use HTML as a way to render content on pixel displays, although this is up to the manufacturer. 

Note that it's possible to show arbitrary images on a pixel display, by using the image component type. This cna be used if you want to do you own custom rendering of content and just send the resulting image to the display.

## Layouts
The location of physical elements are fixed. Their locations can be read, but not modified.

Virtual components rendered on a pixel display can moved around without the the pixel display, using a simple layout language.

The location and scaling of all component together is called an **layout**. A device that includes one or more pixel displays can have multiple layouts that you can switch between.

## HTML and Dynamic Content
You can use HTML components to render advanced content, including dynamic content.

Javascript can be used to fetch data from APIs, dynamically update content, etc.

The HTML source can either be send directly, or fetched via an URL.


