Introduction
------------
### What You Need to Know

This Workshop expects that you have some familiarity with a programming language.
It is platform-agnostic in that we're discussing the base JavaScript language
without focusing particularly on the language host environment e.g. browsers, Windows
Metro apps, JavaScript frameworks, etc.  However, all the lessons in this workshop could be used directly in TestComplete

### What You Need to Have

The easiest way to run JavaScript code without much setup is to use a console application.
Here are a few popular browsers that come with their own JavaScript console:
Safari can be downloaded from ![](http://www.apple.com/safari/download/)
Chrome can be downloaded from ![](https://www.google.com/intl/en/chrome/browser/)
Firefox can be downloaded from ![](http://www.mozilla.org/en-US/firefox/new/)
Internet Explorer can be downloaded from ![](http://windows.microsoft.com/en-US/internet-explorer/downloads/ie/)
See the Consoles topic for more information on configuring the consoles and running
JavaScript code.

## How This Courseware is Organized

### Getting Started

In this chapter you'll learn how to configure a console application to start working
interactively with JavaScript.

### The Basics

This chapter provides the basics that make up the JavaScript language. The Variables and
Types topic explains the dynamic nature of JavaScript variables, how to determine the
variable type and basic operations with Numbers, Strings and Boolean variables. The
Operators topic starts with basic arithmetic and then explores how conversion between
types can lead to unexpected results. See the Comparisons topic to learn about
"truthiness" and the sometimes unexpected rules of type coercion. Use the information on
comparisons to branch and loop in the Control Structures topic.

### Funtions and Parameters

The construction and behavior of functions are discussed in this chapter, including
function parameters, arguments, storing functions in variables and passing functions as
parameters. You'll learn how to use a function as a callback for notification within another
function. You'll also learn how to construct and call unnamed, anonymous functions. This
chapter focuses on the rules for how variables are scoped inside and outside of functions
and how to control scope using call() and apply(). The explanation of scoping also
includes a breakdown of how hoisting works in JavaScript. The Closure topic discusses the
visibility of variables to functions defined inside of other functions.

### Native Objects

In this chapter you will learn about the built-in objects supported by JavaScript including
Numbers, Strings, Date and Arrays. The Strings topic demonstrates methods used to
search or manipulate a series of characters. The Arrays topic explains how arrays are
constructed and the methods used to slice-and-dice arrays into new arrangements. The
Math object topic explores the built-in math constants, basic methods for limiting and
rounding numbers, generating random numbers, manipulating exponents and logarithms
and trigonometric functions.

### Objects in JavaScript

This chapter explores how objects are created, initialized, extended and inherited in
JavaScript. The chapter also discusses the practical matter of simulating namespaces.
Along the way you'll see how objects are created in code and using literal notation, how
prototypes form a inheritance chain and the important topic of how execution context
effects the value of the this keyword.

### Regular Expressions

This chapter takes you on an organized tour of the regular expressions syntax, showing you
how to recognize complex string patterns and extract the portions you need. Then you'll
see how the RegExp object consumes regular expressions in JavaScript code.

### Date and Time Handling

In this chapter you'll learn the basics of the Date object including how to manipulate the
components of dates and times, work with local and international dates and times and
display dates and times in a limited number of formats. You'll learn how to extend the
reach of the Date object by performing custom formatting, add and subtract days,
calculate the difference between dates and work with time zones. You'll also learn some of
the design and implementation issues involved with storing date and time values. Finally,
the chapter introduces a couple of sample utility libraries that you can use to make the job
easier.

### Error Handling

This chapter explains how to handle error conditions raised in your JavaScript application
and coming from other sources. The chapter explores the built-in JavaScript error objects,
demonstrates how to throw exceptions and how to structure your application to capture
and handle exceptions. The chapter also shows how to ensure a consistent application
state, no matter what. Finally, this chapter shows how exception and resource protection
blocks behave when nested.

### Debugging

The debugging chapter explores how to use debuggers to find errors while the code is
running, consoles to log errors as they happen and defensive coding tips. This chapter
looks briefly at the browser debuggers and the Visual Studio debugger. The Console
Debugging topic focuses on the common methods available to all consoles and
techniques for grouping, timing, tracing and profiling. The defensive coding section
demonstrates how the JSLint utility can help you build more robust code by avoiding error
prone practices.

### Thirty Second History

JavaScript was authored by Brendan Eich at Netscape under the code name "Mocha" as a
light-weight interpreted language that would appeal to non-professional programmers.
JavaScript was pushed as a "little brother" to Java in much the same way that Microsoft's
Visual Basic was a little brother to C++. Before JavaScript, If you wanted to access HTML
objects you had to create, compile and package a Java applet. With JavaScript you could
script directly in a web page with little setup. The "Mocha" language morphed into
"LiveScript" and finally shipped as "JavaScript" with Netscape Navigator 2.0B3.

### The ECMAScript Standard
"ECMAScript, which sounds a little like a skin disease. Nobody really wants it." - Brendan Eich, InfoWorld, JavaScript creator ponders past, future
Microsoft was unable to license Sun Microsystems "Java" and instead called their
JavaScript implementation "JScript". The ECMAScript specification was formalized by
Netscape and Microsoft to standardize the JavaScript and JScript implementations. The
first edition of the ECMA-262 specification was adopted in June 1997. JavaScript, JScript
and ActionScript (for Adobe Flash) are all language implementations of the ECMA
standard.