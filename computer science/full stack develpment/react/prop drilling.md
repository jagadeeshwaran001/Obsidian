passing the [[props]] to multilevel component is known as props drilling, consider a situation where middle child class doesn't need that [[state]] props but still in receives the data.

This issues can be fixed  by two approaches

1. [[useContext]]
2. [[store]]