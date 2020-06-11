# Javascript Guide - Text formatting

## Index

- Introduction
- Grammar and types
- Control flow and error handling
- Loops and interaction
- Functions
- Expressions and operators
- Numbers and dates
- **Text formatting**
- Regular expressions
- Indexed collections
- Keyed collections
- Working with objects
- Details of the object model
- Using promises
- Iterators and generators
- Meta programming
- Javascript modules

## Strings

A string in Javascript is a set of "elements" of 16-bit unsigned integer values  (UTF-16 code units). The length of a String is the number of elements in it. You can create strings using string literals or string objects.

### String literals

You can create simple strings using either single or double quote.

More advanced strings can be created using escape sequences:

**Hexadecimal escape sequences**

`'\xA9' // "©"`

**Unicode escape sequences**
`'\u00A9' // "©"`

**Unicode code point escapes**

New in ES6. 
See:
[String.fromCodePoint()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/fromCodePoint) and [String.prototype.codePointAt()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/codePointAt)

### String objects

The `String` object is a wrapper around the string primitive data type.


You can call any of the methods of the `String` object on a string literal value—JavaScript automatically converts the string literal to a temporary `String` object, calls the method, then discards the temporary `String` object.

```javascript
const foo = new String('foo'); // Creates a String object
console.log(foo); // Displays: [String: 'foo']
typeof foo; // Returns 'object'
```

You should use string literals unless you specifically need to use a `String` object, because `String` objects can have counterintuitive behavior.

```javascript
const firstString = '2 + 2'; // Creates a string literal value
const secondString = new String('2 + 2'); // Creates a String object
eval(firstString); // Returns the number 4
eval(secondString); // Returns the string "2 + 2"
```

A `String` object has one property, `length`. You can access each code unit using an array bracket style. You can't change individual characters because strings are immutable array-like objects.


The following table summarizes the methods of `String` objects.

**Methods of `String`**

`charAt, charCodeAt, codePointAt`
`indexOf, lastIndexOf`
`startsWith, endsWith, includes`
`concat`
`fromCharCode, fromCodePoint`
`split`
`slice`
`substring, substr`
`match, matchAll, replace, replaceAll, search`
`toLowerCase, toUpperCase`
`normalize`
`repeat`
`trim`

### Multi-line template literals

Template literals are enclosed by the back-tick (\` \`). Can be used for multi-lines and embedded expressions.

For more info: [Template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) in the Javascript Reference.

## Internationalization

The `Intl` object is the namespace for the ECMAScript Internationalization API, which provides language sensitive string comparison, number formatting, and date and time formatting. The constructors for `Collator`, `NumberFormat`, and `DateTimeFormat` objects are properties of the `Intl` object.

### Date and time formatting

The `DateTimeFormat` object is useful for formatting date and time

```javascript
const msPerDay = 24 * 60 * 60 * 1000;
 
// July 17, 2014 00:00:00 UTC.
const july172014 = new Date(msPerDay * (44 * 365 + 11 + 197));

const options = { year: '2-digit', month: '2-digit', day: '2-digit',
                hour: '2-digit', minute: '2-digit', timeZoneName: 'short' };
const americanDateTime = new Intl.DateTimeFormat('en-US', options).format;
 
console.log(americanDateTime(july172014)); // 07/16/14, 5:00 PM PDT
```

### Number formatting

The `NumberFormat` object is useful for formatting numbers, for example currencies.

```javascript
const gasPrice = new Intl.NumberFormat('en-US',
                        { style: 'currency', currency: 'USD',
                          minimumFractionDigits: 3 });
 
console.log(gasPrice.format(5.259)); // $5.259

const hanDecimalRMBInChina = new Intl.NumberFormat('zh-CN-u-nu-hanidec',
                        { style: 'currency', currency: 'CNY' });
 
console.log(hanDecimalRMBInChina.format(1314.25)); // ￥ 一,三一四.二五
```

### Collation

The `Collator` object is useful for comparing and sorting strings.

For example, there are actually two different sort orders in German, phonebook and dictionary...