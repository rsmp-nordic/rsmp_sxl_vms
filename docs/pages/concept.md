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

## Hardware and Components
A panel consist of hardware elements, e.g. pixel displays, dedicated LED text displays, warning lamps, etc.

Most dedicated hardware can only show one type of content and is therefore linked to one particular component type, e.g. a lamp component.

However, a pixel display can be used as any compponent type, including an HTML component.

Using a pixel didsplay as a simple compoent type, e.g. a text or image compoent, gives you a simple interface to interact with the content, but limits you to that kind of content. This can be useful if you know you only want to display text, or you want to render images server side and show them on the display.

Using a pixel display as an HTML component allows you to show complex and/or interactive content. You can use any HTML, CSS or Javascript, fetch live data from API's etc.

You can mark elements in an HTML layout as text, image, icon or lamp components. This will allow you to interact with these elements using the regular component interfaces. For example you can use HTML to layout an icon with a text area below, and mark the text areas as a text component. You can then use the RSMP text component interface to easily change the text, read it, etc.

Regardless of whether a components is being displayed using dedicated hardware, or rendered on a pixel display using HTML, you interact with using the same component interface.

If you would rather render content on a server as an image and display that on a pixel display, you can use the pixel display as a image component. You can then use the convenient image component interface to upload and change images.

## Layouts
The location of physical elements are fixed. Their locations can be read, but not modified. However, if the physical design of the panel is changed, the layout will change.

Components rendered on a pixel display can be arranged anywhere on the display.

The arrangement of components is called a [layout](layouts.md), and is specified using HTML and CSS. CSS systems like Tailwind can be used to simplify working with CSS.

You can define multiple layouts and switch between them. You can also read layouts and use then for rendering a realistic representation of the content, e.g. in a supervisors system.
