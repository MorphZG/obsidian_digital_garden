---
{"dg-publish":true,"permalink":"/03_Literature_notes/javascript - the definitive guide/","title":"Javascript - The definitive guide","tags":["webdev","javascript"],"created":"2025-12-05T03:27:50.259+01:00"}
---


# Javascript - The definitive guide

> [!abstract]- book metadata
Title: Javascript - The definitive guide, 7th edition
Author: David Flanagan
Pub date: 29 May 2020
Publisher: O'Reilly Media
ISBN: 9781491952023
Language: English
Pages: 687
Weight: 1202 g
Height: 178 mm
Width: 233 mm
Cover:
<img src="https://blackwells.co.uk/jacket/l/9781491952023.webp" alt="Cover" width="300" />

## Summary

The book covers the Javascript language and the Javascript APIs implemented by browsers and by Node. For readers with some prior programming experience who want to learn Javascript and also for programmers who already use JavaScript but want to take understanding to a new level and really master the language. This is a long and comprehensive book that documents the Javascript both on client and server side.

Previous editions included a comprehensive reference section. This revised, seventh edition, no longer needs a reference section since it is much easier to find such material online. Anything related to core or client-side javascript can be found at [MDN website](https://developer.mozilla.org) and for server-side Node APIs there is a [Node.js documentation](https://nodejs.org/api)

### Example code

Example code can be found at [David Flanagan's github page](https://github.com/davidflanagan/jstdg7)

## Table of  content

- [[#Chapter 1 - Introduction to Javascript]]
- [[#Chapter 2 - Lexical Structure]]
- [[#Chapter 3 - Types, Values, and Variables]]
- Expressions and Operators
- Statements
- Objects
- Arrays
- Functions
- Classes
- Modules
- The JavaScript Standard Library
- Iterators and Generators
- Asynchronous JavaScript
- Metaprogramming
- JavaScript in Web Browsers
- Server-Side JavaScript with Node
- JavaScript Tools and Extensions

## Chapter 1 - Introduction to Javascript

### Strict mode

As javascript continues to evolve with many new improvements over the years there is a huge amount of legacy code which is still in use. In order to maintain backward compatibility it is not possible to remove legacy features no matter how flawed. From ES5 and later, applications can opt in to strict mode in which number of early language mistakes have been corrected.

## Chapter 2 - Lexical Structure

The lexical structure of a programming language is the set of elementary rules that specifies how you write programs in that language. It is the lowest-level syntax of a language. It specifies what variable names look like, the delimiter characters for comments, and how one program statement is separated from the next.

- ignores spaces that appear between tokens in programs.
- ignores line breaks.
- indentation can be used to format the code style
- new lines are recognised as line terminators
- inline comment opener: `//`
- multi line comment between `/* comment */`

### 2.4 Identifiers and reserved words

Simply a name. Used to name constants, variables, properties, functions, classes, label for certain loops... Must begin with a letter, an underscore or a dollar sign. Digits are not allowed as first characters so javascript can distinguish identifiers from numbers.

Reserved words cannot be used as identifiers but can be used as property names within the objects.

Keywords such as `let` can't be fully reserved in order to retain backward compatibility with legacy code. `let` can be used as variable name if declared with `var` outside of a class, for example, but not if declared inside a class or with `const`.

> [!info]- Keywords:
> These are true reserved keywords that are part of the JavaScript language syntax and cannot be used as identifiers.
>```
>abstract, arguments, await, boolean, break, byte, case, catch, char, class, const, continue, debugger, default, delete, do, double, else, enum, eval, export, extends, false, final, finally, float, for, function, goto, if, implements, import, in, instanceof, int, interface, let, long, native, new, null, package, private, protected, public, return, short, static, super, switch, synchronized, this, throw, throws, transient, true, try, type, typeof, var, void, volatile, while, with, yield
>```

> [!info]- Additional reserved words:
> This list includes built-in functions, objects, or commonly used methods that are provided by JavaScript but are not reserved keywords in the strictest sense. Some entries may refer to properties of global objects or methods of those objects
>```
>alert, all, apply, async, await, bind, blur, case, catch, clearTimeout, console, debugger, document, encodeURI, encodeURIComponent, escape, eval, fromCharCode, function, hasOwnProperty, Infinity, isFinite, isNaN, isPrototypeOf, length, log, Math, NaN, parseFloat, parseInt, preserve, prototype, push, return, setTimeout, slice, toString, unescape, undefined
>```

### 2.5 Unicode

While it is common to use ASCII symbols, it is only by a convention. Javascript can be written using any Unicode character. This means that developers can use symbols and characters not only from english alphabet. Look for [[00_Fleeting_inbox/Unicode\|Unicode]] character table for more info.

Some computer software or hardware cannot display, input or process full [[00_Fleeting_inbox/Unicode\|Unicode]] character set. In those cases javascript offers Unicode escape sequence. We can use a combination of ASCII characters to represent some Unicode character but to do so we must use Unicode escape sequence. It begins with `\u` and is either followed by exactly four **hexadecimal digits** (using uppercase or lowercase letters A-F) `\u00e9` or by one to six hexadecimal digits enclosed in curly braces `\u{E9}`

### 2.6 Optional semicolons

Semicolons separate statements from one another. Without the separator the end of one statement might appear to be the beginning of the next. If statements are written in separate lines you can omit the semicolon. You can also omit a semicolon at the end of a program or if the next token in the program is a closing curly brace.

```js
// newline, semicolon is optional
a = 3
b = 4;

// semicolon is required
a = 3; b = 4;
```

## Chapter 3 - Types, Values, and Variables

### 3.1 Overview and definitions

Javascript types can be divided into two categories: primitive and object types. Primitive types include numbers, strings and boolean values.

ES6 adds a new special-purpose type, known as **Symbol**, that enables the definition of language extensions without harming backward compatibility. Symbols are covered briefly in 3.6

An object (member of a type object) is a collection of properties where each property has a name and a value (either a primitive value or another object). Special object, the **global** object is covered in 3.7, but more general and more detailed coverage of objects is in chapter 6.

###### CONTINUE HERE

In addition to basic objects and arrays, javascript defines...
