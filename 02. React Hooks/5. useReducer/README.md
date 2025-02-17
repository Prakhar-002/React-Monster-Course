
<h1  align="center" > 🍄 υ𝗌𝖾𝐑𝖾ᑯυ𝖼𝖾𝗋 🥠</h1>

### useReducer is a hook that is similar to useState, but it is designed for more complex state objects or state transitions that involves multiple sub- values. It allows you to manage state in a functional, Immutable way.

![image](https://github.com/user-attachments/assets/7d373176-8f04-4d4c-8afd-7950c1f005d8)

```JSX

// ============ App.jsx ============== 

// The useReducer Hook is the alternative to useState Hook.
// If you find yourself keeping track of multiple pieces of state that rely on complex logic, useReducer may be useful.

// The useReducer Hook returns the current (state) and a (dispatch) method.

// State as the name suggest will be the "state" of your component.
// dispatch will allow you to change that state, Think of it is like [val, setVal]

// useReducer accepts two parameters (reducer, initialState)

// The reducer function contains your custom state logic
//  The initialState can be a simple value but generally will contain an object.

// 1 👇
import { useReducer } from "react";

const Counter = () => {
  // 2 👇
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      {/*  6 👇 */}
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
      <button onClick={() => dispatch({ type: "reset" })}>Reset</button>
      <h1>{state.count}</h1>
    </div>
  );
};

// 3 👇
const initialState = { count: 0 };

// 4 👇
const reducer = (state, action) => {
  // 5 👇
  switch (action.type) {
    case "increment":
      return {
        ...state,
        count: state.count + 1,
      };
    case "decrement":
      return {
        ...state,
        count: state.count - 1,
      };
    case "reset":
      return {
        ...state,
        count: 0,
      };
    default:
      return state;
  }
};

const App = () => {
  return <Counter />;
};

export default App;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise: Using `useReducer` in React

In this exercise, you will learn how to:

- Define a reducer function to manage state logic
- Use the `useReducer` hook to manage complex state in a React component
- Dispatch actions to update state

---

### Step 1: Setting Up the Reducer Function

1. Create a new file called `counterReducer.js`.
2. Inside this file, define a reducer function that will manage a simple counter's state.

### Step 2: Using `useReducer` Hook

1. Create a new file called `Counter.jsx`.
2. Inside this file, create a functional component called `Counter`.
3. Use the `useReducer` hook to manage the state of the counter.

### Step 3: Extending the Reducer with More Actions

1. Modify the `counterReducer.js` file to add more actions for increasing and decreasing by a specific amount.

### Step 4: Using Payloads in Actions

1. Update the `Counter.jsx` file to allow the user to increase or decrease the count by a specific value using an input field.

### Step 5: Rendering the Counter in `App.jsx`

1. In your `App.jsx` file, import and render the `Counter` component.

```jsx
import React from "react";
import Counter from "./Counter";

function App() {
  return (
    <div>
      <h1>React useReducer Example</h1>
      <Counter />
    </div>
  );
}

export default App;

```

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```JSX

//============ App.jsx ============== 

import Counter from "./components/Counter";

function App() {
  return (
    <div>
      <h1>React useReducer Example</h1>
      <Counter />
    </div>
  );
}

export default App;

```

```JSX

//============ Components/Counter.jsx ============== 

import { useReducer, useState } from "react";
import { counterReducer, initialState } from "../counterReducer";

function Counter() {
  const [state, dispatch] = useReducer(counterReducer, initialState);
  const [inputValue, setInputValue] = useState(0);

  const handleIncrement = () => dispatch({ type: "increment" });
  const handleDecrement = () => dispatch({ type: "decrement" });

  const handleIncrementByAmount = () => {
    dispatch({ type: "incrementByAmount", payload: Number(inputValue) });
    setInputValue(0); // Clear input after dispatch
  };

  const handleDecrementByAmount = () => {
    dispatch({ type: "decrementByAmount", payload: Number(inputValue) });
    setInputValue(0); // Clear input after dispatch
  };

  return (
    <div>
      <h2>Count: {state.count}</h2>
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleDecrement}>Decrement</button>
      <div>
        <input
          type="number"
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
        />
        <button onClick={handleIncrementByAmount}>Add</button>
        <button onClick={handleDecrementByAmount}>Subtract</button>
      </div>
    </div>
  );
}

export default Counter;

```

```JS

//============ counterReducer.js ============== 

const initialState = { count: 0 };

function counterReducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    case "incrementByAmount":
      return { count: state.count + action.payload };
    case "decrementByAmount":
      return { count: state.count - action.payload };
    default:
      return state;
  }
}

export { initialState, counterReducer };

```