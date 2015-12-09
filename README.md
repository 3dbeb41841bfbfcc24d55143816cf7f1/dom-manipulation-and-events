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
| ---------------- |:------------------------------------------------------:|
| .children        | Returns a collection of an element's child element (excluding text and comment nodes) |
| .childNodes      | Returns a collection of an element's child nodes (including text and comment nodes) |
| .firstChild      | Returns the first child node of an element             |
| .lastChild       | Returns the last child node of an element              |
| .nextSibling     | Returns the next node at the same node tree level      |
| .parentElement   | Returns the parent element node of an element          |
| .parentNode      | Returns the parent node of an element                  |
| .classList       | Returns the class name(s) of an element                |

Methods are available on any element:

### Element methods

`element`

| Attribute               | Description                                     |
| ----------------------- |:-----------------------------------------------:|
| .getElementsByTagName   | Returns a collection of all child elements with the specified tag name |
| .getElementsByClassName | Returns a collection of all child elements with the specified class name |
| .querySelector          | Returns the first child element that matches a specified CSS selector(s) of an element |
| .querySelectorAll       | Returns all child elements that matches a specified CSS selector(s) of an element |
| .removeChild            | Removes a child node from an element
| .replaceChild           | Replaces a child node in an element

> You can use `document.getElementById(anElementId)` to lookup an element by it's ID.

## You Do: Selecting DOM elements (10 min)

https://github.com/ga-dc/js-dom-quotes

## Altering DOM Elements (5 min)

- [.textContent](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent)
- .innerHTML
- .setAttribute(name, value);
- .id
- .classList.toggle (add, remove, contains)
- .style

## You do: Logo hijack (15 min)

1. Open up www.google.com in Chrome or Firefox, and open up the console.
- Store the url to the Yahoo logo in a variable.
- Find the Google logo and store it in a variable.
- Modify the source of the logo IMG so that it's a Yahoo logo instead.
- Find the Google search button and store it in a variable.
- Modify the text of the button so that it says "Yahooo!" instead.

Bonus: Add a new element between the image and the search textbox, telling the world that "Yahoo is the new Google".

## Creating/Removing DOM Elements (1 min)

- [Document.createElement](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)
- [Node.appendChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)
- Node.removeChild

## Break (5 min)

## Events (10 min)

What is an event?
http://eloquentjavascript.net/14_event.html

- .onclick
- .addEventListener
  - click
  - mouseover
- .preventDefault()

## Examples

- [jessica hische](http://jessicahische.is/)
- [color scheme switcher](https://github.com/ga-dc/color-scheme-switcher)

## Conclusion (5 min)

1. What is the difference between a method and an attribute?
2. What is the difference between `onclick` and `addEventListener?`

## Break (10 min)
---

## Homework

<https://github.com/ga-dc/fellowship>


## References
- - https://developer.mozilla.org/en-US/docs/Web/API/Event
