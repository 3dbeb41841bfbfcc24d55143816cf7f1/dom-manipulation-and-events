# Marc jQuery/JS DOM Events

##Agenda - IWBAT...

- Understand Event Driven Programming
- Create addEventListeners
- Understand and create DOM Events
- Explain why we need to use a `window.onload` function.
- Understand Event bubbling and stop event propagation

<br>

## Event Driven Programming

We've written a couple of different kinds of programs so far. Imperative ones, and Object-Oriented ones. 

- **Imperative** code that starts at the top line, and chugs down through it until it finishes. 
- **Object oriented** programs, where we define a bunch of objects and then our code jumps around as necessary. 

But we've also written **event-driven** programs, though we haven't called it that. 

- When our web server runs, it sets up our app and then just sits there. 
- It's not until something happens - an event - our visit to the web page - that our code runs. 

We can define events on elements, and what JS to run when the event happens. 

<br>

## addEventListener

Before we dive into jQuery events lets take a look at how traditional Javascript handles events. The concept of 'events' will also be important when we get to front-end JS frameworks.

The `addEventListener()` method attaches an event handler to the specified element.

`element.addEventListener(event, function, useCapture);`

- The first parameter is the type of the event (like "click" or "mousedown").
- The second parameter is the function we want to call when the event occurs.
- The third parameter is a boolean value specifying whether to use event bubbling or event capturing. This parameter is optional.

<br>


## Event Bubbling - Lowest to highest

What if you have an `a href` within another click event listener? Maybe hovering over faces in facebook?


Open the next file from London: `bubbling_events.html`

Demonstrate that you can comment out the child #2 stop prop and the difference it makes.

The concept of **event bubbling** was introduced to deal with situations where a single event, such as a mouse click, may be handled by two or more event handlers defined at different levels of the **Document Object Model (DOM)** hierarchy. If this is the case, the event bubbling process starts by executing the event handler defined for individual elements at the **lowest level** (e.g. individual hyperlinks, buttons, table cells etc.). From there, the event bubbles up to the containing elements (e.g. a table or a form with its own event handler), then up to even higher-level elements (e.g. the BODY element of the page). Finally, the event ends up being handled at the highest level in the DOM hierarchy, the document element itself (provided that your document has its own event handler).

## Event Capturing - Lowest to highest
Event capturing is the opposite of bubbling (events are handled at higher levels first, then sink down to individual elements at lower levels). Event capturing is supported in fewer browsers and rarely used; notably, Internet Explorer prior to version 9.0 does not support event capturing.

### Event Propagation

The term **event propagation** is often used as a synonym of event bubbling. However, strictly speaking, event propagation is a wider term: it includes not only **event bubbling** but also **event capturing**. 

```
.stopPropagation();
```

<br>

## DOM Events

[Inspired from SF Lesson](https://github.com/sf-wdi-15/notes/blob/master/week_01_programming_fundamentals_with_the_web/day_4_dom/dusk_dom/README.md)

 We can try this on the Atlanta CL page or use this [codepen](http://codepen.io/marcwright/pen/xGwrdg?editors=101).


### `monitorEvents` 

In chrome we can try the following:

`monitorEvents(window)` 


Let's listen for a click on a `div` on our `greeting` div;

```
document.getElementById("greeting").onclick = function(event){
  alert("Clicked!!")
};
```
we can also listen for other types of events like hovering

```
document.getElementById("greeting").onmouseover = function(event){
  alert("hovering!!")
};

```
or after we're done hover

```
document.getElementById("greeting").onmouseout = function(event){
  alert("read anything interesting??")
};

```

<br>


## Window.onload
When the window is loading it will take a while before it is ready for you to start adding events to the page.


This will work:

```
<script type="text/javascript">
    window.onload = function(){
      var el = document.getElementById("blue_div");
      el.style.backgroundColor = "blue";
    }
</script>

```



<br>

## Lab/Code Along

[JSFiddle Starter with instructions](http://jsfiddle.net/marcwright/x6ncsqLz/1/) - **Be sure to fork!**

[JSFiddle Finished](http://jsfiddle.net/marcwright/x4u5D/149/) 

[JSBin Starter](http://jsbin.com/rawigi/3/edit) - **Be sure to clone!**

[JSBin Finished](http://jsbin.com/kalutepori/2/edit)

Examples:

- click me
- show/hide - add the code below to toggle:

```
//make the show button a Toggle
<button id="show-btn">Toggle menu</button>

//change the show function to a toggle
$("#show-btn").click(handleMenu)

function handleMenu() {
 $("#menu").toggle();     
}
```

- keyup with binding
- To do list appendTo() and prependTo()
- add to todo list to make done items green:
```
.css('background-color', 'green');
```
- you can also add a class: `.addClass('large');`

<br>

##LAB

- Convert traffic light to jquery. Add the starter and js finished versions to their repo.
- Headless DOM?


Others:

- Add jquery to blackout (it uses a function) - could be a morning exercise.
- add jquery to color switcher js version
- convert the click events to jquery
- convert jedi academy to jquery
- add a jquery feature to your project

