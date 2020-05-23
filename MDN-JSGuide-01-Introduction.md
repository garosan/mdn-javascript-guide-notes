# Javascript Guide - Introduction

## Index

- **Introduction**
- Grammar and types
- Control flow and error handling
- Loops and interaction
- Functions
- Expressions and operators
- Numbers and dates
- Text formatting
- Regular expressions
- Indexed collections
- Keyed collections
- Working with objects
- Details of the object model
- Using promises
- Iterators and generators
- Meta programming
- Javascript modules

## Prerequisites

- General understanding of the internet and the WWW
- HTML
- Basic programming

## Where to find Javascript information

- Learn Web Development
- [Javascript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
- Javascript Reference

## What is Javascript?

Javascript is a cross-platform scripting language to make webpages interactive. 

Javascript contains a standard library of objects, such as `Array`, `Date` and `Math` and a core set of language elements such as operators, control structures and statements. Core Javascript can be extended for a variety of purposes by supplementing it with additional objects, for example:

- Client-side Javascript extends the core language by supplying objects to control a browser and its Document Object Model (DOM).
- Server-side Javascript extends the core language by supplying objects for operations such as communication with a database or file manipulations.

## Javascript and Java

Javascript and Java are different languages. In case you didn't know.

- Javascript lacks Java's static typing and strong type checking.
- Javascript supports a runtime system based on a small number of data types.
- Javascript has a prototype-based object model instead of the more common class-based object model.
- Javascript's prototype-based model provides dynamic inheritance.

Javascript is very free-form compared to Java. You don't have to declare all variables, classes and methods. Variables, parameters and function return types are not explicitly typed.

Java's class-based model means that programs consist exclusively of classes and their methods. Java's class inheritance and strong typing requires tightly coupled object hierarchies. This makes Java programming more complex.

In contrast, Javascript descends in spirit from HyperTalk and dBASE: easy syntax, minimal requirements for object creation.

## Javascript and the ECMAScript specification

Javascript is standardized at ECMA International. The standardized version of Javascript is called ECMAScript. The ECMAScript standard is documented in the ECMA-262 specification.

The ECMA-262 standard is also approved by the ISO as ISO-16262. The ECMAScript specification does not describe the Document Object Model (DOM), which is standardized by the W3C.

### Javascript documentation versus the ECMAScript specification

Use the ECMAScript specification to be compliant when writing a JS engine or implementation.
Use the Javascript docs when programming Javascript scripts.

## Getting started with Javascript

### A 'Hello World' in Javascript

```javascript
(function(){
	"use strict";

	function greetMe(yourName) {
		alert("Hello " + yourName);
	}

	greetMe("World");
})();
```

