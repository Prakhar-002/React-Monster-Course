
<h1  align="center" > 🍄 υ𝗌𝖾𝐄𝖿𝖿𝖾𝖼𝗍 🥠</h1>

```JSX

//============ App.jsx ============== 

// We setup useEffect hook to run some code WHEN
//  👉 Component renders for the (First Time)
//  👉  & WHENEVER it re-renders
//  👉  & some data in our component changed.

import { useEffect, useState } from "react";

// 1. Without the empty array
// const App = () => {
//   const [value, setValue] = useState(0);
//   useEffect(() => {
//     console.log("call useEffect");
//     document.title = `Increment (${value})`;
//   });

//   return (
//     <>
//       <h2>{value}</h2>
//       <button onClick={() => setValue(value + 1)}>Click me</button>
//     </>
//   );
// };

// 2. useEffect - Conditional
// You cannot wrap hook with conditional statement
// If you want logic you'll have to put it inside your hook.
// const App = () => {
//   const [value, setValue] = useState(0);

//   useEffect(() => {
//     console.log("call useEffect");
//     if (value > 0) {
//       document.title = `Increment (${value})`;
//     }
//   });

//   return (
//     <>
//       <h2>{value}</h2>
//       <button onClick={() => setValue(value + 1)}>Click me</button>
//     </>
//   );
// };

// 3. useEffect - Dependency List
// empty array means (it will ONLY run on initial render)
// passing value to array means (it will re-render when that value changed)
// const App = () => {
//   const [value, setValue] = useState(0);

//   useEffect(() => {
//     console.log("call useEffect");
//     if (value > 0) {
//       document.title = `Increment (${value})`;
//     }
//   }, [value]);

//   return (
//     <>
//       <h2>{value}</h2>
//       <button onClick={() => setValue(value + 1)}>Click me</button>
//     </>
//   );
// };

// The cleanup can prevent memory leaks and remove unwanted things. Some use-cases for this are:

// Clean up subscriptions
// Clean up modals
// Remove event listeners
// Clear timeouts
// const App = () => {
//   const [size, setSize] = useState(window.innerWidth);
//   console.log(size);

//   const checkSize = () => setSize(window.innerWidth);

//   useEffect(() => {
//     window.addEventListener("resize", checkSize);
//     return () => {
//       // Before we add render our component again
//       // this cleanup function will cleanup the component first.
//       console.log("cleanup");
//       window.removeEventListener("resize", checkSize);
//     };
//   });

//   return (
//     <>
//       <h2>window</h2>
//       <h2>{size}px</h2>
//     </>
//   );
// };

// Fetching Data from 3rd party
const App = () => {
  const [data, setData] = useState([]);

  useEffect(() => {
    async function getData() {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/posts"
      );
      const data = await response.json();
      if (data && data.length) setData(data);
    }
    getData();
  }, []);

  return (
    <>
      <ul>
        {data.map((item) => (
          <li key={Math.random()}>{item.title}</li>
        ))}
      </ul>
    </>
  );
};

export default App;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise: Understanding `useEffect` in React

In this exercise, you’ll practice using the `useEffect` hook in different scenarios, including fetching data, handling side effects.

#### Step 1: Basic Usage of `useEffect`

1. Create a new file called `BasicEffect.jsx`.
2. Inside this file, create a functional component called `BasicEffect`.
3. Use `useEffect` to log a message to the console whenever the component mounts (i.e., when it’s rendered the first time).

#### Step 2: `useEffect` with Dependencies

1. Create a new file called `CounterEffect.jsx`.
2. Inside this file, create a functional component called `CounterEffect`.
3. Use `useEffect` to update the document title whenever a counter value changes.
   - Initialize a `count` state with `0` using `useState`.
   - Render a button that increments the count.
   - Use `useEffect` to update the document title whenever `count` changes.

#### Step 3: `useEffect` for Fetching Data

1. Create a new file called `FetchDataEffect.jsx`.
2. Inside this file, create a functional component called `FetchDataEffect`.
3. Use `useEffect` to fetch data from an API when the component mounts.
   - Use the API endpoint `https://jsonplaceholder.typicode.com/posts` to fetch some data.
   - Store the data in a state variable and display the title of the first post.

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```JSX

//============ App.jsx ============== 

import BasicEffect from "./components/1. BasicEffect";
import CounterEffect from "./components/2. CounterEffect";
import FetchDataEffect from "./components/3. FetchDataEffect";

const App = () => {
  return (
    <div>
      <BasicEffect />
      <CounterEffect />
      <FetchDataEffect />
    </div>
  );
};

export default App;

```

```JSX

//============ components/BasicEffect.jsx ============== 

import { useEffect } from "react";

const BasicEffect = () => {
  useEffect(() => {
    console.log("BasicEffect component mounted");
  }, []);

  return (
    <div>
      <h1>Check the console to see the message!</h1>
    </div>
  );
};

export default BasicEffect;

```

```JSX

//============ components/CounterEffect.jsx ============== 

import { useState, useEffect } from "react";

const CounterEffect = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};

export default CounterEffect;

```

```JSX

//============ components/FetchDataEffect.jsx ============== 

import { useState, useEffect } from "react";

const FetchDataEffect = () => {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    const fetchData = async () => {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/posts"
      );
      const data = await response.json();
      setPosts(data);
    };

    fetchData();
  }, []);

  return (
    <div>
      <h1>First Post Title:</h1>
      {posts.length > 0 ? <h2>{posts[0].title}</h2> : <p>Loading...</p>}
    </div>
  );
};

export default FetchDataEffect;

```