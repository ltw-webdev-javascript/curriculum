---
layout: lesson
title: "Circle mover"
desc: "Use jQuery & CSS to make a small application that will move a circle around the screen with up, down, left & right buttons."

markbot_submit: true
hide_show_for_marks: true

extra_tutorials:
  - title: "Document object model"
    url: dom
    highlight: true
  - title: "JavaScript cheat sheet"
    url: javascript-cheat-sheet
  - title: "JavaScript +jQuery events slide deck"
    url: "/courses/javascript/javascript-jquery-events/"

fork:
  url: "https://github.com/acgd-webdev-javascript/circle-mover/fork"

goal:
  before: "We’ll have a fully functional application that moves a circle around the screen."
  image: goal.gif
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

steps:
  - title: "Set up project"
    before: |
      Before we get started, create some files and get ready.
    folders:
      - label: "circle-mover"
        type: folder
      - label: "index.html"
        indent: 1
      - label: "css"
        type: folder
        indent: 1
      - label: "main.css"
        indent: 2
      - label: "js"
        type: folder
        indent: 1
      - label: "main.js"
        indent: 2
    after: |
      1. Make an `index.html` & add the boilerplate code.
      2. Make a `main.css` in your `css` folder & add the boilerplate code.
      3. Make an empty `main.js` in your `js` folder & connect it to your HTML.
      4. Connect jQuery to your website, with the URL from [cdnjs](https://cdnjs.cloudflare.com/).
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."
      - label: "HTML snippets"
        text: "Create the boilerplate with `html5`, `viewport`, `css` & `jss`"
      - label: "CSS snippets"
        text: "Create the boilerplate with `borderbox`"

  - title: "HTML setup"
    before: |
      We’re going to need a couple HTML elements to make this work: a `<div>` and a `<button>`
    code_lang: html
    code_file: "index.html"
    code: |
      <!DOCTYPE html>
      <html lang="en-ca">
      <head>
        <meta charset="utf-8">
        <title>Circle mover</title>
        <meta name="viewport" content="width=device-width,initial-scale=1">
        <link href="css/main.css" rel="stylesheet">
      </head>
      <body>

        <button id="btn-right">Right</button>
        <div class="ball"></div>

        <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
        <script src="js/main.js"></script>
      </body>
      </html>
    lines:
      - num: 11
        text: "The `<button>` tag should only be used for JavaScript or forms—it **does not** link to other pages."
      - num: 12
        text: "We’re going to use CSS to make this `<div>` look like a circle."

  - title: "Making a rectangle round"
    before: |
      With a touch of CSS we can transform the `<div>` into a circle (because that’s totally necessary).
    code_lang: css
    code_file: "css/main.css"
    code: |
      html {
        box-sizing: border-box;
      }

      *, *::before, *::after {
        box-sizing: inherit;
      }

      .ball {
        width: 200px;
        height: 200px;
        position: absolute;
        top: 200px;
        left: 200px;
        background-color: red;
        border-radius: 100px;
      }
    lines:
      - num: "12-14"
        text: "Using `position: absolute` is really important here because we want to be able to the move the circle around the screen with coordinates."
    after: |
      With our HTML & CSS in place, this is what we should be seeing:

      ![](html-css.jpg)

  - title: "Right button functionality"
    before: |
      Now that we have all the HTML & CSS in place we can make the button work by adding a little JavaScript.
    code_lang: js
    code_file: "js/main.js"
    code: |
      var $ball = $('.ball');

      $('#btn-right').on('click', function () {
        var newLeft = $ball.offset().left + 10;
        $ball.css('left', newLeft);
      });
    lines:
      - num: 3
        text: |
          jQuery provides a function called `on()` that allows us to listen to events.

          1. The first argument is what event to listen to—in this code we’re listening to the `click` event.
          2. The second argument is a function that should be executed when that event triggers.
      - num: 4
        text: |
          With the `offset()` function we can get the exact pixel coordinates of an element on screen. It returns the `left` and `top` positions.

          Here we’re adding `10` onto the left coordinate, making it move rightwards.
      - num: 5
        text: |
          jQuery’s `css()` function allows us to change CSS properties and values directly, overwriting what’s inside our CSS file.

          1. The first argument is the name of the property we want to change—in this code, that’s `left`
          2. The second argument is the value we want to set—in this code we’re assigning a new left coordinate to the circle.
    after: |
      With a refresh in your browser you should now be able to click on the “Right” button to move the circle.

      ![](right.gif)

  - title: "Finish off the remaining buttons"
    before: |
      It’s time to finish of the rest of the functionality so the circle can move in all four directions.

      1. Create 3 new `<button>` tags in HTML: “Left”, “Up” & “Down”.
      2. Write 3 new click events in JavaScript to make the circle perform those functions.

  - title: "Bonus challenge"
    before: |
      Use a CSS property we’ve learned before—no JavaScript—to make the ball animate from position to position instead of just snapping.

---
