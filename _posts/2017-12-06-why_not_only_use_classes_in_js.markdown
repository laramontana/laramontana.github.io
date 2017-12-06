---
layout: post
title:      "Why not only use classes in JS?"
date:       2017-12-06 17:55:06 +0000
permalink:  why_not_only_use_classes_in_js
---

For a person whose first programming language is one of object oriented ones like Ruby, it may be very confusing and uncomfortable to get familiar with JavaScript prototype concept. Most likely is was the main reason why `class` keyword was added to ES6, as it seems easier to wrap the head around. However there are couple of reasons why prototype approach is a crucial thing to learn. First of all, classes do not actually exist in JS. In fact it is a thin layer around prototype behaviour.  Therefore, secondly JS classes do not behave similarly by comparison to other languages. And it would be impossible to use all power of class without figuring out how prototypes work under the hood. 

The reason why it is a good idea to use prototype in the first place is that it makes your code more efficient. Since JavaScript is compiled in a browser, slow code may cause time-delays on the user’s side. Let us look at the example below:

```
function Robot(name) {
  this.name = name;
  this.sayHello = function() {
    console.log(`Hello humans, my name is ${this.name}!`);
  };
}

let jack = new Robot('Jack');
jack.sayHello();
// "Hello humans, my name is Jack!"

let lilly = new Robot('Lilly');
lilly.sayHello();
// "Hello humans, my name is Lilly!"
```

Although the output is the same (except for the certain name), it does not mean that for each of new object the same function `sayHello()` is invoked. Every time a new object is created, our constructor function is run, which declares a new function as a property of the new object. To fix that we can move the declaration of the `sayHello()` function to outside of the constructor `Robot()` function. This prevents the `sayHello()` function from being redeclared each time a new `Robot` is created. 

```
function Robot(name) {
  this.name = name;
}
```
In order to give each constructed `Robot` object access to `sayHello()` function, we assign this function as a `Robot` **prototype property**. 
```
Robot.prototype.sayHello = function() {
  console.log(`Hello humans, my name is ${this.name}`);
};

let lilly = new Robot('Lilly');
lilly.sayHello();
// "Hello humans, my name is Lilly!"
```
In the code above, when we call `new` it creates a new empty object, on which the constructor function `Robot()` gets called, which fills in that empty object with an attribute of `name` and makes it equal to a value of a passed argument, as `this` refers to a just created object. Finally, we assign the `sayHello()` function to a whole prototype of `Robot`, so any object created via `new Robot()` has access to this function. This way regardless of the number of objects produced from the `Robot` constructor, there will be only one declared `sayHello()`  function.

Let’s now have a look how we can wrap it into a ES6 class:
```
class Robot {
  constructor(name) {
    this.name = name;
  }

  sayHello() {
    console.log(`Hello humans, my name is ${this.name}`);
  }
}
```

There is still a constructor and a function, which is available for all objects of this class. However, there is a  way to prove that `Robot` is not a class:

```
typeof Robot
// function
```

Which means that if we call `new Robot()` now the exact same process will start, which was described earlier for prototype. This is important to keep in mind while working with classes, to stay confident and in control of what is happening behind the scenes, as well as to understand some limitations and scope-wise pitfalls of class pattern.  
