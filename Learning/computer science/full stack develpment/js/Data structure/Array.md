In [[js]] Array is also a type of special [[Object]], which key are the index like [0:"0",1: "1"]

[[Object]] are [[Non-Iterable]] but arrays are [[Iterable]].

[[typeof]] array is a [[Object]].

copying the array only assign the [[Refernce]] not the values this cause the below workflow.

`const a = [1,2]`
`const b = a;`
`b.pop()`
`console.log(a,b) // [1][1]`

the above issues can be overcome by using [[spread operator ...]]

