# Javascript Guide - Numbers and dates

## Index

- Introduction
- Grammar and types
- Control flow and error handling
- Loops and interaction
- Functions
- Expressions and operators
- **Numbers and dates**
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

## Numbers

In Javascript, numbers are implemented in double-precision 64-bit binary format IEEE 754, with a numeric precision of 53 bits. Integer values up to ±2<sup>53</sup> − 1 can be represented exactly.

The number type has 3 additional symbolic values: `+Infinity`, `-Infinity` and `NaN`.

A more recent addition to Javascript is `BigInt`, but it has some caveats:
- You can't mix and match `BigInt` and `Number` values in the same operation.
- You can't use the `Math` object with `BigInt` values.

The are four types of number literals: **decimal, binary, octal and hexadecimal**.

### Decimal numbers

```javascript
// Caution when using leading zeros:

0888 // 888 parsed as decimal
0777 // parsed as octal in non-strict mode (511 in decimal)
```

If every digit after the leading 0 is smaller than 8, the number gets parsed as an octal number.

### Binary numbers

Binary number syntax uses a leading zero followed by a lowercase or uppercase Latin letter "B" (`0b` or `0B`). If the digits after the `0b` are not `0` or `1`, the following `SyntaxError` is thrown: "Missing binary digits after 0b".

### Octal numbers

Octal number syntax uses a leading zero. If the digits after the 0 are outside the range 0 through 7, the number will be interpreted as a decimal number.

Strict mode in ECMAScript 5 forbids octal syntax.

### Hexadecimal numbers

Hexadecimal number syntax uses a leading zero followed by a lowercase or uppercase Latin letter "X" (`0x` or `0X`). If the digits after 0x are outside the range (0123456789ABCDEF),  the following `SyntaxError` is thrown: "Identifier starts immediately after numeric literal".

### Exponentiation

```javascript
1E3   // 1000
2e6   // 2000000
0.1e2 // 10
```

## Number object

The built-in Number object has properties for numerical constants:

Table pending

Properties of Number
- Number.MAX_VALUE
- Number.MIN_VALUE
- Number.NaN
- Number.NEGATIVE_INFINITY
- Number.POSITIVE_INFINITY
- Number.EPSILON
- Number.MIN_SAFE_INTEGER
- Number.MAX_SAFE_INTEGER

Methods of `Number`

- Number.parseFloat()
- Number.parseInt()
- Number.isFinite()
- Number.isInteger()
- Number.isNaN()
- Number.isSafeInteger()

Methods of Number.prototype

- toExponential()
- toFixed()
- toPrecision()

## Math object

Methods of Math
- Long list pending

You never create a `Math` object of your own. You always use the built-in `Math` object.

## Date object

JavaScript does not have a date data type. You can use the `Date` object and its methods to work with dates and times. Javscript stores dates as the number of milliseconds since January 1, 1970, 00:00:00.

The `Date` object range is -100,000,000 days to 100,000,000 days relative to 01 January, 1970 UTC.

To create a Date object:

```javascript
var dateObjectName = new Date([parameters]);
```

### Methods of the `Date` object

Some methods:

**Static methods:**

- `Date.now()`
- `Date.parse()`
- `Date.UTC()`

**Instance methods:**

A freaking lot, check the [reference.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)