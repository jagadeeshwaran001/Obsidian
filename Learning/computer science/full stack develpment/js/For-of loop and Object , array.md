it's important to know that a for of loop cannot work on an object directly, since an object is [[Non-Iterable]]

if the Object is creted by [[Object.create()]] Then the for-of loop only iterates the child inherited object keys only. This is the major advantage of the for-of.

`const car = {`
    `speed: 100,`
    `color: "blue"`
`}`
`for(prop of car) {`
    `console.log(prop)`
`}`

output: 
[[Uncaught TypeError]]: car is not iterable

Arrays are iterable.

`const colors = ['red','orange','yellow']`
`for (var color of colors) {`
    `console.log(color);`
`}`

output:

`red`
`orange`
`yellow`


To Iterate a object refer [[Iterate Object]]


