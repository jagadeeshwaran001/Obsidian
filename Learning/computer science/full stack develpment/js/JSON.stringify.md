This [[Method]] convers the js [[Object]] to [[JSON]] [[string]] .

`const  data = {name: "jagadeesh",age: "23"}`
`const jsonStr = [[JSON.stringify]](data);`
`console.log(jsonStr) // '{"name": "jagadeesh","age": "23"}'`

If we [[JSON.stringify]]  a object with a [[Method]] that method will be excluded from the result.

 eg: 
`const  data = {name: "jagadeesh",age: "23", fun: () => {console.log("hii")}}`
`consoel.log(JSON.stringify(data)); //'{"name":"jagadeesh","age":"23"}'`