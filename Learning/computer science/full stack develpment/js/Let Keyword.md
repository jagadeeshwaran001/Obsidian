Let is introduced in a [[Es6]]  and it has block level scope


Its important to read all the examples: 

eg1: In this code we cannot access the b outside of the func but a can accessible any descendance of the function which it is belongs to`

`let a = 10;`
`function f() {`
    `let b = 9`
    `console.log(b);`
    `console.log(a);`
`}`
`f();`



output: 

`9`
`10`

eg2:

`let a = 10;`
`function f() {`
    `if (true) {`
        `let b = 9`

        `// It prints 9`
        `console.log(b);`
    `}`

    `// It gives error as it`
    `// defined in if block`
    `console.log(b);`
`}`
`f()`

`// It prints 10 , but due to error programs stops and this line will not execute`
`console.log(a)`

output: [[ReferenceError]]

`9`
`ReferenceError: b is not defined`

eg3: `//We cannot redeclare a let variable but we can redeclare` [[Var Keyword]]

`let a = 10`

`// It is not allowed`
`let a = 10`

`// It is allowed`
`a = 10`

output: [[Uncaught SyntaxError]]

`Uncaught SyntaxError: Identifier 'a' has already been declared`

eg4: let variables when they are re-declared in the different scopes.

l`et a = 10`
`if (true) {`
    `let a = 9`
    `console.log(a) // It prints 9`
`}`
`console.log(a) // It prints 10`

output: 

`9`
`10`

eg5: This code explains the [[hoisting]] concept with the let variables.

console.log(a);
let a = 10;

output: [[Uncaught ReferenceError]]

`Uncaught ReferenceError: Cannot access 'a' before initialization`













