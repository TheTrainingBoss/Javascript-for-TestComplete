## Functions and Parameters

### Objectives

The construction and behavior of functions are discussed in this chapter, including
function parameters, arguments, storing functions in variables and passing functions as
parameters. You'll learn how to use a function as a callback for notification within another
function. You'll also learn how to construct and call unnamed, anonymous functions. This
chapter focuses on the rules for how variables are scoped inside and outside of functions
and how to control scope using call() and apply(). The explanation of scoping also
includes a breakdown of how hoisting works in JavaScript. The Closure topic discusses the
visibility of variables to functions defined inside of other functions.

### Functions in JavaScript

Functions are the fundamental units of JavaScript that hold statements and are called from
other locations in the code. Functions are first class citizens: objects that can be stored in
variables, passed as parameters, returned from other functions and constructed at runtime.
The example below shows the basic function structure and the function being called.
Notice the "use strict" added as the first line of the function. This is a best-practice to
eliminate some of the flakier aspects of the JavaScript language and should be used inside
all of your functions.

```
// define a function
function myFunction() {
"use strict";
// statements
}
myFunction(); // call the function
```

Functions can accept one or more parameters and may also return a value to the caller.

```
function myFunction(param1, param2, param3) {
"use strict";
return 123;
}
```

Functions are objects and can be assigned to a variable. In the example below,
"compliment" is a variable that holds a function. Passing the variable through the typeof
operator verifies that "compliment" is in fact, a function.

```
var compliment = function () {
"use strict";
var compliments = [
"Outstanding",
"Well done",
"Nice haircut",
"Cool",
"Awesome"
],
random = Math.floor(Math.random() * 5);
return compliments[random];
};
console.log(typeof (compliment)); // "function"
console.log(compliment()); // outputs random compliment
```

Now that the function is stored in a variable, we can pass that function variable to other
functions or even pass the variable back out of a function. The example below passes the
"compliment" into a "saySomethingNice()" function and then directly back out to the
"attaBoy" variable. "saySomethingNice()" isn't really doing anything other than
demonstrating that you can pass the function variable. Finally, "attaBoy" can be called
simply by appending parenthesis.

```
var compliment = function () {
"use strict";
var compliments = [
"Outstanding",
"Well done",
"Nice haircut",
"Cool",
"Awesome"
],
random = Math.floor(Math.random() * 5);
return compliments[random];
};
function saySomethingNice(somethingNice) {
"use strict";
return somethingNice;
}
var attaBoy = saySomethingNice(compliment);
console.log(attaBoy());
```

### Parameters and Arguments

The number of arguments passed to the function does not need to match the number of
parameters. Extra arguments are ignored, too few leave parameters "undefined". The
"getTotal()" method below only uses the "discount" parameter if it is defined:

```
function getTotal(price, qty, discount) {
"use strict";
var total;
total = price * qty;
if (discount !== undefined) {
total += total / discount;
}
console.log(total);
}
getTotal(123.45, 10, 5); // outputs 1481.4
```

The return statement sends back a value to the caller and marks the exit point of the
function. The "getTotal()" method returns immediately with a zero if the first two
parameters are zero, otherwise the function returns the total amount:

```
function getTotal(price, qty, discount) {
"use strict";
var total;
// return zero if price or quantity is zero
if ((price === 0) || (qty === 0)) {
return 0;
}
total = price * qty;
// calculate a discount if the discount param is passed
if (discount !== undefined) {
total += total / discount;
}
return total;
}
var total = getTotal(123.45, 10, 5);
console.log(total);
```

You don't have to define parameters in advance or know how many parameters there are.
Functions have an arguments property that contains an array of everything passed to the
function. You can use the argument's length property to iterate the array.

```
function feedFishies() {
"use strict";
var numberOfFishies = arguments.length,
i;
for (i = 0; i < numberOfFishies; i += 1) {
console.log("Feeding " + arguments[i]);
}
}
feedFishies("Blue fish", "Green fish", "Yellow fish");
// Ouputs:
// "Feeding Blue fish"
// "Feeding Green fish"
// "Feeding Yellow fish"
```

The function arguments parameter is not a true array. Although it has the length
property, you can't call split(), join() or any of the other array methods.

### Callbacks

Once you can pass a function reference to another function, then you can implement
callbacks. Callbacks are used to notify a function from within another function. The
"process()" function in the example below takes a reference to a function and calls it
repeatedly while looping when a loop counter variable lands on a multiple of 10. The
example checks that the callback variable is a "function" type before making each call.

```
// function that accepts a callback reference
function process(callback) {
"use strict";
var i;
for (i = 10; i < 100; i += 1) {
if (i % 10 === 0) {
if (typeof (callback) === "function") {
callback(i);
}
}
}
}
// the function to be called
function myCallback(value) {
"use strict";
console.log(value);
}
// pass a callback function to another function
process(myCallback);
```

### Anonymous Functions

To create an anonymous function, leave out the function name. The example below assigns
an anonymous function to the variable "process".

```
var process = function () {
"use strict";
console.log("processing");
};
process();
```

To self-invoke an anonymous function, surround the function with parenthesis and then
add a second set of parenthesis to invoke the function. This structure is often used to
contain code so that will not leak out into the global scope. The new parenthesis are bold
and red in the example below.

```
(function () {
"use strict";
console.log("processing");
}());
```

### Scope

JavaScript variables can be scoped globally, locally to a function or to the execution
context:
- Global scope: Undeclared variables and variables declared outside of functions are global. These variables belong to the global scope, typically the window.
- Local scope: Variables prefixed with the var keyword inside of functions are stored as local copies (not references). Local variables are not available outside the scope of the function.
- Execution Context Scope: The keyword this refers to the current execution scope. Pepending "this" associates a variable with the current execution context. What that execution context actually is depends on how that context is created.

The global and local scopes in the code sample below are the most intuitive to
understand. "myGlobal" is undeclared and is automatically part of the global scope. This
would be true even if the assignment took place inside a function or object.
"myOtherGlobal" is declared using the var keyword, but is outside the scope of a function
so is part of the global scope as well. "myPrivateVariable" is declared using the var
keyword inside the function and so is only visible inside the function.

```
myGlobal = "undeclared global";
var myOtherGlobal = "declared global";
// available anywhere
console.log(myGlobal + ", " + myOtherGlobal);
function myFunc() {
"use strict";
var myPrivateVariable = "private";
console.log(myPrivateVariable); // only visible here
}
myFunc();
```

The execution context scope using the this keyword is a good deal trickier because the
value of this changes depending on how we invoke code that contains this. Outside a
function, this is the global object, i.e. the Window. Inside a function call, the scope is still
the global object. If the function is constructed as an object using the new keyword, this
points to the object.

Take a look at the following code fragment and try to predict the value of this in each

```
01 console.log(this);
02
03 function myFunc() {
04 "use strict";
05
06 console.log(this);
07 this.myMethod = function () {
08 console.log(this);
09 };
10 }
11
12 myFunc();
13
14 var mf = new myFunc();
15 mf.myMethod();
```

Now check screenshot below to see console output.

![](../media/image13.png)

At line 1, this is the global object, i.e. the Window. The next time this is logged is at line
06 after myFunc is called as a function from line 12. On line 13, the new keyword calls
myFunc as a constructor, so that line 06 logs this as the myFunc object. Finally, when
myMethod() is invoked at line 15, myFunc has been instantiated as an object with the new
keyword, so that line 08 reports that this is the myFunc object.

### Controlling Scope: call() and apply()

Functions have call() and apply() methods that allow you to pass in the scope that will be
used in the function. The only difference between the two is that call() takes a list of
parameters and apply() takes a single array as a parameter. The function call() and apply
() methods effectively overwrite the execution context represented by the this keyword.
The example below creates two objects using literal notation. The speak() function refers
to the this.sound property without specifying what "this" is. All functions have a call()
method. The call() method from speak is used to pass the dog and cat objects.

```
(function () {
"use strict";
var dog = {
sound: "Woof"
},
cat = {
sound: "Meow"
};
function speak() {
console.log(this.sound);
}
speak.call(dog, null); // Woof
speak.call(cat, null); // Meow
}());
```

You can pass a list of one or more parameters to call().

```
(function () {
"use strict";
var dog = {
sound: "Woof"
},
cat = {
sound: "Meow"
};
function speak(name, age) {
console.log(name + " is " + age + " and says " + this.sound);
}
// output "peanut is 2 and says Woof"
speak.call(dog, "peanut", 2);
// output "fluffy is 5 and says Meow"
speak.call(cat, "fluffy", 5);
}());
```

The apply() method passes parameters in a single array. You only need to replace call()
with apply() and pass the parameters as a single array. The function signature does not
need to change.

```
speak.apply(dog, ["peanut", 2]);
speak.apply(cat, ["fluffy", 5]);
```

### Best Practice and Hoisting

It's best practice to declare all variables at the top of functions. Why? In JavaScript, a
variable can be used before it is defined. JavaScript automatically hoists every var
declaration to the top of the function. A variable that is simply undeclared generates an
error:

```
function playTune() {
"use strict";
console.log("Volume is " + volume);
}
playTune(); // ReferenceError: "Volume is not defined"
```

Now take a look at this example where "volume" is declared after its used in a logging
statement:

```
function playTune() {
"use strict";
console.log("Volume is " + volume);
var volume = 1;
}
playTune(); // outputs "Volume is undefined"
```

The log prints "Volume is undefined", exactly the behavior you'd expect for a declared, but
uninitialized variable. While the declaration is moved to the top, the variable initialization
does not get hoisted. Re-writing the function to match its actual behavior looks more like
this example, with the declaration up top, and the assignment in its original location:

```
function playTune() {
"use strict";
var volume;
console.log("Volume is " + volume);
volume = 1;
}
```

This behavior may be confusing if you come from a C-family language background. While
JavaScript looks like a C-family language, JavaScript scoping rules are entirely different. Cfamily
languages use block level scoping where anything inside of curly braces {} has its
own scope. Take a look at the following pseudo-code:

```
playTune()
{
var volume = 1;
log(volume); // 1
// establish block level scope
if (true)
{
var volume = 7;
log(volume); // 7
} // end of block
log(volume); // 1
}
```

Using block scoping rules, the output is 1, 7, 1. The declaration inside the "if" statement is
only in scope within the curly braces. JavaScript uses function level scoping. "volume" is
hoisted to a single definition at the top of the function. The output is now 1, 7, 7.

```
01 function playTune() {
02 "use strict";
03
04 var volume = 1; // 1
05
06 console.log("Volume is " + volume);
07 if (true) {
08 var volume = 7;
09 console.log("Volume is " + volume); // 7
10 }
11 console.log("Volume is " + volume); // 7
12 }
```

By wrapping a section of code with a self-invoking anonymous function, we get the benefit
of block level scoping. The example below now outputs 1 at line 06, 7 inside the
anonymous function at line 11 and 1 again, outside the anonymous function at line 14.

```
01 function playTune() {
02 "use strict";
03
04 var volume = 1;
05
06 console.log("Volume is " + volume); // 1
07 if (true) {
08
09 (function () {
10 var volume = 7;
11 console.log("Volume is " + volume); // 7
12 }());
13 }
14 console.log("Volume is " + volume); // 1
15 }
```

### Closure

When a function is defined inside another function, the inner function has access to the
outer function's variables, even if the outer function has returned. This link to the outer
function's local variables is called a closure. The example below defines a function "outer
()" that returns another function "inner()". "inner()" can access "localVar", even after "outer
()" has been called and returned. Even though "localVar" is defined in the outer function, it
is "closed in" to the inner function. Functions run in the scope where they're defined, not
where the function is executed, so the outer function variables come along for the ride
during the entire lifetime of the inner function.

```
function outer() {
"use strict";
var localVar = 123;
return function inner() {
console.log(localVar);
};
}
var inner = outer();
inner(); // outputs "123"
```

### Summary

The construction and behavior of functions were discussed in this chapter, including
function parameters, arguments, storing functions in variables and passing functions as
parameters. You learned how to use a function as a callback for notification within another
function. You also learned how to construct and call unnamed, anonymous functions. This
chapter focused on the rules for how variables are scoped inside and outside of functions
and how to control scope using call() and apply(). The explanation of scoping included a
breakdown of how hoisting works in JavaScript. The Closure topic discussed the visibility of
variables to functions defined inside of other functions.