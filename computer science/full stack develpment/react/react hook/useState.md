In [[React]] [[useState]] hook allows us to track state in a functional component.

useState accepts an initial state and returns [[array destructure]]d two values.

first value of a destructured array is current value
second value is function updates our state.

if out state is set by the set fuction the components get re-rendered.

# do's and don't

### don't

```jsx
import { useState } from "react"; 
export default function App() {
  const [greeting, setGreeting] = useState({ greet: "Hello, World" }); 
  console.log(greeting, setGreeting); 
  function updateGreeting() { 
    setGreeting({ greet: "Hello, World-Wide Web" }); 
  } 
  return ( 
    <div> 
      <h1>{greeting.greet}</h1> 
      <button onClick={updateGreeting}>Update greeting</button> 
    </div> 
  ); 
}
```

While this works, it's not the recommended way of working with state objects in React, this is because the state object usually has more than a single property, and it is costly to update the entire object just for the sake of updating only a small part of it.

### The correct way to do is 

```jsx
import { useState } from "react"; 
export default function App() { 
  const [greeting, setGreeting] = useState({ greet: "Hello, World" }); 
  console.log(greeting, setGreeting); 
  function updateGreeting() { 
    const newGreeting = {...greeting}; 
    newGreeting.greet = "Hello, World-Wide Web"; 
    setGreeting(newGreeting); 
  } 

  return ( 
    <div> 
      <h1>{greeting.greet}</h1> 
      <button onClick={updateGreeting}>Update greeting</button> 
    </div> 
  ); 
}
```

### dont

To prove that a copy of the old state object is needed to update state, let’s explore what happens when you try to update the old state object directly:

```jsx
import { useState } from "react"; 

export default function App() { 
  const [greeting, setGreeting] = useState({ greet: "Hello, World" }); 
  console.log(greeting, setGreeting); 

  function updateGreeting() { 
    greeting = {greet: "Hello, World-Wide Web}; 
    setGreeting(greeting); 
  } 
  return ( 
    <div> 
      <h1>{greeting.greet}</h1> 
      <button onClick={updateGreeting}>Update greeting</button> 
    </div> 
  ); 
}
```

The above code does not work because it has a TypeError hiding inside of it.
Specifically, the TypeError is: "Assignment to constant variable".

In other words, you cannot reassign a variable declared using `const`, such as in the case of the useState hook's

```jsx
import { useState } from "react"; 
export default function App() { 
  const [greeting, setGreeting] = useState({ greet: "Hello, World" }); 

  console.log(greeting, setGreeting); 

  function updateGreeting() { 
    greeting.greet = "Hello, World-Wide Web; 
    setGreeting(greeting); 
  } 
  return ( 
    <div> 
      <h1>{greeting.greet}</h1> 
      <button onClick={updateGreeting}>Update greeting</button> 
    </div> 
  ); 

}
```
The above code is problematic because it doesn't throw any errors; however, it also doesn't update the heading, so it is not working correctly. This means that, regardless of how many times you click the "Update greeting" button, it will still be "Hello, World".

To reiterate, the proper way of working with state when it's saved as an object is to:

1. Copy the old state object using the spread (...) operator and save it into a new variable and 
    
2. Pass the new variable to the state-updating function

### The correct way to do is

```jsx
import { useState } from "react"; 
export default function App() { 
  const [greeting, setGreeting] = useState({greet: "Hello", place: "World"}); 

  console.log(greeting, setGreeting); 

  function updateGreeting() { 
    setGreeting(prevState => { 
        return {...prevState, place: "World-Wide Web"} 
    }); 
  } 

  return ( 
    <div> 
      <h1>{greeting.greet}, {greeting.place}</h1> 
      <button onClick={updateGreeting}>Update greeting</button> 
    </div> 
  ); 
}
```
The reason this works is because it uses the previous state, which is named `prevState`, and this is the previous value of the greeting variable. In other words, it makes a copy of the `prevState` object, and updates only the place property on the copied object. It then returns a brand-new object: