# Javascript Guide - Grammar and types

## Index

- Introduction
- **Grammar and types**
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

## Basics

Javascript borrows most of its syntax from Java, C and C++, but has also been influenced by Awk, Perl and Python.

Javascript uses the Unicode character set. For example the german word 'Früh' can be used as a variable name.

Instructions are called statements and are separated by semicolons. Semicolons are not mandatory unless you want to write two statements on the same line. It is considered best practice, however, to always write a semicolon after a statement.

The source text of a Javascript script gets scanned and converted into input elements which are tokens, control characters, line terminators, comments and whitespace (spaces, tabs and newline characters are considered whitespace).

## Comments

```javascript
// One line comments

/* Multiline
	 comment
*/
```

A hashbang comment is a special comment used to specify the path to a particular JavaScript engine and looks like this:

```javascript
#!/usr/bin/env node
```

## Declarations

Javascript has three kinds of variable declarations:

- `var`: Declares a variable, optionally initializing it to a value.
- `let`: Declares a block-scoped, local variable, optionally initalizing it to a value.
- `const`: Declares a block-scoped, read-only named constant.

### Variables

The names of variables, called identifiers, conform to certain rules:
- A Javascript identifier must start with a letter, underscore or dollar sign. Subsequent characters can also be digits (0-9).
- Javascript is case sensitive.
- You can use most of ISO 8859-1 or Unicode letters such as `å` and `ü` in identifiers. [More Details](https://mathiasbynens.be/notes/javascript-identifiers-es6)

### Declaring variables

You can declare variables in two ways:

- With `var`. Ex: `var x = 42`. With `var` you can declare **local** and **global** variables, depending on the execution context.
- With `const` or `let`. With them you can declare block-scoped variables.

You can also simply assign a value to a variable: `x = 42`. This form creates an **undeclared global variable**. It also generates a strict Javascript warning. Undeclared global variables can often lead to unexpected behavior, therefore, **it is discouraged to use undeclared global variables**.

### Evaluating variables

A variable declared using `var` or `let` with no assigned value has a value of `undefined`.

An attempt to access an undeclared variable results in a `ReferenceError` exception being thrown.

```javascript
console.log('The value of y is ' + y); // Uncaught ReferenceError: y is not defined
```

The `undefined` value behaves as `false` in a boolean context.
The `undefined` value converts to `NaN` when used in numeric context.

When a variable has the value `null`, it behaves as `0` in numberic contexts and as `false` in boolean contexts.

### Variable scope

- A global variable is a variable declared outside of any function.
- A local variable is a variable declared inside of a function.

Javascript before ECMAScript 2015 doesn't have block statement scope.

Consider the following code:

```javascript
if (true) {
	var x = 5;
}

console.log(x); 		// x is 5
```

`x` is available outside the `if` block.

But when using `let`, the variable is not available outside the block:

```javascript
if (true) {
	let y = 5;
}

console.log(y); 		// ReferenceError: y is not defined
```

### Variable hoisting

An unusual thing about Javascript is that you can refer to a variable declared later, without getting an exception. 

This concepts is known as **hoisting**. Variables that are hoisted return a value of `undefined`.

Examples:

```javascript
// Example 1
console.log(x === undefined); 	// true
var x = 3;

// Example 2
var myvar = 'my value';

(function() {
	console.log(myvar); // undefined
	var myvar = 'local value';
})();
```

Because of hoisting, all `var` statements should be placed as near to the top of the function as possible. This is considered a best practice.

In ES2015, `let` and `const` are hoisted but not initialized. Referencing the variable in the block before its declaration results in a `ReferenceError`.

### Function hoisting

Function *declarations* are hoisted, but not function *expressions*.

```javascript
/* Function declaration */

foo(); // "bar"

function foo() {
  console.log('bar');
}

/* Function expression */

baz(); // TypeError: baz is not a function

var baz = function() {
  console.log('bar2');
};
```

### Global variables

Global variables are properties of the *global object*. In webpages, the global object is `window`. 

### Constants

You can create read-only, named constants with the `const` keyword.

A constant cannot change value through assignment or be re-declared. However, if you assign an object or array to a constant, you can modify the properties inside them without problems.

## Data structures and types

### Data types

(Somewhere else in MDN I read a bit different explanation).

The latest ECMAScript standard defines eight data types:

Seven data types are **primitives**:

- Boolean
- null
- undefined
- Number
- BigInt
- String
- Symbol (New in ES2015)

and Object.

`Objects` and `functions` are the other fundamental elements in the language.

### Data type conversion

Javascript is *dynamically typed*. This means you can assign a variable to an int and later assign it to a string or other type without any problem.

### Numbers and the + operator

In expressions that involve numeric values and strings with the `+` operator, Javascript converts numeric values to strings. With all other operators, it does not.

```javascript
'37' - 7 // 30
'37' + 7 // "377"
```

### Converting strings to numbers


