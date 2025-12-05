---
{"dg-publish":true,"permalink":"/01_Reference/javascript notes/","title":"Javascript notes","tags":["javascript","webdev","programming"],"created":"2025-12-05T03:27:51.078+01:00"}
---


# Javascript notes

---

## Table of content

- [[#Functions]]
- [[#DOM manipulation]]
- [[#Asynchronous Javascript]]
- [[#Read more]]

---

## Functions

### Function definitions

Modern javascript allows few different styles when defining a function. If you are coming from other programming languages you will for sure be familiar with [[#Declarations|function declaration]] by using the  `function` keyword. As language evolved over the years some we got few alternative ways to define a function.

[[#Expressions|Function expressions]] can assign anonymous or named function to a variable. In that case you cannot call the function before you write an expression. There are also [[#Arrow functions]] with it's simplified syntax and very often used as a part of function expression by assigning it to a variable.

#### Declarations

A function declaration defines a function using the `function` keyword, followed by the function name, parameters in parentheses, and the function body inside the curly braces. Declared function are hoisted, available before being defined. Hoisting can make code harder to read and understand, especially for developers who are not familiar with the concept. Seeing a function called before it's defined can be confusing and disrupt the natural flow of reading the code.

To mitigate any possible problems with declared functions being hoisted you should declare them at the top of their scope. Generally preferred for top level functions that you want to be available throughout your code. If you organize all functions below or above main logic than your code can become more readable.

```javascript
// function declaration
// such functions are hoisted and can be called before being defined

console.log(isEven(11));  // output: false

function isEven(number) {
    return number % 2 === 0;
}

console.log(isEven(10));  // output: true
```

#### Expressions

Function expression assigns an anonymous (function name is optional) or named function to a variable. The function itself is created as a part of an expression or statement.

```javascript
// Function expression
// Such functions behaves like a variable and cannot be called before being defined
// Note that we assign it to a variable
const square = function(x) { return x*x; };

// Function expressions can include names, which is useful for recursion.
const f = function fact(x) { if (x <= 1) return 1; else return x*fact(x-1); };

// Function expressions can also be used as arguments to other functions:
[3,2,1].sort(function(a,b) { return a-b; });

// Function expressions are sometimes defined and immediately invoked:
// Notice the '(10)' at the end
let tensquared = (function(x) {return x*x;}(10));
```

> [!tip]
> When importing files and functions in a project, you can occasionally get `TypeError: [name] is not a function`. It can happen because imported function expressions are called before being declared. To solve the issue you can refactor the function expression as a declaration.

#### Arrow functions (ref javascript definitive guide 8.1.3)

You can define functions using a particularly compact syntax known as "arrow functions". It uses the => symbol to separate the function parameters from the function body. Since arrow functions are expressions instead of statements there is no need for a function name either.

```javascript
// Example 1
// Implicit return without parentheses after arrow sign
const add = (a, b) => a + b; // returns a + b

// Example 2
// Requires explicit return with curly braces after arrow
const isEven = (number) => {
  if (number % 2 === 0) {
    return true;
  } else {
    return false;
  }
};

// Example 3
// Arrow function with no parameters and implicit return
const greet = () => "Hello!";

// Example 4
// Arrow function used as a callback
const numbers = [1, 2, 3];
// With only one parameter ther is no need for parentheses
// Return is implicit => number * 2
const doubled = numbers.map(number => number * 2); // Concise callback
```

## DOM manipulation

By using the `web API` provided by the browser, we can manipulate the DOM. There are many different `web API's` you can reference them at: [MDN website/docs/web/api](https://developer.mozilla.org/en-US/docs/Web/API). Reference and guide to the DOM is available at: [MDN website/.../document_object_model](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)

- Adding text content:

```javascript
// creates a text node containing "Hello World!" and inserts it in div
div.textContent = "Hello World!";
```

- Adding HTML content:

```javascript
// renders the HTML inside div
div.innerHTML = "<span>Hello World!</span>";
```

> [!tip]
> Using `element.textContent` is preferred over `element.innerHTML` for adding text. `innerHTML` should be used with caution to avoid potential security risks where it is possible to render `<script>` blocks with malicious code. Watch this [video about preventing one of the most common cross-site scripting attacks.](https://youtube.com/watch?v=ns1LX6mEvyM)

## Asynchronous Javascript

Javascript is synchronous, blocking, single-threaded language. Code executes top-down and only one line is executed at a time.
Single-threaded? Thread is a process that program can use to run a task, each thread can only do one task at a time.

There are ways to implement asynchronous code by using:
- timeouts and intervals
- callbacks
- promises
- async/await
- event loop

## Read more

- [developer.mozilla.org/docs/web/javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) - MDN web docs
- [youtube.com/video](https://www.youtube.com/watch?v=exBgWAIeIeg) - "Asynchronous JavaScript Crash Course" by Codevolution.
- [youtube.com/video](https://www.youtube.com/watch?v=TnhCX0KkPqs) - "Javascript promises - Tutorial for beginners" by ColorCode.
