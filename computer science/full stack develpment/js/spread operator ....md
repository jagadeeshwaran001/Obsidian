it is introduced in [[Es6]]

It is used to unpack a [[computer science/full stack develpment/js/Data structure/Object]].

It is the shortest and easyiest way to copy of a [[computer science/full stack develpment/js/Data structure/Object]] into a newly created [[computer science/full stack develpment/js/Data structure/Object]].

The spread operator allows you to pass all [[Array]] elements into a [[function]] without having to type them all individually

[[spread operator ...]] is used to [[concate]] [[Array]]s and [[computer science/full stack develpment/js/Data structure/Object]]s

`const fruits = ['apple', 'pear', 'plum']`
`const berries = ['blueberry', 'strawberry']`
`const fruitsAndBerries = [...fruits, ...berries] // concatenate`
`console.log(fruitsAndBerries); //['apple', 'pear', 'plum', 'blueberry', 'strawberry']`

`const flying = { wings: 2 }`
`const car = { wheels: 4 }`
`const flyingCar = {...flying, ...car}`
`console.log(flyingCar) // {wings: 2, wheels: 4}`

[[spread operator ...]] is also used to push a element without [[push()]] 

`let veggies = ['onion', 'parsley'];`
`veggies = [...veggies, 'carrot', 'beetroot'];`
`console.log(veggies); // ['onion', 'parsley', 'carrot', 'beetroot']`

can convert [[string]] to [[Array]] using [[spread operator ...]]

`const greeting = "Hello";`
`const arrayOfChars = [...greeting];`
`console.log(arrayOfChars); //  ['H', 'e', 'l', 'l', 'o']`

copy a [[computer science/full stack develpment/js/Data structure/Object]] values without assigning the [[Refernce]] but the actual values.

`const car1 = {speed: 100}`
`const car 2 = {...car1}`
`car1.speed = 200`
`console.log(car1.speed, car2.speed) //100 200`







