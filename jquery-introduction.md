---
layout: slide-deck

title: "jQuery introduction"

slides:
  - type: super-big-text
    content: |
      **jQuery introduction**

  - content: |
      ## jQuery is Javascript

      - Simplifies the interface to HTML
      - Provides a bunch of already made functionality
      - *Not required to do HTML manipulation*

  - content: |
      ## Use from a CDN

      Include jQuery from a content delivery network
      —like we do with Google Fonts

      [**cdnjs ➔**](https://cdnjs.com/)
    notes: |
      This is not the only way to use jQuery, just the most straight forward.

      1. Go to [cdnjs.com](https://cdnjs.com)
      2. Search for “jquery”
      3. Beside the first result there’s a copy button—that’s the URL you’ll need for the `<script>` tag

  - content: |
      ## It’s all money from here

      Everything that is jQuery is inside the `$()` function

      Use the `$()` function to select HTML then manipulate the HTML element
    notes: |
      The `$` is the name the developers of jQuery decided to call their main function.

      Almost everything you want to do with jQuery is within that function.

  - content: |
      ## Based around CSS selectors

      jQuery (and Javascript) use CSS selectors to grab things in HTML

      - `ul`, `h1`, `div`
      - `.dino-list`, `.bones`
      - `#stego`
      - `main > p:first-child`
      - etc.

  - type: code
    html: |
      <h1>Dinosaurs!</h1>
      <ul>
        <li>Stegosaurus</li>
        <li class="tri">Triceratops</li>
        <li>Ankylosaurus</li>
      </ul>
    js: |
      $('h1')                  // Find all the <h1> tags
      $('ul')                  // Find all the <ul> tags
      $('ul li:last-child')    // Find the last <li> tags inside <ul> tags
      $('.tri')                // Find everything with the class of `.tri`
    notes: |
      Inside the `$()` function you write a CSS selector—exactly the same as you’d write in CSS.

      That will make jQuery search for and find the HTML element on your page.

      After jQuery has found the HTML element you can manipulate it.

  - type: code
    js: |
      var $h1 = $('h1');                          // Store a reference to the HTML element
      $h1.html('Dinosaurs rock!');                // Change the HTML inside the <h1>

      $('ul li:last-child').remove()              // Delete and HTML element
      $('ul').append('<li>Apatosaurus</li>');     // Add HTML to the end of the element

      var $newLi = $('<li>');                     // Make a new HTML tag, notice the `<>`
      $newLi.html('Diplodocus');
      $('ul').prepend($newLi);                    // Add HTML to the start of an element

      $h1.addClass('mega');                       // Add a class to the HTML element
      $newLi.hasClass('dino');                    // Checks if a class exists

      $('ul li').each(function () {               // Loop over a bunch of HTML elements
        $(this).addClass('kilo');                 // $(this) is the current HTML element
      });

  - content: |
      ## [api.jqeury.com](https://api.jquery.com/) is your best friend

      It has all the documentation for all the different features that are built into jQuery

  - content: |
      ## Videos & tutorials

      - [Document object model ➔](/topics/dom/)
      - [Javascript cheat sheet ➔](/topics/javascript-cheat-sheet/)

---
