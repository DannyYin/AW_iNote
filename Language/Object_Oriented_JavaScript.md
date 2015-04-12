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

### What is 'this' bound to?

...the object found to the left of the dot where the containing function is called.

Input parameters to a function only have bindings when that function is actually running.
The keyword `this` behaves like a parameter in most of the important ways.

NOTE: The default value is <global>. When no value pass to the method invocation `undefined` is bound to the variable.

![this bounding](http://dl.dropbox.com/u/1725146/Screen%20Shot%202015-04-12%20at%209.00.33%20PM.png)

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

## Object Decorator Pattern

When writing software, code reuse is the practice of writing generalized code that can be relied upon to address a variety of similar goals.
Similar code should be factor out to reusable library code.

