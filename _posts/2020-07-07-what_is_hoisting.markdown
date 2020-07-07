---
layout: post
title:      "What is hoisting?"
date:       2020-07-07 23:49:22 +0000
permalink:  what_is_hoisting
---


Hoisting is when variable and function decalarations are moved up (or hoisted) to the top of the current scope. (Key note: hoisting **only**  applies to **declarations**) Although, this isn't considered best practice,hoisting allows you to call on variables or invoke functions even before declaring it.

Hoisting happens in two phases: Compilation Phase and Execution Phase

**Compilation Phase**

In this phase, the JS compiler will look for variable and function declarations to evaluate. When it finds these declarations, the variable is stored in memory and the vaue of the variable is 'undefined'. As for function declarations, after the proprty is created and stored  in memory, the property points to the function's code and is  already defined.

In addition, a scope chain is created and 'this' is determined  for each declared variable or function.


**Execution Phase**
After all declarations have been compiled, the code is ran line by line.

### Hoisting with 'var' vs 'let'

When it comes to hoisting, the best practice is declaring variables at the top of their scope and only  using 'const' or  'let', but  sometimes, older code will use 'var' instead.

The difference between hoisting with 'let' and 'var' is that 'let' allows the variable to be limited in scope to the block it's located in. On the other hand, 'var' is scoped globally, which can lead to headaches later down the road when trying to debug code. Another difference is that, with 'let', you aren't allowed to redeclare the same variable in the same scope, but as for 'var', you are able to bypass  this and redeclare the same variable in the same scope.




