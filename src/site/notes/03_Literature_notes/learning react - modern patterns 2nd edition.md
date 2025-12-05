---
{"author":"Alex Banks, Eve Porcello","date":"2025-02-07","dg-publish":true,"source":"book","status":"draft","tags":["webdev","react","javascript"],"title":"Learning React","type":"literature_note","URL":"https://www.goodreads.com/book/show/80721783-learning-react","permalink":"/03-literature-notes/learning-react-modern-patterns-2nd-edition/","dgPassFrontmatter":true}
---


```md
## First Chapter
### Key concepts
Main Idea
Details
### Questions, concepts to explore
### Personal thoughts
### Examples or code snippets
### Chapter summary
### References or additional reading materials
- [[#Table of content|Table of content]]: Jump up!
```

---

# Learning React

## Modern Patterns for Developing React Apps

- Local file: [~/Downloads/reading/Learning React.pdf](file:///home/zoran/Downloads/reading/learning_react_by_alex_banks_and_eve_porcello.pdf)
- Code examples, exercises... available for download at [github.com/moonhighway/learning-react](https://github.com/moonhighway/learning-react)

> [!abstract]- book metadata
Title: Learning React - Modern Patterns for Developing React Apps, 2nd Edition
Author: Alex Banks, Eve Porcello
Pub date: June 2020
Publisher: O'Reilly Media, Inc.
ISBN: 9781492051725
Language: English
Pages: 310
Weight:
Height: 233 mm
Width: 178 mm
Cover:
<img src="https://m.media-amazon.com/images/I/91uFdkCJmAL._SL1500_.jpg" alt="Cover" width="300"  />

---

## Table of  content

- [[#Chapter 1 - Welcome to react]]
- [[#Chapter 2 - Javascript for react]]
- [[#Chapter 3 - Functional programming with javascript]]
- [[#Chapter 4 - How react works]]
- [[#Chapter 5 - React with JSX]]
- [[#Chapter 6 - React state management]]
- [[#Chapter 7 - Enhancing components with hooks]]
- [[#Chapter 8 - Incorporating data]]
- [[#Chapter 9 - Suspense]]
- [[#Chapter 10 - React testing]]
- [[#Chapter 11 - React router]]
- [[#Chapter 12 - React and the server]]

---

## Chapter 1 - Welcome to react

### Key concepts

- React developer tools. Available as browser extension for chrome and firefox but also as a standalone app. Useful when debugging or when learning about react in other online projects and web apps.

---

## Chapter 2 - Javascript for react

### Key concepts

- Declaring variables:
	- In addition to `var`, modern javascript can benefit from `const` (constant) and `let` (lexical variable scope) keywords
- Template strings
- Creating functions
	- Function declaration
	- Function expression
	- Arrow functions
- Compiling javascript
- Objects and arrays
- Asynchronous javascript
	- Simple promises with `fetch`
	- `async` and `await` keywords
	- Building promises
- Classes
- ES6 Modules vs CommonJS

### Questions, concepts to explore

### Personal thoughts

Since initial release in 1995, Javascript has gone through many changes. From adding interactive elements to the web pages javascript became more robust with early `DHTML` and `AJAX` features to `Node.js` and many different frameworks but also many core, built-in features have improved so much that javascript has become a real software language that's used to build modern, fullstack applications we have today. In early days many software engineers considered javascript to be a gimmick scripting language and nothing more than that.

After release of ES6 in 2015. there have been yearly releases of new JS features. Each proposal is taken through the clearly defined stages, from stage 0 up to stage 4 which represents the finished proposal. In those final stages it is up to the browser vendors to implement the features.

### Examples or code snippets

- Template strings provide us alternative to string concatenation, allows us to insert variables into a string.

```javascript
// traditional concatenation
console.log(lastName + ", " + firstName + " " + middleName);

// template string or template literal uses backticks and respects the whitespasce making them easier to read
console.log(`${lastName}, ${firstName} ${middleName}`);
```

- Function Declaration starts with the `function` keyword

```javascript
// function declarations are hoisted to the top, you can call the function before it you declare it. so code like this will run without problems

logSomething(); // works fine, function declaration is hoisted to the top of the scope

function logSomething() {
    console.log("You are doing great");
}
```

- Function Expression. If you write the function as a part of the variable then you have written an expression. Such functions are not hoisted and will produce `TypeError` if you invoke it before you write an expression.

```javascript
logSomething(); // TypeError: logSomething is not a function

const logSomething = function() {
    console.log("You are doing great");
}

logSomething(); // works fine
```

> [!tip]
> When importing files and functions in a project you can occasionally get an `TypeError: [name] is not a function` because a function you imported is written as an expression. If you see it, try to refactor the code and declare the function.

### Chapter summary

#### CONTINUE AT `FUNCTION RETURNS` @ 40/488

### References or additional reading materials

- [ECMAScript compatibility table](compat-table.github.io/compat-table/) - List of proposed javascript features and their support by the browsers
- [[01_Reference/javascript notes\|Javascript notes]] - personal reference note on important javascript concepts
- [[#Table of content|Table of content]]: Jump up!
