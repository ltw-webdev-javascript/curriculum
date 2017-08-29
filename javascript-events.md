---
layout: slide-deck
title: "Javascript events"
desc: "A quick overview of events in Javascript, what they are, how they’re triggered, and how to write code that listens to events."

slides:
  - type: super-big-text
    content: |
      **Javascript events**

  - content: |
      ## It’s all eventful

      Much of what we want to do with Javascript is wait for users to interact

      That user interaction is called an “event”

  - content: |
      ## Event listening

      1. When a user interacts with your website an event is triggered
      2. Your JS can listen to when that event happens
      3. A function you write can be called when an event happens

  - content: |
      ## Events

      - `click`, `dblclick`, `contextmenu`
      - `mousedown`, `mouseup`, `mouseover`, `mouseout`, `mousemove`
      - `keypress`, `keydown`, `keyup`
      - `focus`, `blur`, `change`, `submit`
      - animation, transition, touch, drag, browser
      - [and many, many more…](https://developer.mozilla.org/en-US/docs/Web/Events)

  - content: |
      ## Responding to events

      jQuery’s `on()` function can be used to listen and respond

      There’s also `off()` if you want to stop listening

  - type: interactive
    html: |
      <button id="click-me">Click me!</button>
    js: |
      $('#click-me').on('click', function () {
        alert('Hello, World!');
      });
    js_lines:
      - num: 1
        text: |
          This chunk of code will wait for a user to click the button then open a little alert window.

          1. `$('#click-me')` is the jQuery selector to find the HTML element with the matching ID.
          2. `.on('click'` is the event our code is waiting for: `click`
          3. `function () {` groups the code we want to run when the event is triggered.
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  - type: interactive
    html: |
      <ul>
        <li>Titanosaurus</li>
        <li>Apatosaurus</li>
        <li>Brontosaurus</li>
        <li>Brachiosaurus</li>
      </ul>
    css: |
      .is-clicked {
        background-color: limegreen;
      }
    js: |
      $('ul').on('click', 'li', function (e) {
        $(this).toggleClass('is-clicked');
      });
    js_lines:
      - num: 1
        text: |
          This event listener is slightly different: Notice that the we select the `<ul>` tag. But we really want to listen for events on `<li>` tags.

          After the `'click'` event name, we add another CSS selector, in this case `'li'`. This is called event delegation: it means that we’re listening for any `click` event on the `<ul>` but only when it comes from an `<li>` element.

          The benefit of doing this is that `<li>` tags can be added and removed and the click will still happen.
      - num: 2
        text: |
          There’s a special selector here—`$(this)`—it refers directly to the thing that was interacted with. In this case it refers to the single `<li>` our user clicked on.

          The `toggleClass()` function will add a class if it’s missing or remove the class if it already exists.
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  - type: interactive
    html: |
      <a class="stego-link" href="https://en.wikipedia.org/wiki/Stegosaurus">Go!</a>
    js: |
      var $link = $('.stego-link');

      $link.on('click', function (e) {
        e.preventDefault();
        alert($(this).attr('href'));
      });
    js_lines:
      - num: 3
        text: |
          Instead of using jQuery directly we can store the selected HTML element in variable and refer to the variable later.
      - num: 4
        text: |
          Since the element that’s being clicked on is an `<a>` tag, we know that it has some default functionality. The `<a>` tags purpose is to direct a user to another page.

          When we write Javascript, we have complete control over everything. By using `e.preventDefault()` we can stop the link from doing what it normally does and instead do what we want.
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  - type: interactive
    html: |
      <form>
        <label for="grocery-input">Shopping list</label>
        <input id="grocery-input">
        <button type="submit">Add</button>
      </form>
      <ul class="list"></ul>
    js: |
      var $input = $('#grocery-input');
      var $list = $(".list");

      $('form').on('submit', function (e) {
        var $li = $('<li>');
        e.preventDefault();
        $li.html($input.val());
        $list.append($li);
      });
    js_lines:
      - num: 4
        text: |
          Instead of listening for the `click` event it makes more sense to listen for the form’s `submit` event. This event isn’t dependent on how the user submits the form, just that they did so.
      - num: 7
        text: |
          - The `.html()` function is used to replace all the HTML code inside an element.
          - The `.val()` function is used to get the information a user typed into an input field.
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  - content: |
      ## Videos & tutorials

      - [Document object model ➔](/topics/dom/)
      - [Javascript cheat sheet ➔](/topics/javascript-cheat-sheet/)

---
