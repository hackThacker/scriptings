# Introduction to JavaScript

During this program, we will be covering the basics of the programming language JavaScript.

The main purpose of this language is to implement interactivity into webpages and web applications, but thanks to the millions of individuals in the community, we've been able to control more than just the interactivity of web pages.  
Thanks to the community, we can now use JavaScript to control servers, create video games, code mobile applications, and can even be used for cybersecurity in some scenarios.

## Topics Covered:
- [JavaScript Basics](#javascript-basics)
- [Variables](#variables)
- [Conditionals](#conditionals)
- [Functions](#functions)
- [Objects and Arrays](#objects-and-arrays)
- [loops](#loops-in-programming)
- [DOM (Document Object Model)](#comprehensive-guide-to-dom-document-object-model-in-javascript)
- [XSS (Cross-Site Scripting)](#cross-site-scripting-xss-vulnerabilities)



## Prerequisites

Here is what you'll need before beginning this room:
- IDE or Text Editor of your choice (I recommend VS Code or Atom)



### Final Note

This room will not cover everything JavaScript can do, not even close. This room will be targeted towards beginners who are looking to learn basic programming logic and an easy-to-use, versatile language for obtaining a better understanding of how the web works.  
Remember to take your time and read carefully. Enjoy the learning and have fun learning about JavaScript!


---

# JavaScript Basics

Before diving into JavaScript, here are a few things to remember as we traverse through the room:

- Using `//` within your IDE or text editor are considered comments. Use this to take notes directly in your JS file. **Always take notes!**
- We will be using **Chrome dev tools** for this room, so for this, we'll need to link our JavaScript file to an HTML file. We will not be covering much HTML in this room, but you can easily link your JavaScript file by using a `<script>` element. Here’s an example:

```html
<body>
  <script src="script.js"></script>
</body>
```

Remember to put the script tag right before the closing `</body>` tag. This way, your HTML code will execute before your external JavaScript document. There are instances where it’s better to place the script in the `<head>` tag or a certain order when working with multiple documents, but for this room, we will only focus on the basics.

---

## Variables

There are 3 types of variables in JavaScript: `var`, `let`, and `const`.

- **`var`**: The original variable type in JavaScript, but it is now generally replaced by `let` and `const` due to some drawbacks. It's still used and works in modern JavaScript applications. This variable can be updated and re-declared.
- **`let`**: This is the ideal variable type if the variable will be reassigned later within the application.
- **`const`**: Use this if the variable will never change or won’t be reassigned anywhere else in the application.

### Quick Overview:
- **`var`**: It’s globally scoped and can be updated and re-declared.
- **`let`**: It’s block-scoped, meaning it is accessible only within the block, and can be updated but not re-declared.
- **`const`**: It’s block-scoped and cannot be updated or re-declared.

### Example:
```javascript
var variableOne = 'Linus Torvalds';
let variableTwo = 50;
const variableThree = 'Creator of the Linux Kernel';
```

### Scopes:
- **Global Scope**: A variable declared outside a function. This means all scripts and functions on a web application or webpage can access this variable.
- **Block Scope**: A variable declared inside a block (e.g., loops, if statements) is only accessible within that block.

---

## Data Types in Variables

Main data types that you can store within a variable:
| Data Type  | Example |
|------------|---------|
| Number     | `200`   |
| String     | `'Neo'` |
| Boolean    | `true` or `false` |

There are also arrays, objects, and many other data types that we will touch upon during this room.

---

## Operators

### Arithmetic Operators

| Operator | Type        | What It Does                                   | Example                |
|----------|-------------|------------------------------------------------|------------------------|
| `+`      | Addition    | Adds numbers or strings together               | `25 + 5 = 30`          |
| `++`     | Increment   | Increases the variable's number by 1           | `let x = 20; x++; x = 21` |
| `-`      | Subtraction | Subtracts the variable's numbers               | `15 - 5 = 10`          |
| `--`     | Decrement   | Decreases the variable's number by 1           | `let x = 20; x--; x = 19` |
| `*`      | Multiplication | Multiplies one number by another            | `5 * 10 = 50`          |
| `/`      | Division    | Divides one number by another                  | `100 / 10 = 10`        |
| `%`      | Modulus     | Returns remainder of division operation       | `100 % 8 = 4`          |

---

### Comparison Operators

| Operator | What It Does              | Example        |
|----------|---------------------------|----------------|
| `==`     | Equal to                  | `100 == 100`   |
| `===`    | Equal to & identical      | `500 === 500`  |
| `!=`     | Not equal to              | `100 != 50`    |
| `!==`    | Not identical             | `35 !== 75`    |
| `<`      | Less than                 | `5 < 85`       |
| `<=`     | Less than or equal to     | `60 <= 90`     |
| `>`      | Greater than              | `30 > 5`       |
| `>=`     | Greater than or equal to  | `1,000 >= 900` |

These two tables cover the majority of what we will be going over moving forward. However, there are still many more operators to explore. Once you finish learning the basics of JavaScript, I recommend researching more about operators, including **boolean operators** (true or false) and **logical operators** (AND, OR, NOT).

---

## Additional Data Types

Here are a few additional data types you will be using:

- **Strings**: `'Morpheus'`
- **Arrays**: `[1, 2, 3]`
- **Objects**: `{Name: 'John', Occupation: 'Master Hacker'}`
- **Booleans**: `true` or `false`
- **Numbers**: `455`
- **Floating-Point Numbers**: `10.5`

---

## Conditionals

Welcome to Conditionals!

### Example:
```javascript
if (5 === 5) {
  console.log('Hello World!'); // Prints Hello World! to the console
}
```

In plain English, if a condition is met, then the code will run. Remember all those operators we learned about in the first task? We can use those to define these conditions and plan our approach.

There are also `else if` statements, which look like this:

```javascript
if (5 === 10) {
  console.log('Hello World!'); // Skips this code
} else if (10 === 10) {
  console.log('Hello World!'); // Prints Hello World! to the console
}
```

This way we can have multiple conditions before our code executes. Normally, we'd end our code with an `else` statement like this:

```javascript
if (5 === 10) {
  console.log('Hello World!'); // Skips this code
} else if (10 === 10) {
  console.log('Hello World!'); // Prints Hello World! to the console
} else {
  console.log('ERROR ERROR ERROR');
}
```

Basically, the `else` keyword concludes our `if` conditional. We'll learn a better way of writing conditionals later, but for now, this is a clear way of using a condition to return a result.

---

## Switch Cases

If you need to test multiple conditions, then most of the time **switch cases** are best for optimization and readability within your code. `If`, `else if`, `else` statements and `switch` cases can both do similar tasks, but `switch` cases are better for performing multiple different conditions. Here's how a `switch` case looks:

```javascript
const animal = 3;

switch (animal) {
  case 1:
    document.write('Cow');
    break;
  case 2:
    document.write('Chicken');
    break;
  case 3:
    document.write('Monkey');
    break;
  default:
    document.write('Animal?');
} // Outputs Monkey
```

## Functions

Functions are one of the most vital parts of programming. Due to how important functions are, there will be a lot of things we don't cover, but remember that functions are going to be vital to any applications you write.

*ECMAScript 6* is the most popular version of JavaScript. There are a lot of important differences between ES5 and ES6, we focus mainly on ES6 in this room, but knowing past versions can help improve your knowledge of the language and logic of JavaScript.

### This is a function in ES6 (ECMAScript 6):

```javascript
const func = (a, b) => {
    let nums = a * b;
    console.log(nums); // Outputs 250
}

func(25, 10);
```

### ES5:

```javascript
function func(a, b) { // Everything inside of the parenthesis defines our parameter(s)
    let nums = a * b;
    console.log(nums); // Outputs 250
}

func(25, 10);
```


## Objects and Arrays

Learning about Objects and Arrays are heavy subjects, but let's try to break them into easy-to-understand sections.

### Objects

The most important thing about objects is to remember that they're just another variation of variables. Here is a quick example of an object:

```javascript
var choosePill = {
    pillOne: 'Red',
    pillTwo: 'Blue'
}
```

I know we've already used millions of tables, but they're the best way to learn! So, here's a table displaying the code object we just wrote:

| Property      | Stored Value |
|---------------|--------------|
| pillOne       | Red          |
| pillTwo       | Blue         |

Even though we only stored strings (you can remember strings based on the quotations), we can also store numbers. Here is our same code, updated:

```javascript
var choosePill = {
    pillOne: 'Red',
    pillTwo: 'Blue',
    numberOfPills: 2
}
```

```javascript
var choice = choosePill.pillOne; // This will access the object's property
```

| Property      | Stored Value |
|---------------|--------------|
| pillOne       | Red          |
| pillTwo       | Blue         |
| numberOfPills | 2            |

---

### Arrays

Arrays are fairly similar to objects. They have different stored values and syntax but can be used for almost anything.

Here is the same code from before, but in an array:

```javascript
var choosePill = ['Red', 'Blue', 2];

var choice = choosePill[0];

console.log(choice); // Outputs 'Red'
```

**Reminder:** Most programming languages start from 0, not 1. So, when we access the `choosePill` variable, we grab the value from the 1st position.

Arrays are extremely important when storing multiple values within a variable. This way, we don't have to write 100 variables and instead can store them all in a single variable. This is an array. There are multiple ways to write an array, but the simplest and most basic version is the example above.

---

### Quick Challenge

What is the output of this code (Question #3)?

```javascript
var mrRobot = ['Elliot', 'Angela', 'Tyrell', 'Darlene'];

let character = mrRobot[2];

console.log(character); // What is the output?
```

---

# Loops in Programming

Loops can be a bit tricky, but they are an essential concept in programming. There are several types of loops in most programming languages: `for` loops, `while` loops, and `do...while` loops. Let's break down the basic logic behind them with some simple examples.

## For Loop

A `for` loop is commonly used when you know in advance how many times you want to execute a statement or a block of code.

### Syntax:

```javascript
for (initialization; condition; increment) {
    // Code to execute
}
```

### Example:

```javascript
for (let a = 1; a <= 10; a++) {
    console.log(`Number: ${a}`); // Outputs numbers 1-10 in the console
}
```

### Breaking It Down:

- **Initialization (`a = 1`)**: This runs before the loop starts and sets up the loop's counter (in this case, `a` is initialized to 1).
- **Condition (`a <= 10`)**: The loop continues as long as this condition is true. If the condition becomes false, the loop ends.
- **Increment (`a++`)**: This runs after each iteration of the loop and increases the counter (in this case, `a` is incremented by 1).

**Important Note**: Each part of the `for` loop is separated by a semicolon. You can also use multiple initializations or increments if needed, just separate them with commas.

### Example with Multiple Variables:

```javascript
for (let a = 1, b = 2; a <= 5; a++, b++) {
    console.log(`a: ${a}, b: ${b}`);
}
```

---

## While Loop

A `while` loop is used when you want to keep executing code as long as a certain condition is true. The condition is checked before each iteration.

### Syntax:

```javascript
while (condition) {
    // Code to execute
}
```

### Example:

```javascript
let x = 0;

while (x <= 3) {
    console.log(x++); // Prints 0, 1, 2, 3
}
```

### How It Works:

- The loop continues to run as long as the condition (`x <= 3`) is true.
- After each iteration, `x` is incremented by 1 (`x++`), and the loop re-checks the condition.
- **Important Warning**: Be careful of infinite loops! If the condition never becomes false, the loop will continue indefinitely, which can cause issues in your program.

---

## Do...While Loop

A `do...while` loop is different from the other loops because it executes the code block *before* checking the condition. This ensures that the code will run at least once, even if the condition is false.

### Syntax:

```javascript
do {
    // Code to execute
} while (condition);
```

### Example:

```javascript
let c = 10;

do {
    console.log(c++); // Outputs 10, 11, 12, ..., until 50
} while (c <= 50);
```

### How It Works:

- The code inside the `do` block executes first.
- After that, the condition (`c <= 50`) is checked. If true, the loop continues. If false, the loop stops.
- This type of loop is useful when you want the code to run at least once, regardless of the condition.

---

## Summary

Loops are a fundamental part of programming and are used to repeat a block of code multiple times. The three main types of loops are:

- **For Loop**: Used when you know exactly how many times you want to loop.
- **While Loop**: Used when you want to loop as long as a certain condition is true.
- **Do...While Loop**: Similar to the `while` loop but guarantees that the code will run at least once.

Loops have various variations and can behave differently based on the condition you set, but the basic concept remains the same across all programming languages. Understanding loops and how they work will greatly improve your ability to write efficient and effective code.

---



# Comprehensive Guide to DOM (Document Object Model) in JavaScript

The Document Object Model (DOM) represents the structure of an HTML document and provides methods to interact with and manipulate the content and structure of a webpage. This guide will cover everything from basic to advanced DOM manipulation concepts in JavaScript.

---

## 1. **DOM Basics**

### 1.1. **Selecting Elements**

To interact with HTML elements, we need to first select them using DOM methods.

#### **`getElementById`**

Grabs an element by its **ID**.

```javascript
const element = document.getElementById('myElement');
```

#### **`getElementsByClassName`**

Grabs elements by their **class name**. It returns a live HTMLCollection.

```javascript
const elements = document.getElementsByClassName('myClass');
```

#### **`getElementsByTagName`**

Grabs elements by their **tag name**. Returns an HTMLCollection.

```javascript
const divs = document.getElementsByTagName('div');
```

#### **`querySelector`**

Grabs the first element that matches a CSS selector.

```javascript
const element = document.querySelector('.myClass');
```

#### **`querySelectorAll`**

Grabs all elements that match a CSS selector. Returns a NodeList.

```javascript
const elements = document.querySelectorAll('div');
```

### 1.2. **Manipulating Elements**

Once you've selected an element, you can manipulate its content, style, or attributes.

#### **Change Text Content**

```javascript
const element = document.getElementById('myElement');
element.textContent = "New Text!";
```

#### **Change HTML Content**

```javascript
const element = document.getElementById('myElement');
element.innerHTML = "<strong>Bold Content</strong>";
```

#### **Change CSS Styles**

```javascript
const element = document.getElementById('myElement');
element.style.backgroundColor = "yellow";
```

---

## 2. **DOM Events**

Events are actions that occur due to user interaction or system processes, such as clicks, mouse movements, or page loading.

### 2.1. **Common Events**

#### **`onclick`**

Triggered when an element is clicked.

```javascript
const button = document.getElementById('myButton');
button.onclick = function() {
    alert('Button clicked!');
};
```

#### **`onmouseover`**

Triggered when the mouse pointer hovers over an element.

```javascript
const element = document.getElementById('myElement');
element.onmouseover = function() {
    element.style.backgroundColor = 'lightblue';
};
```

#### **`onload`**

Triggered when a page or an image has finished loading.

```javascript
window.onload = function() {
    alert('Page loaded!');
};
```

#### **`onfocus` and `onblur`**

Triggered when an element gains or loses focus (typically used with form elements).

```javascript
const input = document.getElementById('myInput');
input.onfocus = function() {
    input.style.border = '2px solid green';
};
input.onblur = function() {
    input.style.border = '';
};
```

---

## 3. **Event Listeners**

Event listeners provide a more flexible way to attach events to elements. They also allow multiple event listeners to be attached to the same element.

### 3.1. **Adding an Event Listener**

```javascript
const button = document.getElementById('myButton');
button.addEventListener('click', function() {
    alert('Button clicked!');
});
```

### 3.2. **Removing an Event Listener**

```javascript
function showMessage() {
    alert('Button clicked!');
}

const button = document.getElementById('myButton');
button.addEventListener('click', showMessage);

// To remove the event listener
button.removeEventListener('click', showMessage);
```

---

## 4. **DOM Traversing**

Traversing allows you to move between elements in the DOM tree.

### 4.1. **Parent Node**

```javascript
const child = document.getElementById('myElement');
const parent = child.parentNode;
```

### 4.2. **Child Nodes**

```javascript
const parent = document.getElementById('parentElement');
const children = parent.childNodes;
```

### 4.3. **Next and Previous Sibling**

```javascript
const element = document.getElementById('myElement');
const nextSibling = element.nextSibling;
const previousSibling = element.previousSibling;
```

---

## 5. **Creating and Removing Elements**

You can dynamically create, insert, or remove elements using JavaScript.

### 5.1. **Create New Elements**

```javascript
const newDiv = document.createElement('div');
newDiv.textContent = 'Hello, World!';
document.body.appendChild(newDiv);
```

### 5.2. **Remove Elements**

```javascript
const element = document.getElementById('myElement');
element.remove();
```

### 5.3. **Insert Elements**

```javascript
const newDiv = document.createElement('div');
newDiv.textContent = 'New Element';
const parent = document.getElementById('parentElement');
parent.insertBefore(newDiv, parent.firstChild);
```

---

## 6. **Advanced DOM Manipulation**

### 6.1. **Cloning Elements**

You can clone an element and insert it elsewhere in the DOM.

```javascript
const original = document.getElementById('myElement');
const clone = original.cloneNode(true);  // `true` for deep cloning
document.body.appendChild(clone);
```

### 6.2. **Event Delegation**

Event delegation allows you to handle events on dynamically created elements.

```javascript
document.getElementById('parent').addEventListener('click', function(event) {
    if (event.target && event.target.matches('button.classname')) {
        alert('Button clicked!');
    }
});
```

### 6.3. **Async DOM Manipulation**

You can use `setTimeout` or `setInterval` to perform delayed DOM manipulations.

```javascript
setTimeout(function() {
    const element = document.getElementById('myElement');
    element.textContent = 'Updated after 2 seconds';
}, 2000);
```

---

## 7. **DOM Manipulation with Form Elements**

### 7.1. **Accessing Form Inputs**

```javascript
const input = document.getElementById('myInput');
const value = input.value;
```

### 7.2. **Changing Form Values**

```javascript
const input = document.getElementById('myInput');
input.value = 'New Value';
```

### 7.3. **Handling Form Submission**

```javascript
const form = document.getElementById('myForm');
form.onsubmit = function(event) {
    event.preventDefault();  // Prevents form submission
    alert('Form submitted!');
};
```

---

## 8. **Performance Considerations**

### 8.1. **Minimize Reflows and Repaints**

Try to make DOM changes efficiently to minimize performance issues.

```javascript
// Bad example: Triggers multiple reflows
element.style.width = '100px';
element.style.height = '100px';
element.style.backgroundColor = 'red';

// Better: Batch changes to minimize reflows
element.style.cssText = 'width: 100px; height: 100px; background-color: red;';
```

### 8.2. **Using `requestAnimationFrame` for Smooth Animations**

```javascript
function animate() {
    const element = document.getElementById('myElement');
    let left = parseInt(element.style.left || 0);
    element.style.left = (left + 5) + 'px';
    if (left < 500) {
        requestAnimationFrame(animate);
    }
}

animate();
```

---

# Cross-Site Scripting (XSS) Vulnerabilities

Cross-Site Scripting (XSS) is a vulnerability that allows attackers to inject malicious scripts into webpages viewed by other users. XSS is one of the most common and dangerous web application vulnerabilities. It allows attackers to execute arbitrary JavaScript in the context of a victim's browser, leading to theft of sensitive data, session hijacking, and more.

There are three main types of XSS:

1. **Stored XSS (Persistent XSS)**
2. **Reflected XSS (Non-Persistent XSS)**
3. **DOM-based XSS (Client-side XSS)**

---

## **1. Stored XSS (Persistent XSS)**

**Stored XSS** occurs when malicious input provided by the attacker is permanently stored on the server, often in a database, and is later reflected back to users who access the stored data. The injected script is executed when the data is viewed or rendered by other users.

### **How it Works**
- An attacker inputs malicious JavaScript into a form or input field that gets stored on the server.
- When another user views the page containing this malicious data, the script is executed in the context of their browser.
  
### **Example:**

Imagine a simple comment system on a blog:

```html
<!-- comment.php -->
<form method="POST" action="comment.php">
  <textarea name="comment" placeholder="Enter your comment"></textarea>
  <button type="submit">Submit</button>
</form>

<div id="comments">
  <!-- Display stored comments here -->
  <p><?php echo $_POST['comment']; ?></p>
</div>
```

If the attacker submits the following comment:

```html
<script>alert('Stored XSS');</script>
```

The comment is stored on the server and is reflected back to every user who views the comment section. When a user views the page, the script is executed, resulting in an alert box displaying "Stored XSS".

### **Preventing Stored XSS:**
1. **Sanitize Input**: Use input validation and sanitize user inputs to remove or escape any harmful characters, such as `<`, `>`, and `script`.
2. **Escape Output**: Ensure that any user-generated content is properly escaped when rendered on the page.
3. **Content Security Policy (CSP)**: Use a CSP to limit the sources from which scripts can be executed.

---

## **2. Reflected XSS (Non-Persistent XSS)**

**Reflected XSS** occurs when the malicious input provided by the attacker is reflected off the web server, immediately included in the server's response, and executed in the victim's browser. This type of XSS does not get stored on the server and usually requires the user to click on a specially crafted URL.

### **How it Works**
- The attacker crafts a URL with malicious script injected into the URL parameters.
- When the user visits this URL, the server reflects the input back to the page without proper sanitization, causing the script to be executed.

### **Example:**

Consider a simple search feature on a website:

```html
<!-- search.php -->
<form method="GET" action="search.php">
  <input type="text" name="query" placeholder="Search...">
  <button type="submit">Search</button>
</form>

<p>You searched for: <?php echo $_GET['query']; ?></p>
```

An attacker could send the following URL:

```
http://example.com/search.php?query=<script>alert('Reflected XSS')</script>
```

When a user clicks on this URL, the script `<script>alert('Reflected XSS')</script>` is reflected in the page and executed in their browser.

### **Preventing Reflected XSS:**
1. **Validate Input**: Ensure that user inputs are validated on both the client and server-side.
2. **Escape Output**: Use appropriate escaping mechanisms to render user inputs as plain text, preventing them from being interpreted as HTML or JavaScript.
3. **Use HTTP-only Cookies**: Prevent session data from being accessed by JavaScript.

---

## **3. DOM-based XSS (Client-Side XSS)**

**DOM-based XSS** occurs when the vulnerability is caused by client-side JavaScript manipulating the DOM in an unsafe way. This type of XSS happens entirely in the browser, and the server does not necessarily reflect or store the malicious data.

### **How it Works**
- The attacker crafts an input that is manipulated by JavaScript on the client-side.
- The JavaScript on the page then inserts this input into the DOM, and since the input is not sanitized, it executes as JavaScript in the user's browser.

### **Example:**

Consider a webpage with the following JavaScript code:

```html
<!-- dom-xss.html -->
<div id="result"></div>
<script>
  var query = new URLSearchParams(window.location.search).get('query');
  document.getElementById('result').innerHTML = query;
</script>
```

If the attacker sends the following URL to the victim:

```
http://example.com/dom-xss.html?query=<script>alert('DOM-based XSS')</script>
```

The JavaScript will insert the malicious script into the DOM, causing it to execute.

### **Preventing DOM-based XSS:**
1. **Avoid `innerHTML`**: Use safer methods like `textContent` to insert data into the DOM to prevent JavaScript from being executed.
2. **Sanitize Input**: Always sanitize input that is inserted into the DOM to ensure it is safe.
3. **Use JavaScript libraries**: Consider using frameworks like React or Angular, which automatically handle sanitization and escaping.

---

## **Summary of XSS Types**

1. **Stored XSS**:
   - **Occurs when**: Malicious input is stored on the server (e.g., in a database or log).
   - **Example**: Attacker submits a malicious comment that is displayed to all users.
   - **Prevention**: Sanitize and escape input and output; use a Content Security Policy (CSP).

2. **Reflected XSS**:
   - **Occurs when**: Malicious input is reflected off the server and executed immediately in the user's browser.
   - **Example**: Attacker sends a crafted URL with a script embedded in the query string.
   - **Prevention**: Validate input, escape output, use HTTP-only cookies, and employ CSP.

3. **DOM-based XSS**:
   - **Occurs when**: Client-side JavaScript manipulates the DOM with unsanitized data from user input.
   - **Example**: JavaScript reads input from the URL and inserts it into the DOM unsafely.
   - **Prevention**: Avoid `innerHTML`, sanitize input, and use safer JavaScript methods.

---

## **General Recommendations for Preventing XSS**

- **Sanitize Input**: Validate and sanitize all user inputs, especially those from untrusted sources like URLs, forms, and cookies.
- **Escape Output**: Ensure that any user-generated content is properly escaped before rendering on a page.
- **Use HTTP-only and Secure Cookies**: This prevents attackers from accessing session data via JavaScript.
- **Implement Content Security Policy (CSP)**: Restrict sources for JavaScript to mitigate the risk of malicious script execution.
- **Use Secure Frameworks**: Modern web frameworks (like React, Angular, or Vue.js) automatically handle much of the escaping and sanitization, reducing the likelihood of XSS vulnerabilities.

---

By understanding and mitigating the different types of XSS vulnerabilities, developers can significantly enhance the security of their web applications and protect users from malicious attacks.
```

### Key Points:
- **Stored XSS** involves storing malicious scripts on the server.
- **Reflected XSS** involves the immediate reflection of malicious input via URL parameters.
- **DOM-based XSS** occurs when client-side JavaScript manipulates the DOM in an unsafe manner.
```
---

# JavaScript Learning Resources

JavaScript is a versatile and impressive language. I did my best to cover all of the important aspects in this room, but there are still hours of content that we didn't cover. JavaScript has unlimited resources across the web, and if you're serious about web development, programming, or anything in between, I recommend looking into the logic behind the code. Learning how a programming language works will help you 100x more than just memorizing the syntax. You may not always have to explain the logic behind an algorithm, but being able to write the code and explain it can set you apart from the average enthusiast or web developer.

## Free Resources to Continue Learning JavaScript

- [MDN Web Docs - JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [W3Schools - JavaScript](https://www.w3schools.com/js/default.asp)

## What Wasn't Covered in This learning:

- Libraries or Frameworks
- ES6 Destructuring
- Advanced Methods
- And so much more!
