---
layout: slide-deck
title: "JavaScript + jQuery accessibility"
desc: "Describing accessibility considerations for JavaScript functionality within websites."

slides:
  - type: super-big-text
    content: |
      **JavaScript + jQuery accessibility**

  - content: |
      ## JavaScript isn’t inaccessible

      But if you’re not careful you can create some horribly inaccessible solutions

      Since you have complete control over HTML & CSS you can interfere with accessibility tools

  - content: |
      ## Always start with strong semantics

      - If it doesn’t link to another page don’t use a `<a>` tag
      - There are more tags than just `<div>`
      - If it’s a clickable thing it should be a `<button>`
      - Always use the browser’s default controls first—they have all the accessibility functionality built-in

  - content: |
      ## Keyboards rule

      *Always make your interaction work with the keyboard!*

  - content: |
      ## ARIA can help

      ARIA, the accessibility standard is targeted at JavaScript applications

      Adding ARIA roles & states to elements with JavaScript helps accessibility tools understand the purpose
    notes: |
      ### Helpful links

      - [ARIA roles](https://www.w3.org/TR/wai-aria-1.1/#roles_categorization)
      - [ARIA states & properties](https://www.w3.org/TR/wai-aria-1.1/#states_and_properties)

  - type: code
    html: |
      <!-- Used to label something, like `alt=""` on images -->
      <i class="icon" aria-label="Play"><svg></svg></i>

      <!-- Used to define what element on the page this thing controls -->
      <button aria-controls="SOME-ID"></button>

      <!-- Define what kind of control this is -->
      <!-- There are many more roles than the landmark roles we’ve previously used -->
      <div role="tabpanel"></div>

      <!-- To demonstrate when something is active or hidden -->
      <button aria-pressed="true"></button>
      <button aria-selected="true"></button>
      <div aria-hidden="true"></div>

  - type: interactive
    html: |
      <button id="pause-btn" aria-pressed="false" aria-label="Pause">
        <i class="icon i-96">
          <svg class="icon-pause"><use xlink:href="images/icons.svg#pause"></use></svg>
          <svg class="icon-play"><use xlink:href="images/icons.svg#play"></use></svg>
        </i>
      </button>
    css: |
      .icon-play {
        visibility: hidden;
      }

      [aria-pressed="true"] .icon-pause {
        visibility: hidden;
      }

      [aria-pressed="true"] .icon-play {
        visibility: visible;
      }
    css_lines:
      - num: 5
        text: |
          Using the `[aria-pressed]` attribute selector we can hide & show the appropriate icon inside the button.
    js: |
      $('#pause-btn').on('click', function () {
        if ($(this).attr('aria-pressed') == 'true') {
          $(this).attr('aria-pressed', false);
        } else {
          $(this).attr('aria-pressed', true);
        }
      });
    js_lines:
      - num: 2
        text: |
          The if-statement checks to see what the `aria-pressed` is currently: `true` or `false`
      - num: 3
        text: |
          We manipulate the `aria-pressed` attribute with the `attr()` function setting it to the opposite of what it currently is.
    css_hidden: |
      .icon {
        display: inline-block;
        position: relative;
        background: transparent none no-repeat center center;
        background-size: contain;
        vertical-align: middle;
      }

      .i-96, .i--96 {
        height: 96px;
        width: 96px;
      }

      .icon svg {
        left: 0;
        height: 100%;
        position: absolute;
        top: 0;
        width: 100%;
        fill: currentColor;
      }
    js_hidden: |
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  - content: |
      ## Videos & tutorials

      - [JavaScript, jQuery & accessibility ➔](/topics/javascript-jquery-accessibility/)
      - [Accessibility ➔](/topics/accessibility/)
      - [Accessibility cheat sheet ➔](/topics/accessibility-cheat-sheet/)
      - [Accessibility checklist ➔](/topics/accessibility-checklist/)
      - [Progressive enhancement ➔](/topics/progressive-enhancement/)

---
