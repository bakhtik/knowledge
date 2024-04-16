# JavaScript Basics

- [Variables](#variables)
- [Types](#types)
- [Conversions](#conversions)
- [Numbers and Math](#numbers-and-math)
- [Strings](#strings)

## Variables

```js
// log to console
console.log("Hello World!");
console.log(123);
console.log(true);
var arg = 'Hello';
console.log(arg);
console.log([1,2,3]);
console.log({a:1, b:2});
console.table({a:1, b:2});

console.error('This is some error');
console.clear();
console.warn('This is a warning');
console.time('Hello');
  console.log("Hello World!");
  console.log("Hello World!");
  console.log("Hello World!");
console.timeEnd('Hello');

/*
 * Multiline
 * comments
 */

// var, let, const
var name = 'John Doe';
name = "Steve Smith";

// Init var
var greeting;
greeting = "Hello";

// letters, numbers, _, $
// cannot statrt with number

// Multi word vars
var firstName = 'John'; // Camel clase

// LET
let name;
name = 'John Doe';
name = 'Steve Smith';

// CONST
const name = 'John';
// Cannot reassign
name = 'Sara';
// Have to assign a value
const greeting;

const person = {
	name: 'John',
	age: 30
}

person.name = 'Sara';
person.age = 32;

const numbers = [1,2,3,4,5];
numbers.push(6);
```

## Types

```js
// PRIMITIVE

// String
const name = 'John Doe';
// Number
const age = 45;
// Boolean
const hasKids = true;
// Null
const car = null;
// Undefined
let test;
// Symbol
const sym = Symbol();

// REFERENCE TYPES - Objects:w

// Array
const hobbies = ['movies', 'music'];
// Object litersl
const address = {
	city: 'Boston',
	state: 'MA'
}
const today = new Date();

console.log(today);
console.log(typeof today);
```

## Conversions

```js
// Type conversion

let val;

// Number to string
val = String(555);
val = String(4+4);
// Bool to stirng
val = String(true);
// Date to string
val = String(new Date());
// Array to string
val = String([1,2,3,4]);

// toString()
val = (5).toString();
val = (true).toString();

// String to number
val = Number('5');
val = Number(true);		// 1
val = Number(false);	// 0
val = Number(null);		// 0
val = Number('hello');  // NaN - not a number
val = Number([1,2,3]);  // NaN

val = parseInt('100');
val = parseFloat('100.30');

// Output
console.log(val);
console.log(typeof val);
//console.log(val.length);
console.log(val.toFixed(2));

// Type coersion

const val1 = String(5);
const val2 = 6;
const sum = val1 + val2; // '56'

console.log(sum);
console.log(typeof sum);
```

## Numbers and Math

```js
// Numbers and Math

const num1 = 100;
const num2 = 50;
let val;

// Simple math with numbers
val = num1 + num2;
val = num1 * num2;
val = num1 - num2;
val = num1 / num2;
val = num1 % num2;

// Math Object
val = Math.PI;
val = Math.E;
val = Math.round(2.8);	// 3
val = Math.ceil(2.4);	// 3
val = Math.floor(2.8);	// 2
val = Math.sqrt(64);	// 8
val = Math.abs(-3);
val = Math.pow(8, 2);	// 64
val = Math.min(2,33,4,1,55,6,3,-2);	// -2
val = Math.max(2,33,4,1,55,6,3,-2);	// 55
val = Math.random(); // random decimal

val = Math.floor(Math.random() * 20 + 1); // radnom integer between 1 and 20

console.log(val);
```

## Strings

```js
// String Meothods and Concatenations

const firstName = "William";
const lastName = "Johnson";
const age = 36;
const str = 'Hello there my name is Brad';
const tags = 'web design,web development';

let val;

val = firstName + lastName;

// Concatenation
val = firstName + ' ' + lastName;

// Append
val = 'Brad ';
val += 'Traversy';

val = 'Hello, my name is ' + firstName + ' and I am ' +  age;

// Escaping
val = 'That\'s awesome, I can\'t wait';

// Length
val = firstName.length;

// concat method
val = firstName.concat(' ', lastName);

// Change case
val = firstName.toUpperCase();
val = firstName.toLowerCase();

// treat strings as a readonly arrays
val = firstName[0]; // 'W'

// indexOf()
val = firstName.indexOf('l'); // 2
val = firstName.lastIndexOf('i'); // 4


// charAt()
val = firstName.charAt('2'); // 'l'

// Get last char
val = firstName.charAt(firstName.length - 1); // 'm'

// Substtings
val = firstName.substring(0, 4); // 'Will'

// slice()
val = firstName.slice(0, 4); // 'Will'
val = firstName.slice(-3); // 'iam'

// split
val = str.split(' '); // ['Hello', 'there', 'my', ...]
val = tags.split(',');

// replace
val = str.replace('Brad', 'Jack');

// inlcudes()
val = str.includes('Hello'); // true
val = str.includes('foo'); // false

console.log(val);
```
