---
layout: base
title: LxD Game
permalink: /CodeID
comments: true
---
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Code Identify Game</title>
  <style>
    body {
      font-family: 'Segoe UI', Arial, sans-serif;
      /* pastel pink -> pastel blue gradient */
      background: #9797d4ff;
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
      justify-content: center;
      align-items: center;
    }
    .game-container {
      background: #ffffffff;
      border-radius: 12px;
      box-shadow: 0 2px 12px rgba(0,0,0,0.08);
      padding: 2rem 2.5rem;
      margin-top: 2rem;
      min-width: 350px;
      max-width: 580px;
      width: 580px;
      flex: 0 0 580px;
    }
    .game-flex-row {
      display: flex;
      flex-direction: row;
      align-items: flex-start;
      gap: 2.5rem;
      width: 800px;
      max-width: 95vw;
      margin: 0 auto;
      justify-content: center;
    }
    .explanation-panel {
      min-width: 260px;
      max-width: 320px;
      width: 260px;
      background: #f3f2faff;
      border-radius: 10px;
      box-shadow: 0 2px 10px rgba(76,64,101,0.07);
      padding: 1.2rem 1.3rem;
      margin-left: 0.5rem;
      font-size: 1.05rem;
      color: #4c4065ff;
      visibility: hidden;
      opacity: 0;
      transition: opacity 0.3s, visibility 0.3s;
      height: auto;
      flex: 0 0 260px;
    }
    .explanation-panel.show {
      visibility: visible;
      opacity: 1;
      animation: fadeInNext 0.4s;
    }
    .code-block {
      background: #222;
      color: #e0e0e0;
      border-radius: 8px;
      padding: 1.2rem;
      font-size: 1.1rem;
      font-family: 'Fira Mono', 'Consolas', monospace;
      margin-bottom: 2rem;
      white-space: pre-wrap;
      word-break: break-word;
    }
    .options-bar {
      display: flex;
      gap: 1rem;
      justify-content: center;
      margin-bottom: 1rem;
    }
    .option-btn {
      /* pastel blue buttons */
      background: #9c99ccff;
      color: #eae8f5ff;
      border: none;
      border-radius: 6px;
      padding: 0.7rem 1.5rem;
      font-size: 1rem;
      cursor: pointer;
      transition: background 0.2s, transform 0.06s;
    }
    .option-btn:hover {
      background: #9c99ccff;
      transform: translateY(-1px);
    }
    .result-message {
      text-align: center;
      font-size: 1.1rem;
      margin-top: 0.5rem;
      min-height: 1.5em;
    }
    .correct {
      color: #2e8b57;
      font-weight: bold;
    }
    .incorrect {
      color: #c0392b;
      font-weight: bold;
    }
    .next-btn {
      margin-top: 1.2rem;
      background: #9d5663ff;
      color: #fff;
      border: none;
      border-radius: 8px;
      padding: 0.85rem 2.2rem;
      font-size: 1.15rem;
      font-weight: 700;
      cursor: pointer;
      display: none;
      opacity: 0;
      transition: opacity 0.3s, background 0.2s, transform 0.15s;
      box-shadow: 0 2px 12px rgba(76,64,101,0.10);
    }
    .next-btn.show {
      display: inline-block !important;
      opacity: 1;
      animation: fadeInNext 0.4s;
    }
    .next-btn:hover {
      background: #b86b7bff;
      color: #fff;
      transform: scale(1.06);
    }
    @keyframes fadeInNext {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    /* Level toggle button (floating on the right) */
    .level-btn {
      position: fixed;
      right: 1rem;
      background: #e3b1d9ff; /* pastel pink */
      color: #571d2aff;
      border: none;
      padding: 0.6rem 0.9rem;
      border-radius: 6px;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0,0,0,0.12);
      font-size: 1rem;
      margin-bottom: 0.7rem;
      z-index: 10;
      transition: background 0.2s, color 0.2s, transform 0.12s;
    }
    .level-btn.level2 {
      top: 6rem;
    }
    .level-btn.level3 {
      top: 8.5rem;
    }
    .level-btn.active, .level-btn.level3.active {
      background: #e3b1d9ff;
      color: #571d2aff;
      font-weight: 700;
      transform: scale(1.06);
    }
  </style>
</head>
<body>
  <button id="level2Btn" class="level-btn level2">Level Two</button>
  <button id="level3Btn" class="level-btn level3">Level Three</button>
  <div class="game-container start-aesthetic" id="startScreen" style="display:flex; flex-direction:column; align-items:flex-start; gap:1.2rem; background: #515170ff;">
    <h1 style="font-size:2.1rem; font-weight:900; color:#181828; margin-bottom:0.2rem; letter-spacing:1px; text-shadow:0 2px 12px rgba(76,64,101,0.10);">Welcome to Code Identify!</h1>
    <ul style="list-style:none; padding:0; margin:0 0 1.2rem 0; color:#232336;">
      <li style="margin-bottom:0.7rem; font-size:1.13rem; font-weight:500;">• Test your skills by matching code snippets to their language.</li>
      <li style="margin-bottom:0.7rem; font-size:1.13rem; font-weight:500;">• Each round, a code snippet appears.</li>
      <li style="margin-bottom:0.7rem; font-size:1.13rem; font-weight:500;">• Choose the correct language from the options.</li>
      <li style="margin-bottom:0.7rem; font-size:1.13rem; font-weight:500;">• Try to get as many correct as you can!</li>
    </ul>
    <button class="option-btn start-btn-aesthetic" id="startBtn" style="font-size:1.18rem; padding:0.95rem 2.5rem; font-weight:700; background: #978ec8ff; color:#fff; border:none; border-radius:10px; box-shadow:0 2px 12px rgba(76,64,101,0.10); transition:background 0.2s,transform 0.15s; align-self:center;">Start Game</button>
  </div>

  <div id="game-container">
  <button id="toggleStatsBtn" class="option-btn" style="margin-bottom:0.7em; background:#e3b1d9ff; color:#571d2aff; font-weight:600;">Show Stats</button>
  <div id="stats-container" style="display:none;"></div>
    <div class="game-flex-row">
      <div class="game-container" id="gameContainer" style="display:none;">
        <div id="progressBarContainer" style="width:100%; margin-bottom:1.2rem;">
          <div style="font-size:1.05rem; color:#4c4065ff; font-weight:600; margin-bottom:0.3rem;">Progress: <span id="progressText">0 / 15</span></div>
          <div style="background: #c2c2e2ff; border-radius:8px; width:100%; height:18px; overflow:hidden;">
            <div id="progressBar" style="background:linear-gradient(90deg,#9797d4 60%,#4c4065 100%); height:100%; width:0%; border-radius:8px; transition:width 0.3s;"></div>
          </div>
        </div>
        <h2 style="color:#4c4065ff;">Code Identify Game</h2>
        <div class="code-block" id="codeBlock">Loading...</div>
        <div class="options-bar" id="optionsBar"></div>
        <div class="result-message" id="resultMessage"></div>
        <button class="next-btn" id="nextBtn">Next</button>
      </div>
      <div class="explanation-panel" id="explanationPanel"></div>
    </div>
  </div>

  <div class="game-container start-aesthetic" id="levelCompleteScreen" style="display:none; flex-direction:column; align-items:center; justify-content:center; min-height:220px; background: #515170ff !important;">
    <h2 id="levelCompleteTitle" style="color: #181828; margin-bottom:1.2rem;">Level Complete!</h2>
    <p id="levelCompleteMsg" style="font-size:1.15rem; color:#232336; margin-bottom:1.5rem;">You answered 15 questions correctly!<br>Click below to go to the next level.</p>
    <button class="option-btn" id="nextLevelBtn" style="font-size:1.1rem; padding:0.8rem 2.2rem;">Go to Next Level</button>
  </div>

  </div>
  <script>
    // Add explanations for each snippet
    const codeSnippets = [
      {
        code: `body {\n  background: #222;\n  color: #fff;\n}`,
        lang: 'CSS',
        explanation: 'This is a CSS code block that sets the background color to dark and the text color to white for the entire page. It uses selectors (`body`) and curly braces `{}` to apply style rules. The snippet sets the background color of the entire page to a dark gray (`#222`) and the text color to white (`#fff`). The colon `:` separates property names (like background, color) from their values, and the semicolon `;` ends each declaration.'
      },
      // Additional Level 1 beginner snippets (added to increase pool size)
      {
        code: `<p>Hello, world!</p>`,
        lang: 'HTML',
        explanation: 'Simple HTML paragraph element. It uses tags wrapped in angle brackets `< >`. The `<p>` and `</p>` tags define a paragraph element. The text "Hello, world!" is placed between the opening and closing tags, which is the standard structure of HTML.'
      },
      {
        code: `# This is a comment in Python\nprint('Hello')`,
        lang: 'Python',
        explanation: 'A Python comment followed by a print statement. It uses the `#` symbol for comments and the built-in `print()` function. The `#` tells the interpreter to ignore that line, while `print()` outputs the string "Hello". Python does not use semicolons or curly braces, which distinguishes it from languages like JavaScript or C.'
      },
      {
        code: `const name = 'Sam';\nconsole.log('Hi ' + name);`,
        lang: 'Javascript',
        explanation: 'Declares a JS variable and logs a greeting. It uses the `const` keyword for declaring a variable, and the `console.log()` function to print to the browser console. The `+` operator concatenates strings. JavaScript syntax requires semicolons (optional but standard) and uses curly braces in larger code blocks.'
      },
      {
        code: `- item one\n- item two\n- item three`,
        lang: 'Markdown',
        explanation: 'A simple Markdown bulleted list. It uses a leading dash `-` to create unordered list items. Markdown syntax is plain text designed for easy formatting into HTML. Unlike HTML, no tags are required — just symbols like `-` or `*` at the start of each line.'
      },
      {
        code: `h1 { font-size: 2em; }`,
        lang: 'CSS',
        explanation: 'CSS rule setting font size for h1 elements. It uses a selector (`h1`) and a declaration block `{}`. The property `font-size` is paired with the value `2em`, which scales text relative to the parent size. This style applies specifically to all `<h1>` elements in an HTML document.'
      },
      {
        code: `<a href="/#">Link</a>`,
        lang: 'HTML',
        explanation: 'An HTML anchor link. It uses the `<a>` anchor tag. The `href` attribute specifies the link destination. Opening `<a>` and closing `</a>` tags wrap the text "Link", which is displayed as clickable in a browser.'
      },
      {
        code: `for i in range(3):\n    print(i)`,
        lang: 'Python',
        explanation: 'Python loop that prints numbers 0 through 2. It uses the `for` loop with the built-in `range()` function and indentation for the block. The loop iterates through numbers 0, 1, 2 and prints them. Python relies on colons `:` to start code blocks and indentation instead of curly braces.'
      },
      {
        code: `let total = 0;\nfor (let i=0;i<3;i++) total += i;`,
        lang: 'Javascript',
        explanation: 'Simple JS loop that accumulates a total. It uses the `let` keyword for variable declaration and a C-style `for` loop with parentheses `()` and curly braces `{}`. The code initializes `total` to 0 and accumulates numbers from 0 to 2. The syntax with semicolons and `++` increments is specific to JavaScript (and similar languages).'
      },
      {
        code: "function greet(name) {\n  return 'Hello, ' + name + '!';\n}",
        lang: 'Javascript',
        explanation: 'This JavaScript function takes a name as input and returns a greeting string. It defines a function using the `function` keyword, curly braces `{}`, and the `return` statement. The `+` operator concatenates strings with the variable `name`. Functions like this are fundamental in JavaScript for reusable code.'
      },
      {
        code: `def add(a, b):\n    return a + b`,
        lang: 'Python',
        explanation: 'This Python function adds two numbers and returns the result. It uses the `def` keyword to define a function, a colon `:` to start the block, and indentation to define scope. The `return` statement outputs the sum of `a` and `b`. Python does not require parentheses around blocks, unlike JavaScript.'
      },
      {
        code: `# Welcome to Markdown\n\n- List item 1\n- List item 2`,
        lang: 'Markdown',
        explanation: 'This is a Markdown snippet with a heading and a bulleted list. It starts with `#` for a heading and `-` for bullet points. Markdown uses simple plain-text markers rather than tags or keywords. A single `#` creates a top-level heading, while a dash `-` starts list items.'
      },
      {
        code: `<h1>Hello, world!</h1>\n<p>This is HTML.</p>`,
        lang: 'HTML',
        explanation: 'This HTML snippet displays a heading and a paragraph. Iit uses tags like `<h1>` for a heading and `<p>` for a paragraph. The tags wrap the text, which is how HTML structures content. Opening and closing tags must match, which is part of HTML’s syntax.'
      },
      {
        code: `console.log('JavaScript is fun!');`,
        lang: 'Javascript',
        explanation: 'This JavaScript code prints a message to the browser console. It uses the `console.log()` function, which is built into browsers for debugging. The string "JavaScript is fun!" is enclosed in quotes and output to the console. The semicolon `;` ends the statement.'
      },
      {
        code: `**Bold text** and *italic text*`,
        lang: 'Markdown',
        explanation: 'This Markdown snippet shows how to write bold and italic text. It uses double asterisks `**` for bold and single asterisks `*` for italic. Markdown focuses on readable plain text, and these symbols are specifically part of its syntax for styling text.'
      },
      {
        code: `for (let i = 0; i < 5; i++) {\n  console.log(i);\n}`,
        lang: 'Javascript',
        explanation: 'This JavaScript loop prints numbers 0 to 4 to the console. It uses the `for` loop with initialization, condition, and increment inside parentheses `()`. The loop body is wrapped in curly braces `{}`. It logs numbers 0 through 4 using `console.log()`. The syntax is JavaScript’s standard loop style.'
      },
      {
        code: `print('Hello from Python!')`,
        lang: 'Python',
        explanation: 'This Python code prints a message to the console. It uses the built-in `print()` function with parentheses and no semicolon. The string is in quotes and is printed directly to the console. The absence of extra syntax like braces or semicolons marks it as Python.'
      },
      {
        code: `a {\n  color: blue;\n  text-decoration: underline;\n}`,
        lang: 'CSS',
        explanation: 'This CSS rule styles anchor elements to be blue and underlined. It uses a selector (`a`) to target anchor elements and style them with properties inside `{}`. The `color` property sets text to blue, and `text-decoration: underline;` ensures links are underlined. The colon `:` separates property from value.'
      },
      {
        code: `<ul>\n  <li>Item 1</li>\n  <li>Item 2</li>\n</ul>`,
        lang: 'HTML',
        explanation: 'This HTML snippet creates an unordered list with two items. It uses `<ul>` tags for an unordered list and `<li>` tags for list items. The nested structure with opening and closing tags is the hallmark of HTML document structure.'
      },
      {
        code: `<!-- This is a comment in HTML -->`,
        lang: 'HTML',
        explanation: 'This is how you write a comment in HTML. It uses the `<!-- ... -->` syntax for comments. Anything inside is ignored by the browser. This style of comment is unique to HTML and not used in languages like Python or CSS.'
      },
      {
        code: `/* CSS comment */\n.header {\n  font-size: 2em;\n}`,
        lang: 'CSS',
        explanation: 'This CSS snippet includes a comment and a rule that sets the font size of elements with class header. It includes a `/* ... */` comment and a rule targeting the `.header` class. The `font-size: 2em;` sets text size relative to the base font. CSS uses class selectors with a dot `.` to apply styles to elements with that class.'
      },
      {
        code: `let x = 10;\nlet y = 20;\nlet sum = x + y;`,
        lang: 'Javascript',
        explanation: 'This JavaScript code declares two variables and calculates their sum. t uses the `let` keyword for variable declarations, semicolons `;` to end statements, and the `+` operator to add values. JavaScript syntax requires these features and is executed in browsers or Node.js.'
      },
      {
        code: `## Subheading in Markdown`,
        lang: 'Markdown',
        explanation: 'This Markdown line creates a subheading. It uses two hash symbols `##` at the start of a line to create a subheading. Markdown headings use `#` symbols instead of tags, unlike HTML’s `<h2>` tag.'
      },
      {
        code: `if x > 0:\n    print('Positive')\nelse:\n    print('Non-positive')`,
        lang: 'Python',
        explanation: 'This Python code checks if x is positive and prints a message accordingly. It uses the `if` and `else` keywords with a colon `:` to define conditional blocks. Indentation controls scope instead of braces. The `print()` function outputs whether `x` is positive or not, showing Python’s clean, readable style.'
      }
    ];
    const languages = ['CSS', 'Javascript', 'Python', 'Markdown', 'HTML'];
    let currentSnippet = null;
    // Add explanations for level three as well
    const levelThreeSnippets = [
      { code: "fetch('/api/data').then(res => res.json()).then(d => console.log(d));", lang: 'Javascript', explanation: 'This is JavaScript because it uses the "fetch" API and Promises with "then" syntax, which are specific to JS. It fetches data from a URL, converts the response to JSON using res.json(), and logs the resulting data to the console. "fetch" is an asynchronous function in JS, and "then" chains the actions after the promise resolves.' },
      { code: "const [a,b] = arr; const result = a.map(x => x*2).filter(Boolean);", lang: 'Javascript', explanation: 'This is JavaScript because it uses "const" for variable declaration, array destructuring "[a,b]", and array methods "map" and "filter". It extracts two elements from the array "arr", doubles each element of "a" using "map", and removes falsy values using "filter(Boolean)". These are standard JS array operations.' },
      { code: "let nums = [1,2,3]; let doubled = nums.reduce((a,b)=>a.concat(b*2),[]);", lang: 'Javascript', explanation: 'This is JavaScript because it uses "let" declarations, array literal "[1,2,3]", and the "reduce" method with an arrow function. It iterates through the array "nums", doubles each element "b", and accumulates them into a new array "doubled". The "=>" syntax and "reduce" method are unique to JS.' },
      { code: "for (let i=0;i<10;i++){if(i%2===0)console.log(i)}", lang: 'Javascript', explanation: 'This is JavaScript because it uses "for" loop syntax, "let" declarations, strict equality "===" and console logging with console.log(). The loop iterates i from 0 to 9, and prints only even numbers (i%2===0). These structures and console methods are specific to JS.' },
      { code: "name, score\nWHERE score > 100\nORDER BY score DESC;", lang: 'Python', explanation: 'This is labeled Python for the game, even though it resembles a SQL query. In the game context, it is considered Python. The "WHERE" clause filters records where score > 100, and "ORDER BY score DESC" sorts them in descending order. The snippet illustrates how Python code might include SQL-like string expressions.' },
      { code: "a,b=0,1\nfor _ in range(n):\n    a,b=b,a+b\nreturn a", lang: 'Python', explanation: 'This is Python because it uses tuple unpacking "a,b=0,1", "for" loops with "range()", indentation to define block scope, and "return" to return a value. It calculates the nth Fibonacci number by updating "a" and "b" in each iteration.' },
      { code: "s == s[::-1]", lang: 'Python', explanation: 'This is Python because it uses slicing "s[::-1]" and the equality operator "==". The code checks if the string "s" is equal to its reverse. Slicing with "[::-1]" is a Python-specific feature for reversing sequences.' },
      { code: "with open('file.txt') as f:\n    data = f.read()", lang: 'Python', explanation: 'This is Python because it uses the "with" statement for context management, "open()" to open files, and indentation to define the block. It reads the contents of "file.txt" into the variable "data" safely, automatically closing the file afterwards.' },
      { code: "<section><article><h2>Title</h2><p>Content here</p></article></section>", lang: 'HTML', explanation: 'This is HTML because it uses angle-bracket tags "<>" to define elements. The code defines a semantic section, an article inside it, a heading <h2>, and a paragraph <p>. HTML uses this markup syntax to structure web content.' },
      { code: "<form><input type='text' /><button>Go</button></form>", lang: 'HTML', explanation: 'This is HTML because it defines a form element with an input field and a button. The "<form>" tag groups inputs, "<input type=\'text\'>" creates a text box, and "<button>" defines a clickable button. Angle-bracket markup identifies this as HTML.' },
      { code: "<ul>\n  <li>One</li>\n  <li>Two</li>\n</ul>", lang: 'HTML', explanation: 'This is HTML because it uses "<ul>" for an unordered list and "<li>" for list items. The structure and tags are HTML-specific syntax for lists.' },
      { code: "@media (min-width: 600px) { .col { display: grid; grid-template-columns: 1fr 2fr; } }", lang: 'CSS', explanation: 'This is CSS because it uses a media query "@media" and styling rules inside curly braces. It applies a grid layout to elements with class ".col" when the screen width is at least 600px. Selectors, properties, and values are CSS-specific syntax.' },
      { code: ".container { display: flex; flex-wrap: wrap; }", lang: 'CSS', explanation: 'This is CSS because it uses a class selector ".container" and declares style rules with curly braces. "display: flex" makes it a flex container, and "flex-wrap: wrap" allows child elements to wrap. The structure of "selector { property: value; }" is CSS-specific.' },
      { code: "#main { padding: 2em; border: 1px solid #ccc; }", lang: 'CSS', explanation: 'This is CSS because it uses an ID selector "#main" and style declarations inside braces. It adds 2em padding and a 1px solid border. The use of selectors, properties, and values in braces is how CSS styles HTML elements.' },
      { code: "- [x] Task done\n- [ ] Task todo\n\nSome **notes** here.", lang: 'Markdown', explanation: 'This is Markdown because it uses "-" for list items, "[x]" and "[ ]" for checked/unchecked tasks, and "**" for bold text. Markdown syntax uses simple text symbols to format content, unlike HTML or code.' },
      { code: "1. First\n2. Second\n3. Third", lang: 'Markdown', explanation: 'This is Markdown because it uses numbers followed by a period for an ordered list. Each line represents a list item, which is rendered as a numbered list in Markdown.' },
      { code: "> Blockquote example\n> More text", lang: 'Markdown', explanation: 'This is Markdown because it uses ">" to create blockquotes. Each line starting with ">" is treated as a quoted section. Markdown interprets these symbols for formatting.' },
      { code: "def foo():\n    pass", lang: 'Markdown', explanation: 'This is a Python function labeled as Markdown for the game. It uses "def" to define the function, a colon to start the block, and indentation with "pass" as a placeholder. The syntax is clearly Python, but it is included as a tricky Markdown example.' }
    ];
    // mode-aware random snippet selector: prefers levelThree if enabled
    function getRandomSnippet() {
      if (typeof levelThreeMode !== 'undefined' && levelThreeMode) {
        return levelThreeSnippets[Math.floor(Math.random() * levelThreeSnippets.length)];
      }
      return codeSnippets[Math.floor(Math.random() * codeSnippets.length)];
    }
    function showSnippet() {
      currentSnippet = getRandomSnippet();
      document.getElementById('codeBlock').textContent = currentSnippet.code;
      document.getElementById('resultMessage').textContent = '';
      document.getElementById('nextBtn').classList.remove('show');
      hideExplanation();
      renderOptions();
    }
    function renderOptions() {
      const optionsBar = document.getElementById('optionsBar');
      optionsBar.innerHTML = '';
      languages.forEach(lang => {
        const btn = document.createElement('button');
        btn.className = 'option-btn';
        btn.textContent = lang;
        btn.onclick = () => checkAnswer(lang);
        optionsBar.appendChild(btn);
      });
    }
    // Progress tracking
    let correctCount = 0;
    let currentLevel = 1; // 1, 2, 3
    function updateProgressBar() {
      const pct = Math.min(100, Math.round((correctCount/15)*100));
      document.getElementById('progressBar').style.width = pct + '%';
      document.getElementById('progressText').textContent = `${correctCount} / 15`;
    }
    function resetProgress() {
      correctCount = 0;
      updateProgressBar();
    }
    function checkAnswer(selected) {
      const result = document.getElementById('resultMessage');
      const correctLanguage = currentSnippet.lang;
      if (selected === correctLanguage) {
        result.textContent = 'Correct!';
        result.className = 'result-message correct';
        document.getElementById('nextBtn').classList.add('show');
        correctCount++;
        updateProgressBar();
        languageStats[correctLanguage].correct++;
        showExplanation(currentSnippet.explanation);
        if (correctCount >= 15) {
          setTimeout(showLevelComplete, 500);
        }
      } else {
        result.textContent = 'Try again!';
        result.className = 'result-message incorrect';
        languageStats[selected].incorrect++;
        hideExplanation();
      }
      updateStatsDisplay();
    }
    function showExplanation(text) {
      const panel = document.getElementById('explanationPanel');
      panel.textContent = text || '';
      panel.classList.add('show');
    }
    function hideExplanation() {
      const panel = document.getElementById('explanationPanel');
      panel.textContent = '';
      panel.classList.remove('show');
    }
    function showLevelComplete() {
      document.getElementById('gameContainer').style.display = 'none';
      document.getElementById('levelCompleteScreen').style.display = 'flex';
      let title = 'Level Complete!';
      let msg = '';
      let btn = document.getElementById('nextLevelBtn');
      if (currentLevel === 1) {
        title = 'Level 1 Complete!';
        msg = 'You answered 15 questions correctly!<br>Click below to go to Level 2.';
        btn.textContent = 'Go to Level 2';
      } else if (currentLevel === 2) {
        title = 'Level 2 Complete!';
        msg = 'Great job!<br>Click below to go to Level 3.';
        btn.textContent = 'Go to Level 3';
      } else {
        title = 'Level 3 Complete!';
        msg = 'You finished all levels!<br>Refresh to play again.';
        btn.style.display = 'none';
      }
      document.getElementById('levelCompleteTitle').textContent = title;
      document.getElementById('levelCompleteMsg').innerHTML = msg;
    }
    document.getElementById('nextBtn').onclick = showSnippet;
  // advancedMode: when true remove explicit language-word hints from displayed snippets
  let advancedMode = false;
  let levelThreeMode = false;
  const level2Btn = document.getElementById('level2Btn');
  const level3Btn = document.getElementById('level3Btn');
    function sanitizeForAdvanced(code) {
      // remove occurrences of explicit language names to make identification harder
      return code.replace(/\b(JavaScript|Javascript|Python|HTML|CSS|Markdown)\b/gi, '').trim();
    }
    function showSnippetAdvanced() {
      currentSnippet = getRandomSnippet();
      let displayCode = currentSnippet.code;
      // Level Three snippets are selected from a different pool; always sanitize if advancedMode or levelThreeMode
      if (advancedMode || levelThreeMode) displayCode = sanitizeForAdvanced(displayCode);
      document.getElementById('codeBlock').textContent = displayCode;
      document.getElementById('resultMessage').textContent = '';
      document.getElementById('nextBtn').classList.remove('show');
      hideExplanation();
      renderOptions();
    }
    function showSnippet() {
      // keep backward compatible: prefer advanced-aware function
      showSnippetAdvanced();
    }
    level2Btn.addEventListener('click', () => {
      // toggle Level Two advanced mode; if Level Three is active, ignore Level Two toggles
      if (levelThreeMode) {
        // if level three is active, toggle it off and enable Level Two
        levelThreeMode = false;
        level3Btn.classList.remove('active');
        level3Btn.textContent = 'Level Three';
      }
      advancedMode = !advancedMode;
      level2Btn.classList.toggle('active', advancedMode);
      level2Btn.textContent = advancedMode ? 'Level Two (on)' : 'Level Two';
      // immediately show a fresh snippet in the selected mode
      showSnippet();
    });
    level3Btn.addEventListener('click', () => {
      // Level Three takes precedence: it switches to a harder snippet pool
      levelThreeMode = !levelThreeMode;
      if (levelThreeMode) {
        // enable advanced sanitization for Level Three
        advancedMode = true;
        level2Btn.classList.remove('active');
        level2Btn.textContent = 'Level Two';
      }
      level3Btn.classList.toggle('active', levelThreeMode);
      level3Btn.textContent = levelThreeMode ? 'Level Three (on)' : 'Level Three';
      showSnippet();
    });
    // Only show the start screen on load
    window.onload = function() {
      document.getElementById('startScreen').style.display = 'flex';
      document.getElementById('gameContainer').style.display = 'none';
      document.getElementById('levelCompleteScreen').style.display = 'none';
      currentLevel = 1;
      resetProgress();
      updateStatsDisplay(); // Ensure stats are rendered at least once
    };
    // Start button logic: hide start, show game, start game
    document.getElementById('startBtn').onclick = function() {
      document.getElementById('startScreen').style.display = 'none';
      document.getElementById('gameContainer').style.display = 'block';
      document.getElementById('levelCompleteScreen').style.display = 'none';
      currentLevel = 1;
      resetProgress();
      updateStatsDisplay(); // Ensure stats are rendered when game starts
      showSnippet();
    };
    // Next level button logic
    document.getElementById('nextLevelBtn').onclick = function() {
      document.getElementById('levelCompleteScreen').style.display = 'none';
      document.getElementById('gameContainer').style.display = 'block';
      resetProgress();
      currentLevel++;
      // Set mode for next level
      if (currentLevel === 2) {
        advancedMode = true;
        level2Btn.classList.add('active');
        level2Btn.textContent = 'Level Two (on)';
        levelThreeMode = false;
        level3Btn.classList.remove('active');
        level3Btn.textContent = 'Level Three';
      } else if (currentLevel === 3) {
        levelThreeMode = true;
        level3Btn.classList.add('active');
        level3Btn.textContent = 'Level Three (on)';
        advancedMode = true;
        level2Btn.classList.remove('active');
        level2Btn.textContent = 'Level Two';
      }
      showSnippet();
    };
    let currentQuestion = 0;
    let score = 0;
    // Track correct/incorrect counts per language
    const languageStats = {};
    languages.forEach(lang => {
      languageStats[lang] = { correct: 0, incorrect: 0 };
    });
    function updateStatsDisplay() {
      let statsHtml = '<div id="language-stats" style="margin-bottom:1em;">';
      statsHtml += '<h3>Language Stats</h3>';
      statsHtml += '<table style="width:100%;text-align:center;border-collapse:collapse;">';
      statsHtml += '<tr><th>Language</th><th>Correct</th><th>Incorrect</th></tr>';
      languages.forEach(lang => {
        statsHtml += `<tr><td>${lang}</td><td>${languageStats[lang].correct}</td><td>${languageStats[lang].incorrect}</td></tr>`;
      });
      statsHtml += '</table></div>';
      document.getElementById('stats-container').innerHTML = statsHtml;
    }
    // Toggle stats button logic
    const statsContainer = document.getElementById('stats-container');
    const toggleStatsBtn = document.getElementById('toggleStatsBtn');
    toggleStatsBtn.onclick = function() {
      if (statsContainer.style.display === 'none' || statsContainer.style.display === '') {
        statsContainer.style.display = 'block';
        toggleStatsBtn.textContent = 'Hide Stats';
      } else {
        statsContainer.style.display = 'none';
        toggleStatsBtn.textContent = 'Show Stats';
      }
    };
    function showQuestion() {
        updateStatsDisplay();
        currentSnippet = getRandomSnippet();
        document.getElementById('codeBlock').textContent = currentSnippet.code;
        document.getElementById('resultMessage').textContent = '';
        document.getElementById('nextBtn').classList.remove('show');
        renderOptions();
    }
    // (removed duplicate checkAnswer) 
  </script>
</body>
</html>
