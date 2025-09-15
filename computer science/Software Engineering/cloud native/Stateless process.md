In [[Microservice]] architecture we should not maintain any type of object or [[cache]] etc... in [[In-Memory]], because if any of the service if down then all the data will gone.

so for a example for [[cache]] instead of using a [[In-Memory]] caching, we need to use external caching server like [[Redis]].