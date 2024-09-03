It is like a [[Array]] because it is [[Iterable]].

With [[Map]] any values can be used as a key, but in [[Object]] only be [[string]] and symbols.

The key must be [[unique]] in the [[Map]]


keyValues pair -> Hash function -> Hash table.

we can create a new map using [[new Map();]]

A map can feel very similar to an object in JS.

However, it doesn't have [[Inheritance]]. No [[Prototypes]]! This makes it useful as a data storage.

`let bestBoxers = new Map();`
`bestBoxers.set(1, "The Champion");`
`bestBoxers.set(2, "The Runner-up");`
`bestBoxers.set(3, "The third place");`

`console.log(bestBoxers);`

output: 
`Map(3) {1 => 'The Champion', 2 => 'The Runner-up', 3 => 'The third place'}`

we can access the map items by the key using get methods:

`bestBoxers.get(1);`


