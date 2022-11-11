---
layout: lesson
title: "Contact list generator"
desc: "Use JavaScript to create a data structure representing contact information and display it on the page."

markbot_submit: true
hide_show_for_marks: true

extra_tutorials:
  - title: "JavaScript syntax"
    url: javascript-syntax
  - title: "JavaScript debugging"
    url: javascript-debugging
    highlight: true
  - title: "JavaScript validator"
    url: /topics/validators/#validating-javascript
  - title: "JavaScript cheat sheet"
    url: javascript-cheat-sheet
    highlight: true

goal:
  before: "We’re going to look at using objects inside an array to represent contact information. Then spit that information out to the page."
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

fork:
  url: "https://github.com/ltw-webdev-javascript/contact-list-generator/fork"

steps:
  - title: "Set up project"
    before: |
      Before we get started, create some files and get ready.
    folders:
      - label: "contact-list-generator"
        type: folder
      - label: "index.html"
        indent: 1
      - label: "js"
        type: folder
        indent: 1
      - label: "main.js"
        indent: 2
      - label: "contacts.js"
        indent: 2
    after: |
      1. Make an `index.html` & add the boilerplate code.
      2. Make a `main.js` in your `js` folder.
      3. Make a `contacts.js` in your `js` folder.
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."
      - label: "HTML snippets"
        text: "Create the boilerplate with `html5` & `viewport`"

  - title: "Connect the JavaScript files"
    before: |
      We can connect as many JavaScript files to our website as we want. *But, just as CSS, the more there are the slower your website.*
    code_file: "index.html"
    code_lang: html
    code: |
      ⋮
      </head>
      <body>

        <script src="js/contacts.js"></script>
        <script src="js/main.js"></script>
      </body>
      </html>
    lines:
      - num: "2-3"
        fade: true
      - num: "5-6"
        text: |
          Everything we write in one JavaScript file is usable in the other file. The order is important.
      - num: "7-8"
        fade: true
    notes:
      - label: "HTML snippets"
        text: "Create the `<script>` tag with `jss`"

  - title: "Write the data structure"
    before: |
      Inside our `contacts.js` file I want to write out the data for all of the contacts.
    code_file: "js/contacts.js"
    code_lang: js
    code: |
      var peeps = [
        {
          name: 'Mercury Man',
          email: 'theman@mercury.com',
          tel: '+05551234',
          loc: [46001200, 69816900]
        },
        {
          name: 'Venus ’Venturer',
          email: 'venus@theadventurer.com',
          tel: '+15551234',
          loc: [107477000, 108939000]
        },
        {
          name: 'Jupiter Juggernaut',
          email: 'thejugger@jupiter.com',
          tel: '+55551234',
          loc: [816040000, 740550000]
        }
      ];
    lines:
      - num: "1-2"
        text: "Notice how we’re creating an array and every item inside the array is an object."
      - num: 6
        text: "An array inside an object inside an array."
      - num: 7
        text: "Don’t forget the commas between each object!"

  - title: "Starting the function"
    before: |
      Let’s start writing the function that will take a list of peeps and output it to our HTML file.
    code_file: "js/main.js"
    code_lang: js
    code: |
      var listContacts = function (contacts) {
        // We’ll write stuff in here later
      };

      listContacts(peeps);
    lines:
      - num: 1
        text: |
          Functions are just another thing you can put inside a variable. They’re reusable pieces of code.

          In between the round brackets (`contact`) is an argument—you can call it whatever you want. An argument is a variable that’s only available inside the function. It can be set when executing the function.
      - num: 5
        text: |
          Here we execute the function. To call a function you write its variable name followed by open and close round brackets. Like `writeContacts()` or `document.write()`

          We can put information between the round brackets to set the function’s argument variables. The order you write it between the brackets is captured by the same order in the function.

          In this line `peeps` refers to the name of the variable we created in `contacts.js`.

  - title: "Output the contact names"
    before: |
      Let’s see if our function is working by outputting the name of the contacts and a page title.
    code_file: "js/main.js"
    code_lang: js
    code: |
      ⋮
      var listContacts = function (contacts) {
        document.write('<h1>Planetary peeps</h1>');

        contacts.forEach(function (item) {
          document.write(`<h2>${item.name}</h2>`);
          // More stuff going in here later
        });
      };

      listContacts(peeps);
      ⋮
    lines:
      - num: 2
        fade: true
      - num: 3
        text: "We’ll use `document.write()` to create an `<h1>` tag in our website."
      - num: 5
        text: |
          The `forEach` loop is a special kind of loop that will iterate over every single item in an array. With this loop we don’t need to know how many times to loop—JavaScript just does it.

          Notice that we pass in a `function()` to the loop. This function will be executed on every item in the array. The current array item will be saved into the functions first argument—here it’s called it `item`
      - num: 6
        text: |
          By writing code inside the `forEach` loop it will happen for every single item in the array.

          Notice the `item.name`:

          - `item` refers to the function argument variable defined in the `forEach` loop on the line above. It’s a representation of one single item in the array.
          - `.name` refers to one of the object properties we defined in `contacts.js`
      - num: "8-9"
        text: |
          Be careful of all these brackets.

          1. The first `}` closes the `function` inside the loop.
          2. The `)` closes the `forEach` loop.
          3. The last `}` closes the `listContacts` function.
      - num: 11
        fade: true
    after: |
      Check your browser and you should see all the contact names output.

      ![](names.jpg)

  - title: "Output the e-mail & phone"
    before: |
      Looking at the data in the `peeps`, I feel like much of the information should go into a `<dl>` tag.
    code_file: "js/main.js"
    code_lang: js
    code: |
      ⋮
        contacts.forEach(function (item) {
          document.write('<h2>' + item.name + '</h2>');
          document.write('<dl>');
          document.write('<dt>E-mail address</dt>');
          document.write(`<dd><a href="mailto:${item.email}">${item.email}</a></dd>`);
          document.write('<dt>Phone number</dt>');
          document.write(`<dd><a href="tel:${item.tel}">${item.tel}</a></dd>`);
          // More stuff to come here
          document.write('</dl>');
        });
      };
      ⋮
    lines:
      - num: "2-3"
        fade: true
      - num: 4
        text: "Start the `<dl>` tag by writing only the opening HTML tag."
      - num: 5
        text: "Write out a `<dt>` tag to before we get to the actual data."
      - num: 6
        text: |
          Write out `<dd>` and `<a>` tags by using the `` ` `` to concatenate a bunch of things together. Inside the interpolated string use `${}` to surround variables.
      - num: 10
        text: "Finally end the `<dl>` tag by writing the closing HTML tag."
      - num: "11-12"
        fade: true
    after: |
      Check your browser and you should be seeing more information from the contacts.

      ![](email-tel.jpg)

  - title: "Display the location"
    before: |
      Unlike the other pieces of data, the `loc` is an array, so we have to treat it slightly differently.
    code_file: "js/main.js"
    code_lang: js
    code: |
      ⋮
          document.write('<dt>Phone number</dt>');
          document.write(`<dd><a href="tel:${item.tel}">${item.tel}</a></dd>`);
          document.write('<dt>Location</dt>');
          document.write(`<dd>Between ${item.loc[0]} km & ${item.loc[1]} km from the Sun.</dd>`);
          document.write('</dl>');
        });
      };
      ⋮
    lines:
      - num: "2-3"
        fade: true
      - num: 5
        text: |
          Notice the `item.loc[0]`:

          - `item` refers to the function argument variable defined in the `forEach` loop. It’s a representation of one single item in the array.
          - `.loc` refers to one of the object properties we defined in `contacts.js`
          - The `[0]` will get the first item out of the `loc` array.
      - num: "6-8"
        fade: true
    after: |
      Check your browser and you lots of details now.

      ![](loc.jpg)

  - title: "Add more contacts"
    before: |
      We’ve created a very basic templating system now where we don’t have to copy-and-paste a bunch of HTML code to write out similar information.

      There’s a motto in programming: **Keep things DRY**. As in “Don’t Repeat Yourself”. *If you have to copy and paste you’re doing something wrong.*

      **Go into the `contacts.js` file and add a new contact at the bottom.** When you refresh your HTML page a new entry should magically appear.
---
