
<h1  align="center" > 🍄 υ𝗌𝖾𝐒𝗍α𝗍𝖾 𝐓𝗒ρ𝖾𝗌 🥠</h1>

```TSX

//============ Page.tsx ============== 

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

//============ components/Counter.tsx ============== 

// import { useState } from "react";

// const Counter = () => {
//   const [count, setCount] = useState<number>(0);

//   const increment = () => {
//     setCount(count + 1);
//   };

//   const decrement = () => {
//     setCount(count - 1);
//   };

//   return (
//     <div>
//       <h1>Counter App</h1>
//       <p>Count: {count}</p>
//       <button onClick={increment}>Increment</button>
//       <button onClick={decrement}>Decrement</button>
//     </div>
//   );
// };

// export default Counter;
// ---------------------------------
"use client";

import { useState } from "react";

const Counter = () => {
  const [count, setCount] = useState<number>(0);

  return (
    <div>
      <h1>Counter App</h1>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
};

export default Counter;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

# Typing the `useState` Hook

## Objective

In this exercise, you'll practice typing the `useState` hook in TypeScript. You will define state types for various use cases and apply them in functional components to ensure type safety and clarity.

## Instructions

### Step 2: Basic `useState` Typing

1. Open `App.tsx` (or create a new component if you prefer).

2. Define a state variable with `useState` and type it explicitly.

### Step 3: Typing Complex State

1. Create a new file named `UserProfile.tsx` in the `src` directory.

2. Define a state variable that holds an object with user profile information and type it accordingly:

### Step 4: Typing State with Arrays

1. Create a new file named `TodoList.tsx` in the `src` directory.

2. Define a state variable for a list of to-do items and type it accordingly:

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```TSX

//============ App.tsx ============== 

import { useState } from "react";
import UserProfile from "./components/UserProfile";
import TodoList from "./components/TodoList";

const App = () => {
  // Define a state variable for a counter
  const [count, setCount] = useState<number>(0);

  const increment = () => {
    setCount((prevCount) => prevCount + 1);
  };

  return (
    <div>
      <h1>Counter: {count}</h1>
      <button onClick={increment}>Increment</button>

      <UserProfile />
      <TodoList />
    </div>
  );
};

export default App;

```

```TSX

//============ TodoList.tsx ============== 

import { useState } from "react";

interface Todo {
  id: number;
  task: string;
  completed: boolean;
}

const TodoList: React.FC = () => {
  // Define a state variable for a list of to-do items
  const [todos, setTodos] = useState<Todo[]>([]);

  const addTodo = (task: string) => {
    const newTodo: Todo = {
      id: todos.length + 1,
      task,
      completed: false,
    };
    setTodos((prevTodos) => [...prevTodos, newTodo]);
  };

  return (
    <div>
      <h2>Todo List</h2>
      <button onClick={() => addTodo("New Todo")}>Add Todo</button>
      <ul>
        {todos.map((todo) => (
          <li key={todo.id}>
            {todo.task} {todo.completed ? "(Completed)" : ""}
          </li>
        ))}
      </ul>
    </div>
  );
};

export default TodoList;

```

```TSX

//============ UserProfile.tsx ============== 

import { useState } from "react";

interface UserProfile {
  name: string;
  age: number;
  email: string;
}

const UserProfile = () => {
  // Define a state variable for user profile
  const [profile, setProfile] = useState<UserProfile>({
    name: "",
    age: 0,
    email: "",
  });

  const updateName = (name: string) => {
    setProfile((prevProfile) => ({ ...prevProfile, name }));
  };

  const updateAge = (age: string) => {
    setProfile((prevProfile) => ({ ...prevProfile, age: Number(age) }));
  };

  const updateEmail = (email: string) => {
    setProfile((prevProfile) => ({ ...prevProfile, email }));
  };

  return (
    <div>
      <h2>User Profile</h2>
      <input
        type="text"
        placeholder="Name"
        value={profile.name}
        onChange={(e) => updateName(e.target.value)}
      />
      <input
        type="number"
        placeholder="Age"
        value={profile.age > 0 ? profile.age : ""}
        onChange={(e) => updateAge(e.target.value)}
      />
      <input
        type="email"
        placeholder="Email"
        value={profile.email}
        onChange={(e) => updateEmail(e.target.value)}
      />
      <h3>Profile Summary:</h3>
      <p>Name: {profile.name}</p>
      <p>Age: {profile.age}</p>
      <p>Email: {profile.email}</p>
    </div>
  );
};

export default UserProfile;

```