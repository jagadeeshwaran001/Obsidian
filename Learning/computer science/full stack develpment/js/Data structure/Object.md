Object are [[Hash tables]].
It is un-ordered and [[Non-Iterable]] key value pairs. 

The key must be [[unique]] in the [[Map]]

Objects also be created by using [[Object.create()]]

Objects are only [[Iterable]] only using [[Iterate Object]]

Directly assigning a object to variable will copy the [[Refernce]] of the object, so if we edit the copied [[Object]] it also alter the original [[Object]] 
const a = {speed : 100}
const b = a;
b.speed = 200
console.log(a.speed, b.speed); //200 , 200

The above behaviour is also works same for [[Array]]

The above issues can over come up through the [[[spread operator ...]]

`const car1 = {speed: 100}`
`const car 2 = {...car1}`
`car1.speed = 200`
`console.log(car1.speed, car2.speed) //100 200`


