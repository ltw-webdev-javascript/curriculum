---
layout: slide-deck
title: "jQuery plugins"
desc: "A quick overview of using jQuery plugins to integrate quick, simple, already built functionality into your website."

slides:
  - type: super-big-text
    content: |
      **jQuery plugins**

  - content: |
      ## Pre-written JavaScript

      There are lots of pre-written JavaScript code bits out there (in the nebulous web)

      Quite a popular segment is jQuery plugins: new features added to jQuery
    notes: |
      These things can be done with jQuery itself but would require you to write a bunch of code—so someone has already written the code

  - content: |
      ## Example plugins

      - Lightboxes
      - Carousels
      - Animation systems
      - Parallax
      - Waypoints
      - etc.

  - content: |
      ## Using jQuery plugins

      They always require jQuery (obviously…)

      The `<script>` tags must go in a specific order:

      1. jQuery
      2. The plugin
      3. Your JavaScript file

  - type: code
    html: |
      <body>



        <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
        <script src="js/jquery.waypoints.min.js"></script>
        <script src="js/waypoints.js"></script>
      </body>
      </html>
    notes: |
      Important order:

      1. jQuery—first
      2. The plugin—second
      3. Your JavaScript file—last

  - content: |
      ## Starting the plugin

      jQuery plugins almost always want you to write some code to initialize the plugin. It’s usually in a form similar to this:

      ```js
      $('.thingy').thePluginName();
      ```
      It could be much more complicated too. You’ll have to read the documentation, they’re all different.

  - content: |
      ## Plugin initialization tips

      **Always put the plugin initialization code in your `main.js` file—I don’t care where their documentation tells you to put it!**

      Also, if their docs tell you to put the `<script>` tag in the `<head>` of your HTML—**they’re plain wrong.** `<script>` tags always go at the bottom right above the closing `</body>` tag.

  - content: |
      ## Videos & tutorials

      - [JavaScript + jQuery effects ➔](/topics/javascript-jquery-effects/)
---
