# JavaScript

## Getting Up and Running

```JavaScript
// print thing on console
console.log("Hello world!");
```

Introducing **jQuery**, read more [here](https://jquery.com/).

JavaScript includes math operatos, `+`, `-`, `*`, `/`, `(` and `)`.

## Data Types

```JavaScript
var {{variableName}} = {{someValue}};

var firstName = 'Xinyang';
```

### Truthy/Falsy

|Truthy|Falsy|
|------|-----|
|true|false|
|non-zero numbers|0|
|"string"|""|
|objects|undefined|
|arrays|null|
|functions|NaN|

NOTE: Truthy evaluates to *true* and falsy evaluates to *false*. Two special numeric values are `Infinity` and `-Infinity`.

`NaN` or Not a Number, is a value that turns up when user ask **JavaScript** to do impossible things in arithmetic. 
(e.g. Deivide zero by zero)

If in double, use strick equal `===` and strict not equal `!==` in situations where truthy or falsy values could lead to logic errors.
These operators ensure that the objects are compared by type and by by value.

Read more about "True Lies and Falsy Values in Python and JavaScript" 
[here](http://opensourcehacker.com/2012/10/17/true-lies-and-falsy-values-in-python-and-javascript/).

### Arrays

```JavaScript
var array0 = [item1, item2, item3];

var array1 = ["string",
			  3.1415,
			  {
				"state": false
			  }, 
			  function(){return 0}
			 ];
```

NOTE: Length of array is **NOT** equal to number of elements inside.

### Object

Object contains information and tools. There are no class in **JavaScript**. 

```JavaScript
skills = ['awesomeness', 'programming', 'JavaScript'];

// JavaScript Object
var bio = {
	'name': 'Xinyang',
	'age': 9999,
	'skills': skills
};

// access to the property with dot notation and bracket notation
var age = bio.age;
var name = bio['name'];

function Car() {}

/*
var Car = function() {}
*/

var car = new Car();
```

NOTE: Dote notation and bracket notation are different with the properties you can access with.

### JSON

**JavaScript Object Notation**, a popular and simple format for storing and transferring nested or hierarchal data.
Internet GET and POST requests frequently pass data in JSON format.
JSON allows for objects to be easily encapsulated within other objects.

NOTE: If you generate JSON by hand, test you code using JSON linter, [jsonlint.com](http://jsonlint.com/)

## Flow Control

### if Statement

```JavaScript
if (condition) {
	statement;
} else {
	statement;
}
```

### Strick Equality vs. Loose Equality

When use strick equality, `===`, no type conversion is done prior to the comparison. 
If the value are different types, they can never be **true**. 
(e.g. a `String` and a `Number`). 
In order to return **true**, the valuees must be equal and the types must be the same.

Loose equality, `==`, if two values are not the same type, converts to a common type before the comparison.
If the types are the same, no difference between `===` and `==`.

NOTE: **NEVER** use `==` because it is frequent source of bugs.
Read more about equlity comparisons and sameness [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness).

## Loops

> Don't repeat yourself!

### while Loop

```JavaScript
while(condition) {
	statement;
}
```

### for Loop

```JavaScript
for(initialisation; condition; mutator) {
	statement;
}

for(var i = 0; i < 3; i++) {
	console.log('Hi!');
}

for(item in object_Or_Array) {
	// item is the INDEX
	statement();
}

var countries = ["China", "India", "Singapore"];
for(country in countries) {
	// console.log(country) --- WRONG
	console.log(countries[country]);
}
```

## Functions

```JavaScript
var myFunc = function(param1, param2) {
	// code goes here
	return returnValue;
}

function myFunc(param1, param2) {
	// code goes here
	return returnvalue;
}
```

NOTE: These are equivalent. Pretty much everything is an **Object** in JavaScript.

