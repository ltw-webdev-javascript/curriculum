---
layout: lesson
title: "Bubble popper"
desc: "Use jQuery & CSS animations and transitions to make a small application that makes and pops random bubbles."

extra_tutorials:
  - title: "Javascript effects"
    url: javascript-effects
  - title: "Javascript cheat sheet"
    url: javascript-cheat-sheet
  - title: "Javascript effects slide deck"
    url: /courses/web-dev-4/javascript-effects/

goal:
  before: "We’ll have a fully functional application that—when the space key is pressed—makes a random, poppable bubble."
  image: goal.gif
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

fork:
  url: "https://github.com/acgd-webdev-javascript/bubble-popper/fork"

steps:
  - title: "Set up project"
    before: |
      Before we get started, create some files and get ready.
    folders:
      - label: "bubble-popper"
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

  - title: "HTML setup"
    before: |
      We’re not going to need any HTML elements to make this work, so the `<body>` can stay empty except for the `<script>` tags.
    code_lang: html
    code_file: "index.html"
    code: |
      <!DOCTYPE html>
      <html lang="en-ca">
      <head>
        <meta charset="utf-8">
        <title>Bubble popper</title>
        <meta name="viewport" content="width=device-width,initial-scale=1">
        <link href="css/main.css" rel="stylesheet">
      </head>
      <body>

        <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
        <script src="js/main.js"></script>
      </body>
      </html>
    lines:
      - num: 11
        text: "Don’t forget to hook up jQuery."
    notes:
      - label: "HTML snippets"
        text: "Create the boilerplate with `html5`, `viewport`, `css` & `jss`"

  - title: "Styling the bubbles"
    before: |
      With a touch of CSS we can transform any `<div>` into a bubble.
    code_lang: css
    code_file: "css/main.css"
    code: |
      html {
        box-sizing: border-box;
      }

      *, *::before, *::after {
        box-sizing: inherit;
      }

      .bubble {
        left: 0;
        top: 0;
        position: absolute;
        height: 50px;
        width: 50px;
        border-radius: 50%;
        background-color: lightblue;
      }
    lines:
      - num: "10-12"
        text: "Using `position: absolute` is really important here because we want to be able to the move the circle around the screen with coordinates."
    notes:
      - label: "CSS snippets"
        text: "Create the boilerplate with `borderbox`"

  - title: "Add random bubbles to the screen"
    before: |
      When the `Space` key is pressed on the keyboard, we’re going to create a new `<div>` tag, with the class of bubble, and place it on the screen in a random location.
    code_lang: js
    code_file: "js/main.js"
    code: |
      var $body = $('body');

      $('html').on('keydown', function (e) {
        var $bubble;

        if (e.key == ' ') {
          $bubble = $('<div>');
          $bubble.addClass('bubble');
          $bubble.css({
            'top': Math.random() * (document.documentElement.clientHeight - 100),
            'left': Math.random() * (document.documentElement.clientWidth - 100)
          });
          $body.append($bubble);
        }
      });
    lines:
      - num: 6
        text: |
          The `Space` key is represented by the key `' '` a literal space. [You can see all the different key values here.](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key/Key_Values)
      - num: "9"
        text: "If we want to change multiple CSS properties at the same time we can pass and object to the `.css()` function instead of calling it multiple times."
      - num: "10-11"
        text: |
          We can use `document.documentElement.clientWidth` & `height` to constrain the random coordinates to the dimensions of the window.

          The `- 100` here is subtracting the width of the circle so they don’t appear slightly off the screen.
    after: |
      At this point, pressing the `Space` key should create a random bubble on the screen.

      ![](create.gif)

  - title: "Make the bubbles grow"
    before: |
      When the bubbles appear on the screen, it’d be neat if they grew into place. With some CSS animations we can do that.
    code_lang: css
    code_file: "css/main.css"
    code: |
      .bubble {
        ⋮
        border-radius: 50%;
        background-color: lightblue;
        animation: bounce .5s cubic-bezier(.5, -.9, .6, 1.9) forwards;
        transform: translate(-50%, -50%);
      }

      @keyframes bounce {
        0% {
          height: 50px;
          width: 50px;
        }
        100% {
          height: 100px;
          width: 100px;
        }
      }
    lines:
      - num: "3-4"
        fade: true
      - num: 5
        text: |
          Add an `animation` to the bubble that makes a bounce effect.

          Notice in the keyframes that the bubble is just being scaled from `50px` to `100px`. The bouncing comes from the custom easing: `cubic-bezier()`

          With the `cubic-bezier()` function we can make any kind of easing we want. I didn’t magically come up with these numbers I used a [cubic bezier generator](http://cubic-bezier.com/).

          We’re using `forwards` here to keep the bubble at its bigger size when it’s done animating, otherwise it would snap back to the smaller size.
      - num: 6
        text: |
          The `transform` is here so the bubble scales from the centre, because we’re adjusting the width and height it will naturally scale from the top-left corner, so we’re changing the anchor point.

          Of course, I could have used `transform: scale()` inside `@keyframes` instead of `width` & `height` to acheive the same results.
    after: |
      With a refresh in your browser, pressing `Space` now should drop a bubble on the screen and it should animate.

      ![](animate.gif)

  - title: "Click to pop"
    before: |
      The next piece of code we’re going to write is to make the bubbles “pop” when they are clicked.

      To start, let’s write some Javascript that will add a class to the bubble when it’s clicked:
    code_lang: js
    code_file: "js/main.js"
    code: |
      ⋮
          $body.append($bubble);
        }
      });

      $body.on('click', '.bubble', function () {
        $(this).addClass('is-popping');
      });
    lines:
      - num: "2-4"
        fade: true
      - num: 6
        text: |
          We’re using event delegation here: listening for clicks on the `<body>`, but only activating the event handler when a `.bubble` is called upon.

          We need to use event delegation because we don’t know how many bubbles there are and we don’t want to add an event listener to every single one.

  - title: "Popping CSS"
    before: |
      The new `.is-popping` class will change the `width` & `height` to `0`, making the bubble shrink & set the `opacity` to `0` to fade the bubble away.

      We also need to add a transition to the `.bubble` to create the easing effect.
    code_lang: css
    code_file: "css/main.css"
    code: |
      .bubble {
        ⋮
        animation: bounce .5s cubic-bezier(.5, -.9, .6, 1.9) forwards;
        transform: translate(-50%, -50%);
        transition:
          width .3s cubic-bezier(.7, -.6, .4, 1.5),
          height .3s cubic-bezier(.7, -.6, .4, 1.5),
          opacity .3s ease-out
          ;
      }

      .is-popping {
        height: 0;
        width: 0;
        opacity: 0;
        animation-name: none;
      }

      @keyframes bounce {
        0% {
          height: 50px;
      ⋮
    lines:
      - num: "3-4"
        fade: true
      - num: "19-21"
        fade: true
      - num: "5-9"
        text: |
          The `transition` is written on multiple lines because certain properties are going to have different easing than others—and one line is difficult to read.

          The 3 different transitions:

          - The `width` & `height` should have a bouncing effect
          - The `opactiy` should just `ease-out`
      - num: "16"
        text: |
          It’s very important that we remove the `animation` at this point. Because the `forwards` in the animation forces the element to stay at its largest size after the animation is completed.

          Without removing the animation from the element we wouldn’t see it shrink.
    after: |
      When clicking on each of the bubbles now they should shrink and fade away.

      ![](pop.gif)

  - title: "Removing the element when completed"
    before: |
      Even though the bubble shrinks and fades away there’s still an invisible `<div>` in the HTML.

      *Let’s use Javascript to remove the `<div>` from the `<body>` after its animation has finished:*
    code_lang: js
    code_file: "js/main.js"
    code: |
      ⋮
        $(this).addClass('is-popping');
      });

      $body.on('transitionend', '.bubble', function () {
        $(this).remove();
      });
    lines:
      - num: "2-3"
        fade: true
      - num: 5
        text: |
          The code is listening for the `transitionend` event that will be triggered whenever the `.bubble` has finished its shrinking-fading transition.
      - num: 6
        text: |
          We then target `$(this)`—which represents the single ball that finished—and remove it from the `<body>`

---
