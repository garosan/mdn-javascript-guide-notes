# Javascript Guide - Control flow and error handling

## Index

- Introduction
- Grammar and types
- **Control flow and error handling**
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

## Block statement

The most basic statement is a block statement, which is used to group statements. The block is delimited by a pair of curly brackets:

Block statements are commonly used with control flow statements (`if`, `for`, `while`):

```javascript
while (x < 10) {
  x++;
}
```

## Conditional statements

JavaScript supports two conditional statements: `if...else` and `switch`.

### If...else statement

Conditional statement example:

```javascript
if (condition_1) {
  statement_1;
} else if (condition_2) {
  statement_2;
} else if (condition_n) {
  statement_n;
} else {
  statement_last;
} 
```

**Falsy values**

- `false`
- `undefined`
- `null`
- `0`
- `NaN`
- Empty string (`""`)

### Switch statement

```javascript
switch (expression) {
  case label_1:
    statements_1
    [break;]
  case label_2:
    statements_2
    [break;]
    …
  default:
    statements_def
    [break;]
}
```

## Exception handling statements

You can throw exceptions using the `throw` statement and handle them using the `try...catch` statements.

### Exception types

- [ECMAScript Exceptions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error#Error_types)
- [`DOMException`](https://developer.mozilla.org/en-US/docs/Web/API/DOMException) and [`DOMError`](https://developer.mozilla.org/en-US/docs/Web/API/DOMError)

### Throw statement

Use the `throw` statement to throw an exception. A `throw` statement specifies the value to be thrown:

```javascript
throw 'Error2';   // String type
throw 42;         // Number type
throw true;       // Boolean type
throw {toString: function() { return "I'm an object!"; } };
```

### `try...catch` statement

The `try...catch` statement marks a block of statements to try, and specifies one or more responses should an exception be thrown. If an exception is thrown, the `try...catch` statement catches it.

Here's am example including `finally`:

```javascript
openMyFile();
try {
  writeMyFile(theData); // This may throw an error
} catch(e) {  
  handleError(e); // If an error occurred, handle it
} finally {
  closeMyFile(); // Always close the resource
}
```

### Utilizing error objects

Depending on the type of error, you may be able to use the `name` and `message` properties to get a more refined message.

The `name` property provides the general class of `Error` (such as `DOMException` or `Error`), while `message`generally provides a more succinct message than one would get by converting the error object to a string.