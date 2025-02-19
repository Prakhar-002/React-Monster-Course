
<h1  align="center" > 🍄 𝐂υ𝗌𝗍ⱺꭑ 𝐇ⱺⱺ𝗄𝗌 🥠</h1>

```JSX

//============ App.jsx ============== 

// ---------------------------------------------------
// Hooks are reusable functions.
// When you have component logic that needs to be used by multiple components, we can extract that logic to a custom Hook.
// Custom Hooks start with "use". Example: useFetch.

// import { useState, useEffect } from "react";

// Typical Code 👇
// const Home = () => {
//   const [data, setData] = useState(null);

//   useEffect(() => {
//     fetch("https://jsonplaceholder.typicode.com/todos")
//       .then((res) => res.json())
//       .then((data) => setData(data));
//   }, []);

//   return (
//     <>
//       {data &&
//         data.map((item) => {
//           return <p key={item.id}>{item.title}</p>;
//         })}
//     </>
//   );
// };
// ---------------------------------------------------

// Now we'll extract the fetching data functionality into new file name (useFetch) and it'll be our custom hook.

// Importing our custom hook 👇
import useFetch from "./useFetch";

const Home = () => {
  // using our custom hook 👇
  const [data] = useFetch("https://jsonplaceholder.typicode.com/todos");

  return (
    <>
      {data &&
        data.map((item) => {
          return (
            <ul key={item.id}>
              <li>{item.title}</li>
            </ul>
          );
        })}
    </>
  );
};

const App = () => {
  return <Home />;
};

export default App;

```

```JSX

//============ Index.jsx ============== 

import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);

```

```JSX

//============ useFetch.jsx ============== 

import { useState, useEffect } from "react";

const useFetch = (url) => {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then((data) => setData(data));
  }, [url]);

  return [data];
};

export default useFetch;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise: Creating and Using Custom Hooks in React

In this exercise, you will learn how to:

- Create a custom hook that encapsulates state and logic.
- Reuse the custom hook in multiple components.
- Create hooks for handling form inputs and fetch data from an API.

---

### Step 1: Create a Custom Hook for Toggling a Boolean State

1. Create a new file called `useToggle.js`.
2. Inside this file, define a custom hook `useToggle` that toggles a boolean value between `true` and `false`.

### Step 2: Use the Custom Hook in a Component

1. Create a new file called `ToggleComponent.jsx`.
2. Inside this file, create a component that uses the `useToggle` hook to toggle a message.

### Step 3: Create a Custom Hook for Form Input Management

1. Create a new file called `useInput.js`.
2. Inside this file, define a custom hook `useInput` that handles form input changes.

### Step 4: Use the `useInput` Hook in a Form Component

1. Create a new file called `FormComponent.jsx`.
2. Inside this file, create a form component that uses the `useInput` hook to manage multiple input fields.

### Step 5: Create a Custom Hook for Fetching Data from an API

1. Create a new file called `useFetch.js`.
2. Inside this file, define a custom hook `useFetch` that fetches data from an API and returns the data, loading state, and any error.

### Step 6: Use the `useFetch` Hook to Fetch Data in a Component

1. Create a new file called `FetchComponent.jsx`.
2. Inside this file, create a component that uses the `useFetch` hook to display data from an API.

### Step 7: Render All Components in `App.jsx`

1. In your `App.jsx` file, import and render the `ToggleComponent`, `FormComponent`, and `FetchComponent` components.

```jsx
import React from "react";
import ToggleComponent from "./ToggleComponent";
import FormComponent from "./FormComponent";
import FetchComponent from "./FetchComponent";

function App() {
  return (
    <div>
      <h1>React Custom Hooks Examples</h1>
      <ToggleComponent />
      <FormComponent />
      <FetchComponent />
    </div>
  );
}

export default App;
```

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```JSX

//============ App.jsx ============== 

import FetchComponent from "./components/FetchComponent";
import FormComponent from "./components/FormComponent";
import ToggleComponent from "./components/ToggleComponent";

function App() {
  return (
    <div>
      <h1>React Custom Hooks Examples</h1>
      <ToggleComponent />
      <FormComponent />
      <FetchComponent />
    </div>
  );
}

export default App;

```

<h2  align="center" >📦 𝖼ⱺꭑρⱺ𐓣𝖾𐓣𝗍𝗌 📜</h2>

```JSX

//============ components/FetchComponent.jsx ============== 

import useFetch from "../hooks/useFetch";

const FetchComponent = () => {
  const { data, loading, error } = useFetch(
    "https://jsonplaceholder.typicode.com/posts"
  );

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <ul>
      {data.map((post) => (
        <li key={post.id}>{post.title}</li>
      ))}
    </ul>
  );
};

export default FetchComponent;

```

```JSX

//============ components/useInput.jsx ============== 

import useInput from "../hooks/useInput";

const FormComponent = () => {
  const name = useInput("");
  const email = useInput("");

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`Name: ${name.value}, Email: ${email.value}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label>
          Name:
          <input type="text" {...name} />
        </label>
      </div>
      <div>
        <label>
          Email:
          <input type="email" {...email} />
        </label>
      </div>
      <button type="submit">Submit</button>
    </form>
  );
};

export default FormComponent;

```

```JSX

//============ components/useToggle.jsx ============== 

import useToggle from "../hooks/useToggle";

const ToggleComponent = () => {
  const [isToggled, toggle] = useToggle();

  return (
    <div>
      <button onClick={toggle}>{isToggled ? "Hide" : "Show"} Message</button>
      {isToggled && <p>This is a toggled message!</p>}
    </div>
  );
};

export default ToggleComponent;

```

<h2  align="center" >🎣 𝐇ⱺⱺ𝗄𝗌 🦨</h2>

```JS

//============ hooks/useEffect.js ============== 

import { useEffect, useState } from "react";

const useFetch = (url) => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch(url);
        if (!response.ok) {
          throw new Error("Network response was not ok");
        }
        const result = await response.json();
        setData(result);
      } catch (error) {
        setError(error);
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, [url]);

  return { data, loading, error };
};

export default useFetch;

```

```JS

//============ hooks/useInput.js ============== 

import { useState } from "react";

const useInput = (initialValue = "") => {
  const [value, setValue] = useState(initialValue);

  const handleChange = (event) => {
    setValue(event.target.value);
  };

  return {
    value,
    onChange: handleChange,
  };
};

export default useInput;

```

```JS

//============ hooks/useToggle.js ============== 

import { useState } from "react";

const useToggle = (initialValue = false) => {
  const [value, setValue] = useState(initialValue);
  const toggle = () => setValue((prevValue) => !prevValue);
  return [value, toggle];
};

export default useToggle;

```