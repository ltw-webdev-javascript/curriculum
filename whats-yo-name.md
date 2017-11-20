---
layout: lesson
title: "What’s yo name?"
desc: "Watch some videos showing basic JavaScript syntax and build a small name comparing program."

markbot_submit: true
hide_show_for_marks: true

goal:
  image: "goal.png"
  before: |
    We’re going to make a small program that accepts a user’s name and writes out different sentences based on what they type.
  notes:
    - label: "Type it, type it real good"
      text: "Remember the purpose of this lesson is to type the code out yourself—build up that muscle memory in your fingers!"

extra_tutorials:
  - title: "JavaScript syntax"
    url: javascript-syntax
  - title: "JavaScript validator"
    url: /topics/validators/#validating-javascript
  - title: "JavaScript cheat sheet"
    url: javascript-cheat-sheet
    highlight: true
  - title: "JavaScript intro slide deck"
    url: /courses/javascript/javascript-intro/
    highlight: true

fork:
  url: "https://github.com/acgd-webdev-javascript/whats-yo-name/fork"

steps:
  - title: "Set up project"
    before: |
      Before we start writing any JavaScript we need to have an HTML file set up. That’s where we’ll start.
    folders:
      - label: "whats-yo-name"
        type: folder
      - label: "index.html"
        indent: 1
      - label: "js"
        type: folder
        indent: 1
      - label: "main.js"
        indent: 2
    after: |
      1. Make an `index.html` & add the boilerplate code.
      2. Make a `main.js` in your `js` folder.
    notes:
      - label: "Naming conventions"
        text: "Don’t forget to follow the [naming conventions](/topics/naming-paths-cheat-sheet/#naming-conventions)."
      - label: "HTML snippets"
        text: "Create the boilerplate with `html5`, `viewport`"

  - title: "Link the JavaScript to the HTML"
    before: |
      At the bottom of the `index.html` file we need to connect the JavaScript file.
    code_lang: "html"
    code_file: "index.html"
    code: |
      ⋮
      </head>
      <body>

        <script src="js/main.js"></script>
      </body>
      </html>
    lines:
      - num: "2-3"
        fade: true
      - num: 5
        text: |
          The `<script>` tag is used to connect a JavaScript file to HTML.

          It should always go at the bottom for two reasons:

          1. **Performance** — JavaScript will stop rendering the page until the JS loads. Putting it at the bottom makes the load time appear faster because the page can be displayed first.
          2. **HTML manipulation** — we want to manipulate HTML with our JS, but the HTML must be rendered to the screen before JS can do anything.
      - num: "6-7"
        fade: true
    after: |
      **JavaScript files are always connected at the bottom, right before the closing `</body>` tag.**

  - title: "Write some JavaScript!"
    before: |
      These few lines of code will ask a user for their name and display a message based on what they type.
    code_lang: "js"
    code_file: "main.js"
    code: |
      var newName = prompt('What is your name?');

      if (newName == 'Thomas') {
        alert('Names are the same!');
      } else {
        alert('Names are different.');
      }
    lines:
      - num: 1
        text: |
          The variable `newName` will hold whatever someone types into the dialogue box.

          The `prompt()` is a function built into JavaScript that will display a dialogue people can type into.
      - num: 3
        text: |
          The if-statement is going to compare the contents of `newName` against the string `'Thomas'`.

          - If they are the same the first path is taken.
          - If they are different the second path is taken.

          The double equals `==` means compare.
          A single equals `=` means set.
      - num: 4
        text: |
          The `alert()` function is built into JavaScript and will display a dialogue with some text.
    after: |
      Try it out in your browser. It should work great.

  - title: "Bonus challenge"
    before: |
      Change the program above so that the `alert` messages say what the user typed in. Make the messages read:

      - **“Hey Thomas, our names are the same!”**
      - **“Too bad our names are different, Thomas.”**
    notes:
      - label: "Hint"
        text: "You’ll have to combine strings and variables together with a special character."

---
