# Object Oriented JavaScript

## Scopes

### Lexical Scope

Global Scope can be shared between files. 
A variable without `var` infront of declearation will automatically assign to the **Global Scope**, therefore avoid doing this to prevent potential problem.

In JavaScript **only** function create scope, loop and expression statements do not create scope.

### Execution Contexts

When program runs it builds up storage systems for holding the variables and their values.
These *in memory scope* structures are called execution contexts.

#### Execution Contexts vs. Lexical Scopes

**Execution Contexts** (in memory scopes), they are built as they are running. 
A new execution context should be created every time you call a function, therefore, each lexical scope there may be many execution scopes created or none (Depend on the number of function has been called).

![Execution Context Explanation](http://dl.dropbox.com/u/1725146/Screen%20Shot%202015-04-12%20at%207.08.26%20PM.png)

## Closures

Function has access to all the variables fomr the scopes that surround it. 
**Closures** is any function that remains available after those outer scopes have returned.

A new context always gets created in the same context as its function was defined within.

![Closures Explanation](http://dl.dropbox.com/u/1725146/Screen%20Shot%202015-04-12%20at%207.23.01%20PM.png)

## this Keyword

`this` is an identifier to get the value bound to it, it gets bound to the correct object automatically.

`this` is easily the most widely misunderstood aspect of the languages.
Two major differences between a regular positional parameter and `this`.

- You do not need pick name for `this`
- Value binding is different. (5 ways)

### What is 'this' not bound to?

![this not bound to](http://dl.dropbox.com/u/1725146/Screen%20Shot%202015-04-12%20at%207.34.09%20PM.png)

**Sample Code**:

```JavaScript
var fn = function(a, b) {
	log(this); 
	// NOT bound to the function object this appears within
}
// NOT bound to an new instance of the function 'this' appears within

var ob1 = {method: fn};
// NOT bound to an object that happens to have that function as 
// a property

var ob2 = {
	fn: function(a, b) {
		log(this);
	}
};
// NOT bound to the object created by the literal `this` appear
// within

ob2.fn(3, 4);
// NOTE bound to an "execution context" or "scope" of that function
// call
```

### What is 'this' bound to?

...the object found to the left of the dot where the containing function is called.

```JavaScript
// BOUND to the object found to the left of the dot where the 
// containing function is called. 'ob2' in this case.
ob2.fn(3, 4);
```

Input parameters to a function only have bindings when that function is actually running.
The keyword `this` behaves like a parameter in most of the important ways.

NOTE: The **default** value is <global>. When no value pass to the method invocation `undefined` is bound to the variable.

![this bounding](http://dl.dropbox.com/u/1725146/Screen%20Shot%202015-04-12%20at%209.00.33%20PM.png)

#### Predicting Parameter Output Sample

```JavaScript
var fn = function(one, two) {
	log(this, one, two);
}
var r = {}, g = {}, b = {};

fn(g, b);
// <global>, g, b
// 'g' bind to 'one' and 'b' bind to 'two'
// but NOT ture for every function invocation

r.method = fn;

r.method(g, b);
// r, g, b
// focal object is the one on the left side of dot
// same to the left of the bracket
// r['method'](g, b);

fn.call(r, g, b);
// r, g, b
// using function '.call' method to override the default binding
// to global and override the left of the dot rule

r.method.call(y, g, b);
// y, g, b

setTimeout(fn, 1000);
// <global>, undefined, undefined

var setTimeout = function(callback, ms) {
	waitSomeTime(ms);
	callback(); // NO parameter at all while calling
};

setTimeout(r.method, 1000);
// <global> , undefined, undefined
// the argument passed in is a function object 
// nothing to do with 'r' object

setTimeout(function(){
	r.method()
	// r, undefined, undefined
}, 1000);

log(this);
// <global>
log(one);
// error

new r.method(g, b);
// 'a brand new object', g, b
```

## Prototype Chains

It is mechanism to make object resemble to other object. 

```JavaScript
var gold = {a: 1};
console.log(gold.a); // 1
console.log(gold.z); // undefined

// Simple One-time Copy
var blue = extend({}, gold); 
blue.b = 2;
console.log(blue.a); // 1
console.log(blue.b); // 2
console.log(blue.z); // undefined

// Set Up Prototype Chain
var rose = Object.create(gold);
rose.b = 2;
console.log(rose.a); // 1
console.log(rose.b); // 2
console.log(rose.z); // undefined

gold.z = 3;
console.log(blue.z); // undefined
console.log(rose.z); // 3
```

NOTE: There are special object, like `Array`. `Array Object` -> `Array Prototype` -> `Object Prototype`.

## Object Decorator Pattern (修饰模式)

Decorator accept an **object** as input.

When writing software, code reuse is the practice of writing generalized code that can be relied upon to address a variety of similar goals.
Similar code should be factor out to reusable library code.
[中文 Wikipedia](http://zh.wikipedia.org/wiki/%E4%BF%AE%E9%A5%B0%E6%A8%A1%E5%BC%8F)

**Sample Code**
```JavaScript
/*
 * Version 1.0
 */ 
var amy = {
	loc: 1
};
var ben = {
	loc: 9
};

amy.loc++;
console.log(amy.loc);
ben.loc++;
console.log(ben.loc);

/*
 * Version 2.0
 */

// Create Reuse Library
var move = function(car){
	car.loc += 1;
};

move(amy);
console.log(amy.loc);
move(ben);
console.log(ben.loc);

/*
 * Version 3.0
 */

var carlike = function(obj, loc) {
	obj.loc = loc;
	return obj;
}

var amy = carlike({}, 1);
var ben = carlike({}, 9);
move(amy);
move(ben);

/*
 * Version 4.0
 */
var carlike = function(obj, loc) {
  obj.loc = loc;
  obj.move = move;
  return obj;
};

var move = function(){
	this.loc += 1; // 'this' automatically bound to caller obj
};
var sheldon = carlike({}, 3);
sheldon.move(); 
// -> this.loc += 1 , this is bound to sheldon 
// its bound at runtime

/*
 * Version 5.0
 */

var carlike = function(obj, loc) {
  obj.loc = loc;
  obj.move = function(){
  	this.loc++;
  };
  return obj;
};

/*
 * Version 6.0
 */

var carlike = function(obj, loc) {
  obj.loc = loc;
  obj.move = function() {
      obj.loc++;
  };
  return obj;
};
```

NOTE: `===` asks about object identity, NOT merely value equality.

## Functional Classes

Class is a powerful form of functions that can be used to manufacture fleets of similar objects, a construct that is capable of building a fleet of similar objects that all conform to the same interface.
Function produce objects called *Constructor functions*.

NOTE: Name class with capitalised noun, like proper noun for a category. 

Short story, the **class** is the **category** and the **constructor** is the function that produce a new instance of that class, the process is known as **Instantiating**.
This is an example of the **Functional Class Pattern**.

```JavaScript
var Car = function(loc) {
	var obj = {loc: loc};
	obj.move = function() {
		obj.loc++;
	};
	return obj;
}

var amy = Car(1);
amy.move();
var ben = Car(9);
ben.move();
```

### Reducing Dupblicit

Move the duplicit part from the class and use `this` to refer the calling object.

```JavaScript
/*
 * Version 1.0
 */
var Car = function(loc) {
	var obj = {loc: loc};
	obj.move = move;               <--- 'move' here
	return obj;
}

// Functional shared patterns with SHARED methods
var move = function(){           <--- 'move' here
	this.loc++;
}

// However, keep `move` to two place seems hard to maintain

/*
 * Version 2.0
 */
var Car = function(loc) {
	var obj = {loc: loc};
	extends(obj, methods);
	// 'extends()' is NOT a native JavaScript function
	// Google for external library that implement it
	return obj;
}

// 'methods' current in the <global> scope
// This should be avoid
var methods = {
	move: function(){
		this.loc++;
	},
	on: function(){...},
	off: function(){...}
};

/*
 * Version 3.0
 */

// Functions are object and it can have its properties.
// This move the methods out the <global> scope
Car.methods = {
	move: function(){
		this.loc++;
	};
};
```

## Prototypal Classes 

Any object could delegate its failed property lookups to other object.

To improve the performance, instead of coping everything in `Car.methods` property which use **Prototye Chain**.
The common methods can be stored inside a share prototyle object.

Object literal do not allow you to define its *prototype*, using `Object.create()` allow developer to set classes' prototype. The default storage for methods is called `.prototype` which is automatically created for every object.

Every `property` object has a `.constructor` property which point back to the function which came attatch to.

```JavaScript
/*
 * Version 1.0 (Complete Prototype Pattern)
 */
var Car = function(loc){
	var obj = Object.create(Car.methods);
	obj.loc = loc;
	return obj;
};

Car.methods = {
	move: function(){
		this.loc++;
	}
};

/*
 * Version 2.0
 */
// Regular JavaScript Practice 
var Car = function(loc){
	var obj = Object.create(Car.prototype);
	obj.loc = loc;
	return obj;
};

// Storage place called 'prototype'
// 'prototype' is created automatically
Car.prototype.move = function(){
	this.loc++;
};
console.log(Car.prototype.constructor); // -> Car
console.log(amy.constructor); // -> Car
console.log(amy isinstanceof Car) // -> true
```

NOTE: Using `prototype` as methods container object for every object is really confusing.

Object one's prototype is object two -> failed property lookups on the first object should fall through to the second one.

Amy is Car object failed lookups on the Car object should fall through Car.prototype Object.

Car is function object failed to lookups on the function object should fall through function.prototype Object. The delegation using by Amy is created when Car function get called.

## Pseudoclassical Patterns

Pseudo-classical version is a layer of syntactic convenience over top of the prototypal pattern. 
The difference is the performance optimisation JavaScript engine implemented only apply when using the **pseudo-classical** patter.

With keyword `new` infront of function invocation, the function turning into a *special* model, the **Constructor Mode**, so some of the work can be done automatically.

```JavaScript
// Prototypal Pattern BEFORE USING 'new'
var Car = function(loc){
	var obj = Object.create(Car.prototype); // Repeated Line
	obj.loc = loc;                          // Repeated Line
	return obj;                        
}
Car.prototype.move = function(){
	this.loc++;
};

// When using 'new'
var Car = function(loc){
	this = Object.create(Car.prototype);    // With 'new' (hidden)
	// Your code here...
	this.loc = loc;                    
	return this;                            // With 'new' (hidden)
};
Car.prototype.move = function(){
	this.loc++;
};

/*
 * Final Version HERE
 */

var Car = function(loc){
	this.loc = loc;                    
};
Car.prototype.move = function(){
	this.loc++;
};
```

## Superclass and Subclasses

Subclass use the output from the Superclass as their starting potin.

```JavaScript
// Version 1.0 using Functional Class Pattern
var Car = function(loc){
	var obj = {loc: loc};
	obj.move = function(){
		obj.loc++;
	};
	return obj;
};

var Van = function(loc){
	var obj = Car(loc);
	obj.grab = function(){...};
	return obj;
};

var Cop = function(){
	var obj = Car(loc);
	obj.call = function(){...};
	return obj;
};

// Version 2.0
```

## Pseudoclassical JavaScript

Introducing `Object.create()` method and `Car.call()` mehtod.

NOTE: For prototype chainning, `Van.prototype = new Car()` is a misusage.

```JavaScript
var zed = new Car(3);
zed.move();

var amy = new Van(9);
amy.move();
amy.grab();

// Superclass
var Car = function(loc){
	this.loc = loc;
};
Car.prototype.move = function(){
	this.loc++;
};

// Subclass
var Van = function(loc){
	// this.loc = loc;     <-- WRONG
	// new Car(loc);       <-- WRONG
	// this = new Car(loc) <-- WRONG (NOT ALLOW Using Code)
	// Car(loc);           <-- WRONG
	Car.call(this, loc); //<-- RIGHT
}

// Currently 'Ven.prototype' delegate 'Object.prototype'
Van.prototype = Car.prototype                 // <-- WRONG
Van.prototype = Object.create(Car);           // <-- WRONG
Van.prototype = Object.create(Car.prototype); // <-- RIGHT
Van.prototype.constructor = Van               // <-- Link to object
Van.prototype.grab = function(){...}
```