# JavaScript

**JavaScript** was created in May 1995 by Brendan Eich. The original name was **Mocha**, a name chosen by Marc Andreessen. 

## Getting Up and Running

```
// print thing on console
console.log("Hello world!");
```

Introducing **jQuery**, read more click [here](https://jquery.com/).

JavaScript includes math operatos, `+`, `-`, `*`, `/`, `(` and `)`.

### Data Types

```
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

NOTE: Truthy evaluates to *true* and falsy evaluates to *false*. And there are two(2) special numeric values are `Infinity` and `-Infinity`.
`NaN` or Not a Number, is a value that turns up when user ask **JavaScript** to do impossible things in arithmetic. 
(e.g. Deivide zero by zero)

Use strick equal `===` and strict not equal `!==` in situations where truthy or falsy values could lead to logic errors.
These operators (`===` and `!==`) ensure that the objects are compared by type and by value.

Read more about "True Lies and Falsy Values in Python and JavaScript" 
[here](http://opensourcehacker.com/2012/10/17/true-lies-and-falsy-values-in-python-and-javascript/).

### Arrays

```
// number of item is 3
var array0 = [item1, item2, item3];
var len0 = array0.length // length is 2

// number of item is 4
var array1 = ["string",
			    3.1415,
			    {
				  "state": false
			    }, 
			    function(){return 0}
			   ];
var len1 = array1.length // length is 3
```

NOTE: Length of array is **NOT** equal to number of elements inside.

### Object

Object contains *information* and *tools* and there are no **Class** in **JavaScript**. 
*tools* are properties that contains function.

```
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

function Car() {...}

/*
var Car = function() {}
*/

// Construction mode with keyword 'new'
var car = new Car();
```

NOTE: *Dote Notation* and *Bracket Notation* (It's one more universal) are different with the properties you can access with.

### JSON

**JavaScript Object Notation**, a popular and simple format for storing and transferring nested or hierarchal data.
Internet GET and POST requests frequently pass data in JSON format.
JSON allows for objects to be easily encapsulated within other objects.

NOTE: If you create JSON by hand, test it using JSON linter, like [jsonlint.com](http://jsonlint.com/), or use text editor add-on, like *SublimeLinter*.

## Flow Control

### if Statement

```
if (condition) {
	statement;
} else {
	statement;
}
```

### Strick Equality vs. Loose Equality

More about **equality**, when use strick equality, `===`, no type conversion is done prior to the comparison. 
If the value are different types, they can never be **true**. 
(e.g. a `String` and a `Number`). 
In order to return **true**, the valuees must be equal and the types must be the same.

When using loose equality, `==`, if two values are not the same type, **JavaScript** converts values to a common type before the comparison.
If the types are the same, no difference between `===` and `==`.

NOTE: The recommandation is to **NEVER** use loose equality (`==`) because it is a frequent source of bugs.
Read more about equlity comparisons and sameness [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness).

## Loops

> Don't repeat yourself!

### while Loop

```
while(condition) {
	statement;
}
```

There is know *do-while* loop in **JavaScript**, therefore, using *loop-and-half* can be using to solve the similar issue.

```
while(true) {
    statement;
    if (condition) {
        break;
    }
}
```
### for Loop

```
for(initialisation; condition; mutator) {
	statement;
}

for(var i = 0; i < 3; i++) {
	console.log('Hi!');
}

for(item in object_Or_Array) {
	// item is INDEX, NOT real item inside Object or Array
	statement();
}

var countries = ["China", "India", "Singapore"];
for(country in countries) {
	// console.log(country) --- WRONG
	console.log(countries[country]);
}
```

## Functions

Funcitons in JavaScript are first class objects (means the language supports passing functions as arguments to other functions, returning them as the values from other functions, and assigning them to variables or storing them in data structures). 

Being able to pass logic around an application in the form of a function means it’s possible to move a lot of repetitive code into a library function. It makes it easier to separate the unique pieces of logic from the generally useful logic.

**Ways to Declear Function**

```
var myFunc = function(param1, param2) {
	// code goes here
	return returnValue;
}

function myFunc(param1, param2) {
	// code goes here
	return returnvalue;
}
```

NOTE: Above two are equivalent and pretty much everything is an **Object** in JavaScript.

## Scope

[Origin Post](http://toddmotto.com/everything-you-wanted-to-know-about-javascript-scope/)

JavaScript has a few concepts of "scope".

## What is Scope?

Scope refers to the current context of your code in JavaScript.
It can be globally or locally defined.
Understanding scope is key to writing bulletproof code and being a better developer.

### What is Global Scope?

Before any line of JavaScript code, you are in the `Global Scope`.

We are accessing jQuery in global scope, we can refer to this acess as the `namespace`.
The namespace is an interchangable word for scope, but usually refers to the highest level scope.

### What is Local Scope?

A local scope refers to any scode defined past the global scope.
There is one global scope and **each function defined has its own local scope**.

```
// Scope A: Global scope here
var myFunc = function() {
	// Scope B: Local scope here
}
```

Any locally scoped items are not visible in the global scope - unless exposed.

### Function Scope

All scopes in JavaScript are created with `Function Scope` only.
They are not created by `for` or `while` loops or expression statements.
The rule is **New function is new scope**.

```
// Scope A
function(){
	// Scope B
	function() {
		// Scope C
	}
}
```

### Lexical Scope

Function with another function, the **inner function has acesss to the scope in the outer function**.
This is called Lexical Scope or Closure - referred to as Static Scope.

```
//Scope A
var globalTime = 0000;
var myFunc = function() {
	// Scope B
	var name = 'Xinyang';
	var myOtherFunc = function(){
		// Scope C
		// `name` declear in Scope B is accessible here
		// `globalTime` declear in Scope A is accessible here
	}
}
```

Lexical scope is easy to work with, any vairbales/objects/functions defined in it's parent scode are available in the scope chain.
The **ONLY** important thing to remember is that Lexical scope does not work backwards.

### Scope Chain

Scope chains establish the scope for a given function. 
Each functino defined has its own nested scope and any function defined within another function has a local scope which is linked to the outer function - this link is called the **chain**.

When resolving a variable, JavaScript **always starts at the innermost scope** and searchs outwards until it finds the variable/object/function it was looking for.

### Closures

Closure ties in very closely with Lexical scope.

```
var sayHello = function(name) {
	var text = 'hello, ' + name;
	return function(){
		console.log(text);
	}
}

sayHello('Xinyang'); // nothing happens

var helloXinyang = sayHello('Xinyang');
helloXinyang(); // will call the closure and log 'hello, Xinyang'

// Alternatively

sayHello('Xinyang')(); // calls the returned function without arg 
```

### Scope and 'this'

Each scope binds a different value of `this` depending on how the function is invoked.
By default `this` refers to the outer most global object, the `window`.

```
var myFunction = function () {
  console.log(this); // this = global, [object Window]
};
myFunction();

var myObject = {};
myObject.myMethod = function () {
  console.log(this); // this = Object { myObject }
};
```

There are problems that we run into when dealing with `this` value. 
Even inside the same function the scope can be changed and the `this`value can be changed, hence, extra attention is necessary here.