---
layout: post
title:      "Arrow Functions vs Regular Functions"
date:       2020-09-05 20:15:28 +0000
permalink:  arrow_functions_vs_regular_functions
---


There are several ways to define functions in Javascript, but the most common two are arrow functions and regular functions (function declarations, function expressions). And although they share the same purpose of defining a function, their behaviors and context can be very different, depending on how you use them.

### Arrow Functions

Arrow functions are newer to Javascript and provides the benefit of writing shorter code, but the most important thing to remember is that they do not have their own ```this```. Because of this, the value of ```this``` is resolved lexically, meaning it equals the value of 'this' from the outer function of where the arrow function was defined. Arrow functions are best used for callbacks or iteration methods (e.g., map, reduce, forEach).

### Regular Functions

As for regular functions, the context of ```this``` is dynamic and depends on how the regular function is invoked. 

For ***simple invocation***, the value of ```this``` equals the global object.
```
function myFunc() {
  console.log(this);
}

myFunc();
// logs the global object (Window)
``` 

For ***method invocation***, the value of ```this``` is the object of where the method is defined.
```
const someObj = {
  method() {
	  console.log(this);
	}
};

someObj.method();
// this logs someObj
```

For  ***constructor invocation***, when used with the ```new``` keyword, the value of ```this``` equals the new instance of the object that was created.
```
function myFunc() {
  console.log(this);
}

new myFunc();
// logs an instance of myFunc
```

