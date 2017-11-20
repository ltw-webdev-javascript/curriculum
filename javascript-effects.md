---
layout: slide-deck
title: "JavaScript effects"
desc: "How to apply animations and effects to websites using a combination of JavaScript and CSS."

slides:
  - type: super-big-text
    content: |
      **JavaScript effects**

  - content: |
      ## JS doesn’t do effects—CSS does

      - All the effects we see are created by CSS
      - JavaScript has no concept of animations—it’s all CSS
      - We trigger CSS into action with JS
    notes: |
      That’s not entirely true, just simplified. JS can do effects with the `<canvas>` tag: it’ll do full 2D & 3D graphics and interactions.

  - content: |
      ## Trigger with classes

      1. JavaScript will add a class to an element
      2. The class will have associated CSS
      3. That `animation` or `transition` will be triggered

  - type: interactive
    html: |
      <div></div>
    css: |
      div {
        background-color: darkred;
        transition: all .5s linear;
      }
      .is-clicked {
        background-color: orange;
      }
    css_lines:
      - num: 3
        text: |
          Remember that the `transition` must **always** be on the default state—never on the `:hover` or the class that JS adds.
    css_hidden: |
      div {
        height: 200px;
        width: 200px;
      }
    js: |
      $('div').on('click', function (e) {
        $(this).toggleClass('is-clicked');
      });
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  - type: interactive
    html_hidden: |
      <div></div>
    css: |
      div {
        height: 200px;
        width: 200px;
      }
      .is-clicked {
        animation: spin 1s ease;
      }
      @keyframes spin {
        0% { transform: rotate(0); }
        100% { transform: rotate(360deg); }
      }
    css_lines:
      - num: 5
        text: |
          The `.is-clicked` class doesn’t exist anywhere in our HTML—it’s added by the JavaScript code.

          It’s a fairly common convention to prefix the classes with `is-` or `js-` to denote that JavaScript is the thing that is affecting this class.
    css_hidden: |
      div {
        height: 200px;
        width: 200px;
        background-color: darkred;
      }
    js: |
      $('div').on('click', function (e) {
        $(this).addClass('is-clicked');
      });
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  - content: |
      ## Events

      Animations & transitions dispatch events that our JS can respond to:

      - `animationstart`, `animationiteration`, `animationend`
      - `transitionend`

  - type: interactive
    html_hidden: |
      <div></div>
    css_hidden: |
      div {
        height: 200px;
        width: 200px;
        background-color: darkred;
        animation: none 1s ease;
      }
      .is-clicked {
        animation-name: spin;
      }
      @keyframes spin {
        0% { transform: rotate(0); }
        100% { transform: rotate(360deg); }
      }
    js: |
      $('div').on('click', function (e) {
        $(this).addClass('is-clicked');
      });

      $('div').on('animationend', function (e) {
        $(this).removeClass('is-clicked');
      });
    js_lines:
      - num: 5
        text: |
          Here we’re listening to the special `animationend` event that isn’t triggered by the user, but’s triggered by the CSS when the keyframe animation completes.

          This event allows us to do things after the animation has finished playing.
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  - content: |
      ## Let’s no forget SVG!

      Treat it the same as any other HTML—just add classes, transitions & animations

  - type: interactive
    html: |
      <svg viewBox="0 0 200 200" width="200" height="200">
        <circle fill="midnightblue" cx="100" cy="100" r="90" />
      </svg>
    css: |
      circle {
        transition: all 1s ease;
      }
      .is-clicked {
        fill: purple;
      }
    js: |
      $('svg').on('click', function (e) {
        $('circle').toggleClass('is-clicked');
      });
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  - content: |
      ## Videos & tutorials

      - [JavaScript effects ➔](/topics/javascript-effects/)
---
