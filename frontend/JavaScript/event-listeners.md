
# JavaScript - Event Listeners

Allows the system to respond to various user interactions and events that occur in the browser, such as clicking a button, resizing the window, or typing in an input field.

## Types of Event Listeners
1. [Mouse Events](#1-mouse-events)
2. [Keyboard Events](#2-keyboard-events)
3. [Form Events](#3-form-events)
4. [Window Events](#4-window-events)
5. [Clipboard Events](#5-clipboard-events)
6. [Drag and Drop Events](#6-drag-and-drop-events)
7. [Media Events](#7-media-events)
8. [Touch Events](#8-touch-events-for-mobile-devices)

### 1. Mouse Events
- These are triggered by mouse actions

| Event | Description | Example |
|:-----:|:-----------:|:-------:|
| `click` | Triggered when a user clicks on an element | Button clicks, links, etc.
| `dblclick` | Triggered on a double-click | Double-click actions
| `mousedown` | Triggered when the mouse button is pressed down | Detect mouse press
| `mouseup` | Triggered when the mouse button is released | Detect mouse release
| `mousemove` | Triggered when the mouse moves over an element | Dragging or tracking the mouse position
| `mouseover` | Triggered when the mouse enters an element | Highlighting or hover effects
| `mouseout` | Triggered when the mouse leaves an element | Removing hover effects
| `contextmenu` | Triggered when the user right-clicks to open the context menu | Custom context menus

#### Example
```code
const button = document.getElementById("myButton");

button.addEventListener("click", () => console.log("Button clicked!"));
button.addEventListener("mouseover", () => console.log("Mouse over button!"));
```

### 2. Keyboard Events
- These occur when the user interacts with the keyboard

| Event | Description | Example |
|:-----:|:-----------:|:-------:|
| `keydown` | Triggered when a key is pressed down | Detect key shortcuts
| `keyup` | Triggered when a key is released | Detect key release
| `keypress` | Deprecated, but previously triggered when a key producing a character was pressed | Detect keypresses

#### Example
```code
document.addEventListener("keydown", (event) => {
    console.log(`Key pressed: ${event.key}`);
});

document.addEventListener("keyup", () => console.log("Key released!"));
```

### 3. Form Events
- These are triggered when interacting with form elements

| Event | Description | Example |
|:-----:|:-----------:|:-------:|
| `submit` | Triggered when a form is submitted | Form validation
| `change` | Triggered when the value of an input, select, or textarea changes | Dropdown or checkbox updates
| `input` | Triggered when the value of an input or textarea changes | Live input updates
| `focus` | Triggered when an element gains focus | Highlight active inputs
| `blur` | Triggered when an element loses focus | Validation on losing focus
| `reset` | Triggered when a form is reset | Handle form resets

#### Example
```code
const form = document.querySelector("form");

form.addEventListener("submit", (event) => {
    event.preventDefault();
    console.log("Form submitted!");
});

const input = document.querySelector("input");
input.addEventListener("input", () => console.log(input.value));
```

### 4. Window Events
- These events are triggered on the window object

| Event | Description | Example |
|:-----:|:-----------:|:-------:|
| `load` | Triggered when the entire page (including images) is fully loaded | Initialize app on load
| `DOMContentLoaded` | Triggered when the DOM is fully loaded, but before images are loaded | Early initialization
| `resize` | Triggered when the browser window is resized | Responsive designs
| `scroll` | Triggered when the page is scrolled | Infinite scrolling
| `beforeunload` | Triggered before the page is unloaded | Warning before closing tabs

#### Example
```code
window.addEventListener("load", () => console.log("Page fully loaded!"));

window.addEventListener("resize", () => {
    console.log(`Window size: ${window.innerWidth} x ${window.innerHeight}`);
});
```

### 5. Clipboard Events
- These events deal with clipboard operations like copying or pasting

| Event | Description | Example |
|:-----:|:-----------:|:-------:|
| `copy` | Triggered when content is copied | Track clipboard usage
| `cut` | Triggered when content is cut | Track clipboard usage
| `paste` | Triggered when content is pasted | Validate pasted content

#### Example
```code
document.addEventListener("copy", () => console.log("Content copied!"));
```

### 6. Drag and Drop Events
- Used for implementing drag-and-drop functionality

| Event | Description | Example |
|:-----:|:-----------:|:-------:|
| `drag` | Triggered while an element is being dragged | Update drag status
| `dragstart` | Triggered when drag starts | Initialize drag operation
| `dragend` | Triggered when drag ends | Clean up drag effects
| `dragover` | Triggered when a dragged item is over a drop zone | Highlight drop zone
| `drop` | Triggered when an item is dropped in a drop zone | Handle dropped item

#### Example
```code
const item = document.getElementById("dragItem");
const dropZone = document.getElementById("dropZone");

item.addEventListener("dragstart", () => console.log("Drag started!"));
dropZone.addEventListener("dragover", (event) => event.preventDefault()); // Required to allow drop
dropZone.addEventListener("drop", () => console.log("Item dropped!"));
```

### 7. Media Events
- Triggered by media elements like `<audio>` or `<video>`

| Event | Description | Example |
|:-----:|:-----------:|:-------:|
| `play` | Triggered when playback starts | Monitor media state
| `pause` | Triggered when playback is paused | Monitor media state
| `ended` | Triggered when playback ends | Show replay options
| `volumechange` | Triggered when the volume is changed | Update volume display

#### Example
```code
const video = document.getElementById("myVideo");

video.addEventListener("play", () => console.log("Video is playing!"));
video.addEventListener("pause", () => console.log("Video paused!"));
```

### 8. Touch Events (For Mobile Devices)
- Triggered when a user interacts with the screen

| Event | Description | Example |
|:-----:|:-----------:|:-------:|
| `touchstart` | Triggered when a touch starts | Detect initial touch
| `touchmove` | Triggered when a finger moves on the screen | Track touch movement
| `touchend` | Triggered when a touch ends | Finalize touch operation

### Conclusion
- Wide variety of event listeners is there to respond to user actions and browser events
- To build robust, interactive applications, choose the appropriate event listener and attach it using `addEventListener`
- Always keep performance and event delegation in mind when working with many elements