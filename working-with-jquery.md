---
layout: lesson
title: "Working with jQuery"
desc: "Use jQuery to simplify manipulating HTML while building a list of dinosaurs in JavaScript."

markbot_submit: true
hide_show_for_marks: true

goal:
  before: "We’re going to look at how to use jQuery to change how we work with HTML in JavaScript."
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

fork:
  url: "https://github.com/ltw-webdev-javascript/working-with-jquery/fork"

extra_tutorials:
  - title: "Document object model"
    url: dom
    highlight: true
  - title: "JavaScript cheat sheet"
    url: javascript-cheat-sheet
  - title: "jQuery introduction slide deck"
    url: "/courses/javascript/jquery-introduction/"

steps:
  - title: "Set up project"
    before: |
      Before we get started, create some files and get ready.
    folders:
      - label: "working-with-jquery"
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
      - label: "dinos.js"
        indent: 2
      - label: "main.js"
        indent: 2
      - label: "images"
        type: folder
        indent: 1
      - label: "diplodocus.jpg"
        indent: 2
      - label: "hadrosaur.jpg"
        indent: 2
      - label: "iguanodon.jpg"
        indent: 2
    after: |
      1. Make an `index.html` & add the boilerplate code.
      2. Make a `main.css` in your `css` folder & add the boilerplate code.
      3. Make an empty `dinos.js` in your `js` folder & connect it to your HTML.
      4. Make an empty `main.js` in your `js` folder & connect it to your HTML.
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."
      - label: "HTML snippets"
        text: "Create the boilerplate with `html5`, `viewport`, `css` & `jss`"
      - label: "CSS snippets"
        text: "Create the boilerplate with `borderbox`"

  - title: "Write the HTML"
    before: |
      Here’s the HTML we’ll need to complete this demo.
    code_lang: html
    code_file: "index.html"
    code: |
      <!DOCTYPE html>
      <html lang="en-ca">
      <head>
        <meta charset="utf-8">
        <title>Working with jQuery</title>
        <meta name="viewport" content="width=device-width,initial-scale=1">
        <link href="css/main.css" rel="stylesheet">
      </head>
      <body>

        <h1></h1>
        <ul></ul>

        <h2 class="more-dinos">Prehistoric air creatures</h2>

        <script src="js/dinos.js"></script>
        <script src="js/main.js"></script>
      </body>
      </html>
    lines:
      - num: "11-14"
        text: "We’re going to manipulate these HTML tags in our JavaScript."

  - title: "Connect jQuery"
    before: |
      There are many different ways to include jQuery in our project. The fastest is to use a content delivery network (CDN) and link to their copy of jQuery, like we do with Google Fonts.

      [**Go to cdnjs ➔**](https://cdnjs.com/)

      ![](cdnjs.jpg)

      1. Search for “jquery”.
      2. Press the `copy` button beside the URL.
      3. Create a new `<script>` tag in our HTML.
      4. Paste the URL into the `src=""` attribute.
    code_lang: html
    code_file: "index.html"
    code: |
      ⋮
        <h2 class="more-dinos">Prehistoric air creatures</h2>

        <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
        <script src="js/dinos.js"></script>
        <script src="js/main.js"></script>
      </body>
      </html>
    lines:
      - num: 2
        fade: true
      - num: 4
        text: 'Paste the URL from cdnjs into the `src=""` attribute of the `<script>` tag.'
      - num: "5-8"
        fade: true
    after: |
      **The order of the `<script>` tags is extremely important—put jQuery first.**

  - title: "Make the dinosaur array"
    before: |
      Before we start manipulating our HTML, let’s make a list of dinosaurs we can use.
    code_lang: javascript
    code_file: "js/dinos.js"
    code: |
      var dinos = [
        {
          name: 'Diplodocus',
          img: 'diplodocus.jpg'
        },
        {
          name: 'Hadrosaur',
          img: 'hadrosaur.jpg'
        },
        {
          name: 'Iguanodon',
          img: 'iguanodon.jpg'
        }
      ];

  - title: "Write some HTML manipulating JavaScript"
    before: |
      We don’t need jQuery to manipulate our HTML with JavaScript—jQuery just provides a simplified interface for common tasks.
    code_lang: javascript
    code_file: "js/main.js"
    code: |
      var $h1 = $('h1');
      var $ul = $('ul');

      $h1.html('Dinosaurs!');
      $ul.addClass('dino-list');

      $('.more-dinos').remove();
    lines:
      - num: "1-2"
        text: |
          JavaScript uses CSS selectors to choose things in the page.

          In between the `()` is the CSS selector: we can use tags, classes, IDs, `:first-child`, whatever.

          We’re storing references to the HTML tags for later use in two variables.

          The `$` at the front of the variable isn’t necessary—it’s just common practice to put a dollar sign at the start of variables that represent jQuery objects.
      - num: 4
        text: |
          jQuery’s `html()` function allows us to change the HTML code inside an element.
      - num: 5
        text: |
          With jQuery we can add and remove classes using these two functions:

          - `addClass()`
          - `removeClass()`

          There’s also `hasClass()` that we can use in if statements to see if the class exists on an element.
      - num: 7
        text: |
          We don’t need to always store a reference to the HTML element in a variable if we are only going to use it once.

          jQuery’s `remove()` function will delete an element from the document.
    after: |
      This is what we should see now that we’ve manipulated the HTML a little bit

      ![](html-manipulation.jpg)

      *Notice how the `<h2>` tag has been deleted and the `<h1>` tag now has text inside it.*

  - title: "Generate the dinosaur list"
    before: |
      Using a combination of the Javasript we already know and jQuery functions we’re going to loop over all the dinosaurs and generate HTML for them.
    code_lang: javascript
    code_file: "js/main.js"
    code: |
      ⋮
      $ul.addClass('dino-list');

      $('.more-dinos').remove();

      dinos.forEach(function (dino) {
        var $li = $('<li>');
        var $figure = $('<figure>');
        var $img = $('<img>');
        var $caption = $('<figcaption>');

        $caption.html(dino.name);
        $img.attr('src', 'images/' + dino.img);

        $figure.append($img, $caption);
        $li.append($figure);
        $ul.append($li);
      });
    lines:
      - num: "2-4"
        fade: true
      - num: 6
        text: "We’ll use a `forEach` loop to iterate over the dinosaur array."
      - num: "7-10"
        text: |
          These variables look very similar to previous jQuery selections. But because they have angle brackets `<>` that means we’re creating a **new** element.
      - num: 13
        text: |
          jQuery has a function called `attr()` that allows us to manipulate attributes on HTML elements.

          `attr(attribute-name, attribute-value)`

          If you don’t put the second argument, the value, then jQuery will get the attribute value and return it.
      - num: 15
        text: |
          jQuery has an `append()` function that will add HTML into other HTML elements.

          We can pass it as many new elements that we want and it will add them to the end inside the HTML element.

          ---

          There are a few more manipulations like this:

          - `prepend()` — add to the beginning, inside the HTML element.
          - `after()` — add to the HTML below this elements closing tag.
          - `before()` —
      - num: 17
        text: |
          Up until this line the dinosaur won’t even be visible on the screen. We created new HTML elements, but they only existed in the JavaScript. This line will add them to the HTML tag that’s already in our `index.html` file.

  - title: "Style it up"
    before: |
      Let’s add a little CSS to our application to style things a little more nicely.
    code_lang: css
    code_file: "css/main.css"
    code: |
      ⋮
      *, *::before, *::after {
        box-sizing: inherit;
      }

      .dino-list {
        margin: 0;
        padding: 0;
        list-style-type: none;
      }

      .dino-list li {
        margin-bottom: 1.5rem;
      }

      .dino-list figure {
        margin: 0;
      }

      .dino-list img {
        display: block;
        width: 200px;
      }
    lines:
      - num: "2-4"
        fade: true
      - num: 6
        text: |
          The `.dino-list` class doesn’t exist anywhere in our HTML, we added it to the `<ul>` using JavaScript, with this line: `$ul.addClass('dino-list');`

---
