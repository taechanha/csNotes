# Javascript notes

---

Resources: 

- Udacity, Intro to Javascript
- Udacity, ES6
- [https://github.com/getify/You-Dont-Know-JS/tree/master/this%20%26%20object%20prototypes](https://github.com/getify/You-Dont-Know-JS/tree/master/this %26 object prototypes)
- https://medium.com/better-programming/prototypes-in-javascript-5bba2990e04b=

---

##Basics

### Data types

|   Type    | Passed by | Notes                                                        |      |      |      |
| :-------: | :-------: | ------------------------------------------------------------ | ---- | ---- | ---- |
|   bool    |           |                                                              |      |      |      |
|   null    |           | value = nothing                                              |      |      |      |
| undefined |           | absence of value                                             |      |      |      |
|  string   |           | \'\' is preferred over \" \" <br>\\ to escape                |      |      |      |
|  Number   |           | Positive, negative or decimal <br>Could be NaN if returns error |      |      |      |
|   Array   |    ref    |                                                              |      |      |      |
| function  |    ref    |                                                              |      |      |      |
|  Object   |    ref    |                                                              |      |      |      |



**Equality:**

​        `"1" == 1`returns `true`

​       ` 0==false` returns` true`

​        strict equality:` ===` (depends on type)

​		falsy turns false when evaluated in context of boolean expression. (ie.` false, null, undefined, 0, \"\", NaN`)

---

**concatenation**: "hello"+ 5*10 -> hello50

​		in strings, don't have to do \n anymore. 

​		`'${teacher.name} please see ${teacher}'`

**comments**: //, /* */

**ternary operator**: `var color = isGoing ? "green" : "red"` //where isGoing is bool

`switch (option) {`

​        `case 1: \n ....\n  case 2: \n ..`.

​       ` default:` (will fall through and execute this too)

**variables**: 

​	` 	let`- could change later 

​	`const` - won't change

 and const 

 **loops**

```Python
while (x <= 1000) {
}
for (var i = 0; i < 6; i += 1) {
	i++ //returns i and then implements the addition
	++i //implements addition then returns i 
```



---

### Functions

*functions are objects! 

a constructor is just a function that has "new" in front of it

**Prototype**: javascript automatically adds the "prototype" property to a function object.

​        func.prototype.constructor() points directly back to func

​        obj.\_\__proto\_\_ points to the prototype object. \_\_proto\_\_ = "dunder proto"

​        func.prototype===obj.\_\_proto\_\_

​        you can add a property/method to the prototype object. func.prototype.prop = "field"

​            and the rest of the objects created from that construction (with 'new') will be updated with that field 

​            when you do obj.prop, it will first see if obj has a property named prop, then go into obj.prototype's properties 

​		<center>![img ](https://cdn-images-1.medium.com/max/1600/1*5qHhF8HTzZD2xdx3p-RLIQ.png) </center>

**Example**

```python
function heat(a, b) {
	return "hi";
}
```

​    //if there's no return value, undefined will be returned automatically



  **scope:** 

​        can reassign variables from higher in the scope. (everything is by reference...)

​            "shadowing"

  **hoisting** - function declarations are hoisted to the top of the current scope, so you can use them before they're declared

​        in functions, variable declarations are always hoisted to the top of the scope, but not the assignment. so if you did `var x = 6 `later, it would be undefined at the top of the scope but assigned later.

​		NOT FOR LET OR CONST!

or: **function expression** (not hoisted!)

​    `var func = function(max)` { //anonymous function, but can also be named (function name(max))

​        lwejfwoie.....

​       ` return cat`

   ` };`

​    `func();`

​    func will return the function code

​    can use func as an argument for another function! 

​    if a function would only be used once, you can declare inline:

  `  func(function display(x) { console.log("hi")}, "param2");`

​    or can just declare function as usual



**default parameters (es6):** function func(param = 1 )

- `Func([a=5, b=5] = []) {  //func() `can also be called, will invoke [a, b]



#### arrow functions (es6)

​		paramName => returnValue

​       ` const upperizedNames = ['Kaili', 'Kevin'].map(name => name.toUpperCase()); `(name is the parameter/elem, and changes it.

​        ALWAYS EXPRESSIONS. stored in a variable, passed as an argument to a function, or stored in object's property 

​        if there are 0 or >1 parameters, do: 

​            `const sayHi = () => console.log('hello'); //or could use _ instead of ()`

​            `or const sayHi = (param1, param2) => .... `

block body syntax: 

```javascript
name => { //multiline, use curly braces and return keyword
	name = name.toUpperCase();
	return '${name}';}
```



​    with "this":

​        'this' is based on context. 'this' within arrow function is the same as outside arrow function

​        refers to what obj called the func



#### Generator functions (es6)

```javascript
function* getEmployee() { //or function * getEmployee(), or function *getEmployee()
    //implementation
    yield;
    //more code
    yield 12; //returns 12 when next().value is called
    const input = yield;
    
}
const generIter = getEmployee(); //doesn't actually run; it returns an iterator. 
generIter.next(); //will execute until 'yield' or the end of the function
const twelve = generIter.next();
generIter.next(52); //will be stored into input. sends data into generator
//this first stores data, and then exectues the next lines 
```





---



### arrays

var donuts = [1, 2, 3]`

can mix data types

methods/properties:

- length

- push() -> adds to the end of an array (array.push(3));

- pop() -> removes element from end of array

-  splice(indexLoc, numToRemove, elemToAdd, elemToAdd, etc.)

​        

forEach (only for arrays)

-  **_array_.forEach()**=(func); //where func is the name of a function, func(element), or func(element, index, array)

​        or __array__.forEach(function(param) {

​            ..s ...

​        });



- **.map(func)** //returns new array, doesn't modify the old one. func has to have "return elem" at the end 

- **.filter**(condition function that returns true or false)

**destructuring** 

​			specifying elements you want to extract from array on left side:`const [x, y, z] = point; //where point = [a, b, c]`

​       	 ignoring elements: `const [x, , z] = point;`

​			for a function : ` func([undefined], [a, b, c]]); `when `function func([scoops = default, topping = [1, 2, 3]]);`



​			



---



### Objects

​    includes arrays

​    `var obj = {};`

​    or: 

```javascript
var obj = { //this is object-literal notation
  color: "pink", //key: value 
	isOpen: false,
	open: function() {
}
```

​    data structure that allows you to store any data. 

​    **typeof \_\_** -> returns the type

​    **property vs method** 

​        obj.prop or obj["prop"] (dot vs bracket notation)

​        obj.method()

​        property names: don't use numbers as the first character in property names

​            don't use spaces or hyphens either

​	**destructuring** - `const {prop1, prop2, prop3} = obj; `//given that those are the actual property names

​	 **object literal shorthand**

​        if the variables are the same names as the fields, then just do 

​            `let objName = {field1, field2, field3}; `//assumign fields are vars with values 

​       	 `let objName = {field1, method1() {...}};`





### Classes



```javascript
class Plane { //plane is actually just a function! 
    constructor(numEngines) { //automatically runs whenenver this class object is created 
        this.field = numEngines
    }
    
    startEngines() { //can call through planeName.startEngines()
        this.field2 = true;
    }
    
    static badWeather(planes) { //call through Plane.badWeather(planes)
        for (plane of planes) {
            plane.enginesActive = false;
        }
    }
    
}

const myPlane = new Plane(1); //MUST use new keyword
```



#### Subclasses

```javascript
class boeing747 extends Plane { //subclass of Plane
    constructor(numEngines, year) {
        super(numEngines); //call to super class MUST be made before 'this' is used
        this.year = year;
    }
}
```



### Timing Events

##### setInterval(functionExpression, milliseconds, [arguments from functionExpression]) 

- runs a function multiple times with a delay between each run 
- stopped by clearInterval(timer)

##### setTimeout(functionExpression, milliseconds)

- function won't be executed until specified number of millis
- stopped by clearTimeout(timer)

```javascript
let timerId = setTimeout(func, 1000); //func, not func()! because func() would give return value
clearTimeout(timerId); //quits the timer 
```



## es6, harmony, es2015



   ### iteration



there is a new iterable protocol

**for...in loop** - elimates counting logic and exit condition.

- `for (const index in digits) { `//where digits is an array //index is literally the index, not the elem

- doesn't really work if you add another method to an object (will loop over this property too)

**for...of loop** - loops over anything that is iterable

- for (const digit of digits) { //digit is literally an elem

​        

​        //continue goes to the next iteration of the loop immediately 

**Iterator Protocol** - a standard way an object produces a sequence of values. Can define how an object iterates

```javascript
const digits = [1, 2, 3];
const arrayIter = digits[Symbol.iterator]();

//arrayIter.next() will return 1
```



- implements `.next()`, which returns an object with two properties:
  - `value` - represents the next value in the sequence
  - `done` - boolean representing if iterator is done. 





### Set



Works similarly to an array, but is not index-based, and items in a set can't be accessed individually. A set stores unique items, which can be primitive values or objects (can mix and match)

#### Creating a set:

```javascript
const games = new Set();

//OR

const games = new Set([1, 2, 3]);
```

#### Methods and properties

- .add(value);
- .delete() //if isn't already there, then won't receive an error. just won't do anything
- .clear()
- .size
- .has(value) //returns boolean
- .values() //returns a SetIterator object of the values in the set
  - can iterate over them with .next()
- for...of //loop through items
  - `for (const color of colors)`

#### WeakSet

A Set with the following differences:

- can only contain objects
- not iterable (can't be looped over)
- does not have the clear() method

Useful because it automatically deletes references to deleted objects during **garbage collection**. 



### Maps

Map is an object that stores key-value pairs where both keys and values can be objects or primitives

Sets: Arrays as Maps: Objects

```javascript
//creating a map
const mapName = new Map();
//unlike sets, CAN'T CREATE MAPS FROM LIST OF VALUES

//modifying:
mapName.set('key', {value1: a, value2: b}); //takes key and value
mapName.has('key') //returns true;
mapName.get('key') //returns the value
const keys = mapName.keys(); //returns all the keys as a MapIterator object
const values = mapName.values(); //returns all values as a MapIterator object 

mapName.delete('key'); //returns true if successful
mapName.clear(); 
```

To loop through a map, there are three options:

```javascript
//1. step through each key using Map's default iterator
let mapIter = members.keys();
mapIter.next() //returns the next key

//2. for...of loop
for (const member of memberMap) {
    //each member is ['key', value];
}

//3. forEach loop
members.forEach((value, key) => console.log(key, value));
```

#### WeakMaps

Can only contain objects as keys, not iterable (can't be looped), and doesn't have clear() method

Leverages **garbage collection** for maintainability





### Promises

Allows you to start some work asynchronously while you get back to your regular work. 

```javascript
//immediately returns the Promise object 
const promise = new Promise(function(resolve, reject) { //typical parameter names
    //code that will be run asynchronously
    resolve(); //this should be called when request completes successfully
    if (requestFailed) {
        reject();
    }
});

//notifies whether the promise was successful or failed. 
promise.then({resolve()}, {reject()});
```

*more info on promises in udacity course on promises



### spread & rest operator (…)



**Spread**

​        expands/spreads iterable objects into multiple elements

​        `console.log(...arr); `which prints all the elements in array arr, separated by spaces 

 **rest** parameter: represents indefinite number of elements as an array

​        ...items = arr //where you don't know how many elements arr is  (boxing the elements)



**variadic functions**: takes an indefinite number of arguments 

​            `function sum(...nums) {`



### this

In order of priority:       

1. new binding

​           ` var bar = new foo(2); //'this' within foo will refer to bar `

2. explicit binding (with call(obj))

   hardbinding can't change what var bar = foo.call(obj) binds to 

3. implicit binding

   `obj1.foo()`

   implicit lost: whenenver references link back to original function

4. default binding: points at global object, or undefined if in `"use strict";`

​            

### Symbols

A unique and immutable data type that is used to identify object properties. 

`const sym1 = Symbol('description');`

If two symbols have the same description, that does not mean that they are the same. 

So, you can make multiple symbols with the same description and not override any. 



### Proxies

Allows one object to represent another object and handle all those interactions

```javascript
let agent = new Proxy(originalObject, {list_of_methods_it_will_handle_for_the_object});
//second parameter object is called the handler

//for example, the get trap
//this will happen be invoked when agent.propName is called, where propName is a property of the original Object. 
//doesn't matter what propName is 
const handler = {get(target, propName) { //target is the originalObject 
    //stuff
	}
    //set trap: intercepts code that will change a property
	set(target, propName, value) {
        target[propName] = value;
    }                
}
agent = new Proxy(originalObject, handler);


```

other traps:

- apply
- has
- and 11 others 

It's like getters and setters, but you don't need to know the properties! 



## Javascript and browsers

Source: https://www.smashingmagazine.com/2012/11/writing-fast-memory-efficient-javascript/



### Polyfill

Definition: a piece of code/plugin that provides technology that expect the browser to provide natively. It sort of fills up any broken holes in your code. 



### Transpiling

A subcategory of compiling

It can convert es6 to es5, or human-readable code to other human-readable code 

Javascript's most popular transpiler: Babel



### Javascript engine and optimizing code



#### V8 

is the javascript engine in Chrome and Node

Represents objects in object model (represents objects as hidden classes, optimizes lookups)

Has:

- base compiler (parses js)

- runtime profiler: monitors system, identifies "hot" functions

- optimizing compiler: recompiles and optimizes the "hot" functions identified, such as using inlining (insetting functions in the body of the callee)

- can deoptimize, if it overassumed (?)

- garbage collector 

  - form of memory management. 
  - Objects that are still referenced by application are not cleaned up. 
  - Will automatically clean if you **STORE VARIABLES AS LOCALLY AS POSSIBLE.** variables will get cleaned up once out of scope 
    - If you `return` an object, then it will wait longer to be cleaned up than if you didn't return. 

  - will never clean up global variables as long as the page is open. 

  

#### Tips:

Memory leak is common with loops or timers. Whatever the setTimeout or setInterval is referencing has to be kept alive!!

STORE VARIABLES AS LOCALLY AS POSSIBLE

If you `return` an object, then it will wait longer to be cleaned up than if you didn't return. 

You can't (and shouldn't) force garbage collection! 

AVOID USING `delete`!!!!

- it was supposed to be used just for removing keys from a map
- if you set a variable to null, then garbage collector will remove the original object 

You can template and add functions/fields to the object.prototype, but benefits are negligible 

Don't load from uninitialized or deleted elements. This won't make a difference in output, but it will make things slower.

Don't write enormous functions, as they are more difficult to optimize

Avoid copying big things. And avoid using for...in loops for it. If you have to copy objects, use an array or custom "copy constructor" function, like: 

```javascript
function clone(original) {
  this.foo = original.foo;
  this.bar = original.bar;
}
var copy = new clone(original);
```





**Objects vs. Arrays:**

> If you want to store a bunch of numbers, or a list of objects of the same type, use an array.
>
> If what you semantically need is an object with a bunch of properties (of varying types), use an object with properties. **That’s pretty efficient in terms of memory, and it’s also pretty fast.**
>
> **Integer-indexed elements**, regardless of whether they’re stored in an array or an object, are [much faster to iterate over than object properties](http://jsperf.com/performance-of-array-vs-object/3).
>
> Properties on objects are quite complex: they can be created with setters, and with differing enumerability and writability. Items in arrays aren’t able to be customized as heavily — they either exist or they don’t. At an engine level, this allows for more optimization in terms of organizing the memory representing the structure. This is particularly beneficial when the array contains numbers. For example, when you need vectors, don’t define a class with properties x, y, z; use an array instead..



#### Arrays

Array literals are better (because it tells the size and type)

```javascript
// Here V8 can see that you want a 4-element array containing numbers:
var a = [1, 2, 3, 4];

// Don't do this:
a = []; // Here V8 knows nothing about the array
for(var i = 1; i <= 4; i++) {
     a.push(i);
}
```

Don't mix types within the same array! 

Avoid holes in array (deleting a[x])



#### Work cycle and Technique

- Measure it: Find the slow spots in your application (~45%)
- Understand it: Find out what the actual problem is (~45%)
- Fix it! (~10%)

Use Profiling in devtools 



## Package.json

This file specifies which packages your project depends on. 

- Dependencies: packages required by application for production
  - npm install <package-name> [--save-prod]
- DevDependencies: packages just required by testing

