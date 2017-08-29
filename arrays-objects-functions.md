---
layout: slide-deck
title: "Arrays, objects & functions"
desc: "A quick overview of how arrays, objects, and functions work within Javascript."

slides:
  - type: super-big-text
    content: |
      **Arrays, objects & functions**

  - content: |
      ## Arrays

      Collections of *numbered* things—in a specific order

      Can put anything you want in an array: strings, numbers, arrays, objects, functions

      Each item is accessed by a number—its index

      **Denoted with square brackets `[]`**
    notes: |
      Think of an array like an `<ol>` in HTML: there’s a bunch of things and they’re in a specific order. Each thing is numbered.

  - type: code
    js: |
      var trees = ['Maple', 'Oak', 'Birch', 'Pine'];  // Square brackets

      console.log(trees[0]);                          // Get the first item
      document.write('<h1>' + trees[2] + '</h1>');    // Put the third item into an <h1>

      trees.push('Spruce');                           // Add a new item
      console.log(trees.length);                      // Count the number of items

      document.write('<ul>');
      trees.forEach(function (item) {                 // Loop over every item in array
        document.write('<li>' + item + '</li>');
      });
      document.write('</ul>');

  - content: |
      ## Objects

      Collections of *named* things—order is irrelevant

      Can put anything you want in an object: strings, numbers, arrays, objects, functions

      Each item is accessed by its name

      **Denoted with curly braces `{}`**
    notes: |
      Think of an object like a `<dl>` in HTML: there is a term and a description associated that term. You can get the description by referring to the term.

  - type: code
    js: |
      var latLong = {                                 // Curly braces
        latitude: 45.416667,
        longitude: -75.7
      };

      var dinos = [{                                  // Objects inside an array
          name: 'Apatosaurus',
          diet: 'Herbivore'
        }, {
          name: 'Microraptor',
          diet: 'Carnivore'
      }];

      document.write(latLong.longitude);              // Get the `longitude` item

      // Write a sentence using the second object in the array
      console.log('The ' + dinos[1].name ' is a feathered ' + dinos[1].diet + '.');

  - content: |
      ## Functions

      A chunk of reusable code—stored inside a variable

      Can accept information to change its functionality

      Can send information back to you when executed

      **Denoted with round brackets `()`**

  - type: code
    js: |
      var sayHello = function () {                    // Basic function
        console.log('Hello!');
      };

      var writeH1 = function (text) {                 // Accepts an argument
        document.write('<h1>' + text + '</h1>');
      };

      var getImg = function (src, alt) {              // Accepts two arguments and returns
        return '<img src="' + src + '" alt="' + alt + '">';
      }

      sayHello();
      writeH1('Amaze-balls!');

      // Return values can be stored in variables
      var img = getImg('octopus.jpg', 'A big, goopy cephalopod');

  - type: super-big-text
    content: |
      ```
      document.write();
      ```
    notes: |
      Let’s break down this Javascript piece of code. `document.write()` is built into the browser.

      - `document` is an object — we know because it’s followed by a dot (`.`)
      - `write` is one of the items inside document
      - `write()` is a function — we know because it’s followed by two round brackets (`()`)

  - type: code
    js: |
      var document = {
        write: function (text) {
          // Do whatever with the `text` variable
        }
      }
    notes: |
      If we were to create `document.write()` ourselves it would look something like this:

      - Make a new variable named `document`
      - `document` is equal to a new object (`{}`)
      - Inside the object, one of the properties is named `write`
      - `write` is equal to a new `function ()`

  - content: |
      ## Where are they used?

      - **Arrays** — getting HTML elements
      - **Objects** — each single HTML element
      - **Functions** — whenever a user clicks
    notes: |
      These are just some examples of where you might use these structures—it’s definitely **not** an exhaustive list.

  - content: |
      ## Videos & tutorials

      - [Javascript syntax ➔](/topics/javascript-syntax/)
      - [Javascript debugging ➔](/topics/javascript-debugging/)

---
