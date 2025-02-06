# Layouts
The location and scaling of all component on a Variable Message Panel together is called an **layout**.

## HTML
HTML and CSS is used to describe layouts. Tailwind can bw used to simplify working with CSS.

For example, a panel with a P-icon with a blue border and a text field below can be represented with this HTML (using Tailwind):
```html
<div class="h-screen flex flex-col items-center justify-center">
    <p id="icon" class="font-extrabold indent-20 leading-85"
       style="font-size: 50vw; border-radius: 20vw; border: solid #07f 8vw; width: 70vw; height: 70vw;">P</p>
    <p id="title" class="font-black" style="font-size: 20vw">OPEN</p>
</div>

```
https://play.tailwindcss.com/RVlvz8Xcx9

HTML `id` attributes are used to link HTML elements with RSMP components, as can be seen above.

## Physical Components
The location of physical elements can be read, but not modified. The layout of physical elements is usually fixed, but can change in case the panel is upgraded or changed.

Devices that include only physical elements, have only a single read-only layout. The HTML returned by the device can be used to render a representation of the sign, e.g. in a supervisor system or simulator.

## Virtual Components
A pixel display show virtual components arranged using a layout, specified using HTML and CSS. THe content is rendered using an HTML library.
Multiple layouts (HTML pages) can be used to switch between differt content.

## Handling Commands
RSMP comamnds can be used to change the content on the panel, e.g. change text or icons.

The component id is used to references the component. For virtual components, the device interact with the relevant HTML element by manipulating content or CSS classes, and the content is then rerendered.

For example, when a device receives an RSMP CommandRequest to change the text of text component with the id `title`, it could change the HTML content of the relevat element using something like:

```js
document.getElementById('title').innerHTML = 'CLOSED';
```
