Debugging
----------

### Objectives

The debugging chapter explores how to use debuggers to find errors while the code is
running, consoles to log errors as they happen and defensive coding tips. This chapter
looks briefly at the browser debuggers and the Visual Studio debugger. The Console
Debugging topic focuses on the common methods available to all consoles and
techniques for grouping, timing, tracing and profiling. The defensive coding section
demonstrates how the JSLint utility can help you build more robust code by avoiding error
prone practices.

### Debugging Options

To debug your JavaScript application your choices are:
Using a true interactive debugger at runtime that allows breakpoints, evaluation, step
execution, call stacks and watches. This route is indivisibly coupled with the hosting
environment. Debuggers will require that the JavaScript is pulled in as part of a page.
Log output to the console or embedding log API calls in the JavaScript code itself. This
option doesn't allow you to stop the action and step through it, but will allow you to
load only the pure JavaScript file without loading an HTML page.
You can avoid many errors altogether with JSLint code quality tool. JSLint will help keep
you from obvious mistakes like undeclared variables and some less than obvious
mistakes like leaving trailing whitespace ("In JavaScript, a linefeed can be whitespace or
it can act as a semicolon. This replaces one ambiguity with another. - Douglas
Crockford").

### Debuggers

While consoles allow you to work with "pure" JavaScript, debuggers tend to be tightly
coupled with the environment, usually the browser. Each major browser has developer
tools that include a true runtime debugger.

