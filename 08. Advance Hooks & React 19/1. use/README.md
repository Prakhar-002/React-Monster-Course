
<h1  align="center" > 🍄 𝐔𝐒𝐄 🥠</h1>

The use() hook lets you read and load resources
asynchronously, such as promises or context. Unlike other
hooks, it can be utilized in loops and conditionals.

In certain situations, it can serve as a replacement for
useEffect() when fetching data, and it streamlines context
usage by allowing you to use use(context) instead of
useContext(contex).

<h2  align="center" > 🍄 1. 𝐖𝗂𝗍ɦⱺυ𝗍 𝐔𝗌𝖾 🥠</h2>

```JSX

//============ App.jsx ============== 

import { Suspense } from "react";
import FetchTodo from "./components/FetchTodo";

const App = () => {
  return (
    <Suspense>
      <FetchTodo />
    </Suspense>
  );
};

export default App;

```

```JSX

//============ components/FetchTodo.jsx ============== 

import { useState, useEffect } from "react";

const FetchTodo = () => {
  const [todo, setTodo] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const res = await fetch("https://jsonplaceholder.typicode.com/todos/1");
        const data = await res.json();
        setTodo(data);
        setLoading(false);
      } catch (error) {
        console.log(error);
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, []);

  if (loading) <h1>Loading...</h1>;

  return (
    <div>
      <h1>{todo?.title}</h1>
    </div>
  );
};

export default FetchTodo;

```

<h2  align="center" > 🍄 2. 𝐖𝗂𝗍ɦ 𝐔𝗌𝖾 🥠</h2>

```JSX

//============ App.jsx ============== 

import { Suspense } from "react";
import FetchTodo from "./components/FetchTodo";

const App = () => {
  return (
    <Suspense fallback={<h2>Loading...</h2>}>
      <FetchTodo />
    </Suspense>
  );
};

export default App;

```

```JSX

//============ components/AdminInfo.jsx ============== 

import { use } from "react";
// npm i react@experimental react-dom@experimental

const fetchData = async () => {
  const res = await fetch("https://jsonplaceholder.typicode.com/todos/1");
  return res.json();
};

const FetchTodo = () => {
  const data = use(fetchData());
  return <h1>{data.title}</h1>;
};

export default FetchTodo;

```
