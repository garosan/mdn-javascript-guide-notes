# Javascript Guide - Functions

## Index

- Introduction
- Grammar and types
- Control flow and error handling
- Loops and interaction
- **Functions**
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

A function is a Javascript procedure - a set of statements that performs a task or calculates a value.

## Defining functions

### Function declarations

A function declaration (also called **function definition** or **function statement**) consists of:

- The `function` keyword followed by:
- The name of the function.
- A list of parameters to the function (enclosed in parentheses, comma separated).
- The Javascript statements that make up the function, enclosed in curly braces `{}`.

Example:

```javascript
function square(number) {
  return number * number;
}
```

Primitive parameters are passed to functions **by value**. Non-primitives like arrays or user-defined objects are passed **by reference**. 

This means that if you pass a number as a paratemer to a function, and modify the number inside the function, the change will not be visible outside that function. With non-primitives the opposite happens (`The car.make = 'Toyota'` example).

### Function expressions

Functions can also be created by function expressions. Such functions can be anonymous:

```javascript
const square = function(number) { return number * number }
```

Function expressions *can* have a name. This allows the function to refer to itself, among other things.

```javascript
const factorial = function fac(n) { return n < 2 ? 1 : n * fac(n - 1) }
```

In Javascript, a function can be defined based on a condition:

```javascript
var myFunc;
if (num === 0) {
  myFunc = function(theObject) {
    theObject.make = 'Toyota';
  }
}
```

Finally, you can also use the `Function` constructor to create functions from a string at runtime.

A **method** is a function that is the property of an object.

## Calling functions

Defining a function does not execute it. Calling a function actually executes it. Say we have our function `square`, you could call it as follows:

```javascript
square(5);
```

Functions must be *in scope* when they are called, but the function declaration can be hoisted. (**Function hoisting only works with function declarations, not with function expressions**).

## Function scope

Variables defined inside a function cannot be accessed from anywhere outside the function. However, a function can access all variables and functions defined inside the scope in which it is defined.

## Scope and the function stack

### Recursion

There are three ways for a function to refer to itself:

- The function's name
- `arguments.callee`
- An in-scope variable that refers to the function

### Nested functions and closures

You may nest a function within another function. The nested function is private to its containing function. It also forms a *closure*. A closure is an expression (most commonly, a function) that can have free variables together with an environment that binds those variables (that "closes" the expression).

Since a nested function is a closure, this means that a nested function can "inherit" the arguments and variables of its containing function.

- The inner function forms a closure: the inner function can use the arguments and variables of the outer function, while the outer function cannot use the arguments and variables of the inner function.



### Preservation of variables

### Multiply-nested functions

Functions can be multiply-nested.

Example:

```javascript
function A(x) {
  function B(y) {
    function C(z) {
      console.log(x + y + z);
    }
    C(3);
  }
  B(2);
}
A(1); // logs 6 (1 + 2 + 3)
```

`C` accesses `B`'s `y` and `A`'s `x`. But the reverse is not true. `A` cannot access `B`'s or `C`'s variables.

### Name conflicts

When two arguments or variables in the scopes of a closure have the same name, there is a name conflict. More nested scopes take precedence. This is the scope chain.

## Closures

Closures are one of the most powerful features of JavaScript. JavaScript allows for the nesting of functions and grants the inner function full access to all the variables and functions defined inside the outer function.

However, the outer function does not have access to the variables and functions defined inside the inner function.

A closure is created when the inner function is somehow made available to any scope outside the outer function.

Caution: There are a number of pitfalls to watch out for when using closures!

If an enclosed function defines a variable with the same name as a variable in the outer scope, then there is no way to refer to the variable in the outer scope again.  (The inner scope variable "overrides" the outer one, until the program exits the inner scope.)

More info:
(Use cases for callbacks and closures)[https://stackoverflow.com/questions/2622421/what-are-the-use-cases-for-closures-callback-functions-in-javascript]

## Using the arguments object

The arguments of a function are maintained in an array-like object. Within a function, you can address the arguments passed to it as follows:

```
arguments[i]
```

**Note**: The arguments variable is "array-like", but not an array. It is array-like in that it has a numbered index and a length property. However, it does not possess all of the array-manipulation methods.

## Function parameters

Starting with ES6, there are two new kind of parameters: *default parameters* and *rest parameters*.

### Default parameters

In Javascript, parameters of functions default to undefined.

Before ES6, to create *default* parameters, you had to do a little check for an `undefined` value of a parameter passed. If it was undefined, you assigned it the value you wanted.

With ES6, you can now do this:

```javascript
function multiply(a, b = 1) {
  return a * b;
}

multiply(5); // 5
```


### Rest parameters

The rest parameter syntax allows us to represent an indefinite number of arguments as an array.

In the following example, the function multiply uses rest parameters to collect arguments from the second one to the end. The function then multiplies these by the first argument. 

```javascript
function multiply(multiplier, ...theArgs) {
  return theArgs.map(x => multiplier * x);
}

var arr = multiply(2, 1, 2, 3);
console.log(arr); // [2, 4, 6]
```

## Arrow functions

An arrow function expression has a shorter syntax and does not have its own `this`, arguments, super or new.target. Arrow functions are **always anonymous**.

### Shorter functions

With arrow functions you can do:

```javascript
var mapped = a.map(s => s.length);
```

### No separate `this`

Before arrow functions, every new function defined its own `this` value. An arrow function does not have its own `this`; the `thi`s value of the enclosing execution context is used.

## Predefined functions

JavaScript has several top-level, built-in functions:

- `eval()`
- `uneval()`
- `isFinite()`
- `isNan()`
- `parseFloat()`
- `parseInt()`
- `decodeURI()`
- `decodeURIComponent()`
- `encodeURI()`
- `encodeURIComponent()`
- `escape()`   		// deprecated
- `unescape()` 		// deprecated

