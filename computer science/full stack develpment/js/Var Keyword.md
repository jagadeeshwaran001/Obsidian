Var is a old method to initialize a variable in js and its is global scoped.

Its important to read all the examples: 

eg 1: 

`//a is not a function scope but a global scope.`
`var a = 10`
`function f() {`
    `var b = 20`
    `console.log(a, b)`
`}`
`f();`
`console.log(a);`

output:

`10 20`
`10`

eg2: 

`// It cannot accessible from the outside a method or function`
`function f() {`

    // It can be accessible any
    // where within this function
    var a = 10;
    console.log(a)
`}`
`f();`

`// A cannot be accessible`
`// outside of function`
`console.log(a);`

output: [[ReferenceError]]

`10`
`ReferenceError: a is not defined`

eg3: 

`//var variable can re assigable`
`var a = 10`

`// User can re-declare`
`// variable using var`
`var a = 8`

`// User can update var variable`
`a = 7` 
`console.log(a);`

output:

`7`

eg4:

#hoisting
[[hoisting]]

`//This is example of hoisting`
`console.log(a);`
`var a = 10;`

output:
`undefined`



