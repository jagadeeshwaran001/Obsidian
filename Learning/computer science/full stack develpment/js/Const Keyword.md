Eveything are same as the [[Let Keyword]] one addition is that the value of [[Const Keyword]] is not editable once after its declaration. and it is only supported in [[Es6]].

eg1: This code tries to change the value of the const variable.

`const a = 10;`
`function f() {`
    `a = 9`
    `console.log(a)`
`}`
`f();`

output: [[TypeError]]

`TypeError: Assignment to constant variable.`

eg2: This code explains the use of the [[const keyword]] to declare the [[Object]].

`const a = {`
    `prop1: 10,`
    `prop2: 9`
`}`

`// It is allowed`
`a.prop1 = 3`

`// It is not allowed`
`a = {`
    `b: 10,`
    `prop2: 9`
`}`

output:

`Uncaught SyntaxError: Unexpected identifier`

eg3: Since [[Const Keyword]] is not editable we need to specify the initial value, otherwise it throws [[Uncaught SyntaxError]]

`cosnt a;`

output: 

`Uncaught SyntaxError: Unexpected identifier 'a'`

