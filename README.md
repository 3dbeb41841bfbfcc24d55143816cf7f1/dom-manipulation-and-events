---
title: Document Object Model
type: lesson
duration: 1
authors:
    creators: Jesse Shawl (DC)
    editors: John Master (DC), Matt Scilipoti (DC), Mike Hopper (ATL)
competencies: Programming, Javascript
---

# DOM

- Explain what the DOM is and how it is structured
- Select and target DOM elements using DOM methods
- Select and target DOM elements using a query selector
- Create, read, update, and delete DOM elements
- Change the attributes or content of a DOM element

## Document Object Model (5 min)

The [**D**ocument **O**bject **M**odel](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
is a programming interface for HTML.

An HTML *document* is available for us to manipulate as an object, and this object is structured like a tree:

Like this:

![](http://www.tuxradar.com/files/LXF118.tut_grease.diagram.png)

Or this:

```
html
└── head
│   ├──title
│   ├──meta
│   ├──link[rel="stylesheet"]
|   └──script[type="text/javascript"]
|
└── body
    ├── header
    │   ├── h1
    │   └── nav
    └── section.simplicity
    |   └── h2
    │   └── article
    ├── section.life
    |   └── h2
    │   └── article
    │       └── block_quote
    │       └── block_quote
    └── footer
```

Let's create a web page and begin to inspect its structure.

```html
<!doctype html>

<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Sample HTML5 Page</title>
  <meta name="description" content="Sample HTML Page">
  <meta name="author" content="Mike Hopper">
</head>

<body>
  <section id="main">
    <h1>The DOM Rocks!</h1>
    <p>When this document gets loaded into the browser's memory, it is transformed from a static HTML document to a dynamic DOM tree. At this point we can use JavaScript to inspect and manipulate the nodes in the DOM tree.</p>
  </section>
</body>
</html>
```

Here is the DOM tree for the above HTML document:

![DOM Tree](https://raw.githubusercontent.com/ATL-WDI-Curriculum/dom-events/master/images/dom-tree.png)

## Accessing the document (10 min)

`document`
  - `document.head`
  - `document.body`

Each web page loaded in the browser has its own `document` object. The Document interface serves as an entry point to the web page's content.

### Everything is a Node
In the HTML DOM (Document Object Model), everything is a node:

* The document itself is a document node
* All HTML elements are element nodes
* All HTML attributes are attribute nodes
* Text inside HTML elements are text nodes
* Comments are comment nodes

### Element attributes

`element`

| Attribute        | Description                                            |
| ---------------- |:------------------------------------------------------ |
| .children        | Returns a collection of an element's child elements (excluding text and comment nodes) |
| .childNodes      | Returns a collection of an element's child nodes (including text and comment nodes) |
| .firstChild      | Returns the first child node of an element             |
| .lastChild       | Returns the last child node of an element              |
| .nextSibling     | Returns the next node at the same node tree level      |
| .parentElement   | Returns the parent element node of an element          |
| .parentNode      | Returns the parent node of an element                  |
| .classList       | Returns the class name(s) of an element                |
| .innerHTML       | Sets or returns the content of an element              |

Methods are available on any element:

### Element methods

`element`

| Attribute               | Description                                     |
| ----------------------- |:----------------------------------------------- |
| .getElementsByTagName   | Returns a collection of all child elements with the specified tag name |
| .getElementsByClassName | Returns a collection of all child elements with the specified class name |
| .querySelector          | Returns the first child element that matches a specified CSS selector(s) of an element |
| .querySelectorAll       | Returns all child elements that matches a specified CSS selector(s) of an element |
| .removeChild            | Removes a child node from an element
| .replaceChild           | Replaces a child node in an element

> You can use `document.getElementById(anElementId)` to lookup an element by it's ID.

See more element properties and methods at [DOM properties and methods](http://www.w3schools.com/jsref/dom_obj_all.asp).

## You Do: Selecting DOM elements (10 min)

https://github.com/ATL-WDI-Exercises/js-dom-quotes

## Creating/Removing DOM Elements (5 min)

* [Document.createElement](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)
* [Node.appendChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)
* [Node.removeChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/removeChild)

### Example

[CodePen: JavaScript DOM Manipulation Example](https://codepen.io/drmikeh/pen/YqxaPx?editors=1010)

## Break (5 min)

## Events (10 min)

Event handlers

> Imagine an interface where the only way to find out whether a key on the keyboard is being pressed is to read the current state of that key. To be able to react to keypresses, you would have to constantly read the key’s state so that you’d catch it before it’s released again. It would be dangerous to perform other time-intensive computations since you might miss a keypress.

> A better mechanism is for the underlying system to give our code a chance to react to events as they occur. Browsers do this by allowing us to register functions as handlers for specific events.

The above was taken from [Eloquent JavaScript](http://eloquentjavascript.net/14_event.html).

### What is an event?

An event is an object that is created whenever anything interesting happens (usually something the user did), such as a mouse click, a key press, or a scroll up or down.

***Every DOM element*** has its own `addEventListener` method, which allows you to listen specifically on that element.

### What is an Event Handler?

An ***event handler*** is a JavaScript function that is called whenever the browser detects a specific kind of event. The event handler receives the event object and performs any needed processing, which may include manipulating the DOM tree.

### Example:

[CodePen: Simple DOM Event Example](http://codepen.io/drmikeh/pen/RaZMax/?editors=1111)

```html
<button>Click me</button>
<div id="div1">
</div>
```

```css
body {
  margin: 20px;
}
button {
  background: blue;
  color: white;
}
div {
  margin: 3px;
  padding: 3px;

}
#div1 {
  margin-top: 10px;
  border-radius: 10px;
  background: lightblue;
}
```

```javascript
window.onload = function() {
  var button = document.querySelector("button");
  var count = 0;
  button.addEventListener("click", function() {
    console.log("Button was clicked: " + (++count));
    addElement(count);
  });
}
function addElement(num) {
  // create a new div element and give it some content
  var newDiv = document.createElement("div");
  var newContent = document.createTextNode("Button was clicked: " + num);
  // add the text node to the newly created div.
  newDiv.appendChild(newContent);
  // add the newly created element and its content into the DOM
  var currentDiv = document.getElementById("div1");
  currentDiv.appendChild(newDiv);
}
```

### Waiting for the DOM to load

> window.onload

When the window is loading it will take a while (in computer time) before it is ready for you to start adding events to the page. We can assign a function to `window.onload` and the function will ***wait*** until the DOM is fully loaded before executing the function.

### Common DOM Events

```javascript
element.onclick(someFunction);                          // a shortcut for addEventListener("click")
element.addEventListener('click', someFunction);        // register a function when a click event occurs on element
element.addEventListener('mouseover', someFunction);    // register a function when a mouseover (hover) event occurs on element
element.preventDefault();                               // prevent the default behavior from happening

## Examples

[[CodePen: Simple DOM Event Example 2](http://codepen.io/drmikeh/pen/VazXRd?editors=1011)

* http://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_element_addeventlistener


## Conclusion (5 min)

* Explain the sentence: 'The DOM is a data structure and an API'.
* When would you use `document.getElementById`?
* What does `element.appendChild(anotherElement)` do?
* Why is it a good practice to use `window.onload`?
* What is an Event Handler?
* What are some examples of DOM events?
* What is the difference between `onclick` and `addEventListener?`

## Homework

[Fellowship of the Ring DOM Manipulation](https://github.com/ATL-WDI-Exercises/fellowship)

## References

* [DOM Event](https://developer.mozilla.org/en-US/docs/Web/API/Event)
* [DOM Reference](https://developer.mozilla.org/en-US/docs/DOM/DOM_Reference)
* [DOM CheatSheet](http://christianheilmann.com/stuff/JavaScript-DOM-Cheatsheet.pdf)
```
