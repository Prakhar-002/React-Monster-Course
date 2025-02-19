
<h1  align="center" > 🍄 υ𝗌𝖾𝐑𝖾𝖿 🥠</h1>

useRef Hook provides a way to access and interact with DOM elements or to persist values across renders without causing a re-render.

```JSX

// useRef is use to manage any kind of DOM manipulations.
import { useRef } from "react";

function App() {
  const inputElement = useRef(null);

  const focusInput = () => {
    inputElement.current.focus();
    inputElement.current.value = "HuXn";
  };

  return (
    <>
      <input type="text" ref={inputElement} />
      <button onClick={() => focusInput()}>Focus & write HuXn</button>
    </>
  );
}

export default App;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise: Using `useRef` in React

In this exercise, you will learn how to:

- Use `useRef` to reference DOM elements.
- Use `useRef` to store values that persist between renders without triggering re-renders.

---

### Step 1: Accessing a DOM Element with `useRef`

1. Create a new file called `FocusInput.jsx`.
2. Inside this file, create a functional component that will focus on an input field when a button is clicked, using the `useRef` hook.

### Step 2: Persisting Values Between Renders with `useRef`

1. Create a new file called `Timer.jsx`.
2. Inside this file, create a component that implements a simple timer, where the timer’s interval is stored using `useRef`.

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```JSX

//============ App.jsx ============== 

import FocusInput from "./components/FocusInput";
import Timer from "./components/Timer";

function App() {
  return (
    <div>
      <FocusInput />
      <Timer />
    </div>
  );
}

export default App;

```

```JSX

//============ components/FocusInput.jsx ============== 

import { useRef } from "react";

const FocusInput = () => {
  const inputRef = useRef(null);

  const focusInput = () => {
    if (inputRef.current) {
      inputRef.current.focus();
    }
  };

  return (
    <div>
      <input
        ref={inputRef}
        type="text"
        placeholder="Click the button to focus"
      />
      <button onClick={focusInput}>Focus Input</button>
    </div>
  );
};

export default FocusInput;

```

```JSX

//============ components/Timer.jsx ============== 

import { useRef, useEffect, useState } from "react";

const Timer = () => {
  const [count, setCount] = useState(0);
  const intervalRef = useRef(null);

  useEffect(() => {
    intervalRef.current = setInterval(() => {
      setCount((prevCount) => prevCount + 1);
    }, 1000);

    return () => {
      clearInterval(intervalRef.current);
    };
  }, []);

  return (
    <div>
      <h1>Timer: {count} seconds</h1>
      <button onClick={() => clearInterval(intervalRef.current)}>
        Stop Timer
      </button>
    </div>
  );
};

export default Timer;

```