
<h1  align="center" > 🍄 υ𝗌𝖾𝐑𝖾ᑯυ𝖼𝖾𝗋 🥠</h1>

```TSX

//============ App.tsx ============== 

"use client";

import Counter from "@/components/Counter";

export default function Home() {
  return (
    <>
      <Counter />
    </>
  );
}

```

```TSX

//============ components/reducer.tsx ============== 

import { useReducer } from "react";

// Define types for state and actions
type State = {
  count: number;
};

type Action = { type: "INCREMENT" } | { type: "DECREMENT" };

// Reducer function with types
const reducer = (state: State, action: Action): State => {
  switch (action.type) {
    case "INCREMENT":
      return { count: state.count + 1 };
    case "DECREMENT":
      return { count: state.count - 1 };
    default:
      return state;
  }
};

const Counter = () => {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: "INCREMENT" })}>Increment</button>
      <button onClick={() => dispatch({ type: "DECREMENT" })}>Decrement</button>
    </div>
  );
};

export default Counter;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

# Typing `useReducer`

## Objective

In this exercise, you'll practice using the `useReducer` hook with TypeScript. You will create a state management system using `useReducer` and type the actions, state, and reducer function to ensure type safety.

## Instructions

### Step 1: Define State and Actions

1. Create a file named `counterReducer.ts` in the `src` directory.

2. Define the types for the state and actions for counter:

### Step 2: Create the `Counter` Component

1. Create a file named `Counter.tsx` in the `src` directory.

2. Use `useReducer` to manage the counter state and actions in the component:

### Step 3: Use the Component in `App`

1. Open `App.tsx` (or create a new component if you prefer).

2. Import and use the `Counter` component:

   ```tsx
   // src/App.tsx
   import React from "react";
   import Counter from "./Counter";

   const App: React.FC = () => {
     return (
       <div>
         <h1>React + TypeScript Exercise</h1>
         <Counter />
       </div>
     );
   };

   export default App;
   ```

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```TSX

//============ App.tsx ============== 

import Counter from "./components/Counter";

const App = () => {
  return (
    <div>
      <Counter />
    </div>
  );
};

export default App;

```

```TSX

//============ components/Counter.tsx ============== 

import { useReducer } from "react";
import { counterReducer, CounterState } from "../reducers/counterReducer";

const initialState: CounterState = { count: 0 };

const Counter = () => {
  const [state, dispatch] = useReducer(counterReducer, initialState);

  const increment = () => {
    dispatch({ type: "INCREMENT" });
  };

  const decrement = () => {
    dispatch({ type: "DECREMENT" });
  };

  return (
    <div>
      <h2>Count: {state.count}</h2>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
};

export default Counter;

```

```TS

//============ reducers/counterReducer.ts ============== 

// Define the state type
export type CounterState = {
  count: number;
};

// Define action types
type IncrementAction = {
  type: "INCREMENT";
};

type DecrementAction = {
  type: "DECREMENT";
};

// Union type for actions
export type CounterAction = IncrementAction | DecrementAction;

// Define the reducer function
export const counterReducer = (
  state: CounterState,
  action: CounterAction
): CounterState => {
  switch (action.type) {
    case "INCREMENT":
      return { count: state.count + 1 };
    case "DECREMENT":
      return { count: state.count - 1 };
    default:
      return state;
  }
};

```