[[Wedding RSVP]] > Element

A wrapper for a DOM element that allows for more readable syntax for common operations
# Constructor
## Argument(s)
| Name      | Description                     |
| --------- | ------------------------------- |
| `element` | The `HTMLElement` to be wrapped |
# Properties
| Name       | Description                               |
| ---------- | ----------------------------------------- |
| `element`  | The `HTMLElement` that serves as the root |
| `children` | An array containing child `Element`s      |
# Methods
## append(element1, element2, ...)
Pushes all arguments to `this.children`

All arguments must be of type `Element`
## set(attribute, value)
Sets a given HTML attribute to the given value
## setContent(content)
Sets the inner HTML to `content`

`content` must be of type `String`
## addClass(className1, className2, ...)
Adds all arguments as classes

All arguments must be of type `String`