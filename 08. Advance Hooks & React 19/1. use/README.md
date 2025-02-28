
<h1  align="center" > 🍄 𝐔𝐒𝐄 🥠</h1>

<h2  align="center" > 🍄 1. 𝐖𝗂𝗍ɦⱺυ𝗍 𝐔𝗌𝖾 🥠</h2>

```TSX

//============ App.tsx ============== 

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

```TSX

//============ components/FetchTodo.tsx ============== 

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

```TSX

//============ App.tsx ============== 

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

```TSX

//============ components/AdminInfo.tsx ============== 

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
