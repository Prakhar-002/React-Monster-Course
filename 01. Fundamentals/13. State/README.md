<h1  align="center" > 🍄 𝐒𝗍α𝗍𝖾 🥠</h1>

<h2  align="center" >𝐁α𝗌𝗂𝖼 𝐂ⱺυ𐓣𝗍𝖾𝗋</h2>

``` JSX

import { useState } from "react";

const Counter = () => {
  const [count, setCount] = useState(0);

  const increment = () => setCount(count + 1);
  const decrement = () => setCount(count - 1);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
    </div>
  );
};

const App = () => {
  return <Counter />;
};

export default App;

```

<h2  align="center" >𝐔ρᑯα𝗍𝗂𐓣𝗀 𝐀𝗋𝗋α𝗒𝗌</h2>

``` JSX

import { useState } from "react";

const App = () => {
  const [friends, setFriends] = useState(["Alex", "John"]);

  const addOne = () => setFriends([...friends, "HuXn"]);
  const removeOne = () => setFriends(friends.filter((f) => f !== "John"));
  const updateOne = () =>
    setFriends(friends.map((f) => (f === "Alex" ? "Alex Smith" : f)));

  return (
    <div>
      {friends.map((t) => (
        <li key={Math.random()}>{t}</li>
      ))}
      <button onClick={addOne}>Add One</button>
      <button onClick={removeOne}>Remove One</button>
      <button onClick={updateOne}>Update One</button>
    </div>
  );
};

export default App;

```

<h2  align="center" >𝐔ρᑯα𝗍𝗂𐓣𝗀 𝐎ᑲ𝗃𝖾𝖼𝗍</h2>

``` JSX

import { useState } from "react";

const App = () => {
  const [movie, setMovie] = useState({
    title: "Equalizer 3",
    ratings: 7,
  });

  const handleClick = () => {
    // 🥂 To tell react about state updates, we have to give react a brand new object.

    // 👉 LONG WAY
    // const copyMovie = {
    //   // This will copy all the properties, into the new object, and then we can change whatever we want in new object.
    //   ...movie,
    //   ratings: 5,
    // };
    // setMovie(copyMovie);

    // 👉 SHORT WAY
    setMovie({ ...movie, ratings: 5 });
  };

  return (
    <div>
      <h1>{movie.title}</h1>
      <p>{movie.ratings}</p>
      <button onClick={handleClick}>Change Ratings</button>
    </div>
  );
};

export default App;

```

<h2  align="center" >𝐔ρᑯα𝗍𝗂𐓣𝗀 𝐀𝗋𝗋α𝗒 𝐎𝖿 𝐎ᑲ𝗃𝖾𝖼𝗍𝗌</h2>

``` JSX

import { useState } from "react";

const App = () => {
  const [movies, setMovies] = useState([
    { id: 1, title: "Spider man", ratings: 3 },
    { id: 2, title: "Superman", ratings: 6 },
  ]);

  const handleClick = () => {
    setMovies(
      movies.map((m) => (m.id === 1 ? { ...movies, title: "John Wick 4" } : m))
    );
  };

  return (
    <div>
      {movies.map((movie) => (
        <li key={Math.random()}>{movie.title}</li>
      ))}
      <button onClick={handleClick}>Change Name</button>
    </div>
  );
};

export default App;

```

<h2  align="center" >𝐒ɦα𝗋𝗂𐓣𝗀 𝐒𝗍α𝗍𝖾</h2>

``` JSX

import { useState } from "react";
import ComponentTwo from "./ComponentTwo";
import ComponentOne from "./ComponentOne";

const App = () => {
  const [count, setCount] = useState(0);

  return (
    <section>
      <ComponentOne count={count} onClickHandler={() => setCount(count + 1)} />
      <ComponentTwo count={count} onClickHandler={() => setCount(count + 1)} />
    </section>
  );
};

export default App;

```

```JSX

const ComponentOne = ({ count, onClickHandler }) => {
  const handleClick = () => onClickHandler();

  return (
    <section>
      <p>{count}</p>
      <button onClick={handleClick}>increment</button>
    </section>
  );
};

export default ComponentOne;

```

```JSX

const ComponentTwo = ({ count, onClickHandler }) => {
  const handleClick = () => onClickHandler();

  return (
    <div>
      <p>{count}</p>
      <button onClick={handleClick}>Increment</button>
    </div>
  );
};

export default ComponentTwo;

```

<h2  align="center" >𝐏α𝗌𝗌𝗂𐓣𝗀 𝐅υ𐓣𝖼𝗍𝗂ⱺ𐓣 α𝗌 α 𝗏αᥣυ𝖾</h2>

``` JSX

//============ App.jsx ============== 

import ExampleOne from "./components/ExampleOne";
import ExampleTwo from "./components/ExampleTwo";
import ExampleThree from "./components/ExampleThree";

const App = () => {
  return (
    <div>
      <ExampleOne />
      <ExampleTwo />
      <ExampleThree />
    </div>
  );
};
export default App;

```

```JSX

//============ ExampleOne.jsx ============== 

import { useState } from "react";

const ExampleOne = () => {
  // Use a function to compute the initial state
  const [count, setCount] = useState(() => {
    // This function will only run on the initial render
    const initialCount = 10;
    return initialCount;
  });

  const increment = () => {
    setCount((prevCount) => prevCount + 1);
  };

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={increment}>Increment</button>
    </div>
  );
};

export default ExampleOne;

```

```JSX

//============ ExampleTwo.jsx ============== 

import { useState } from "react";

const ExampleTwo = () => {
  // Initialize state with a function that generates a random number
  const [randomNumber, setRandomNumber] = useState(() =>
    Math.floor(Math.random() * 100)
  );

  const generateNewRandomNumber = () => {
    const newNumber = Math.floor(Math.random() * 100);
    setRandomNumber(newNumber);
  };

  return (
    <div>
      <h1>Random Number: {randomNumber}</h1>
      <button onClick={generateNewRandomNumber}>Generate New Number</button>
    </div>
  );
};

export default ExampleTwo;

```

```JSX

//============ ExampleThree.jsx ============== 

import { useState, useEffect } from "react";

const ExampleThree = () => {
  // Initialize state from localStorage or default to an empty string
  const [name, setName] = useState(() => {
    const savedName = localStorage.getItem("name");
    return savedName ? JSON.parse(savedName) : "";
  });

  // Update localStorage whenever the name changes
  useEffect(() => {
    localStorage.setItem("name", JSON.stringify(name));
  }, [name]);

  const handleChange = (event) => {
    setName(event.target.value);
  };

  const handleClear = () => {
    setName("");
  };

  return (
    <div>
      <h1>Your Name: {name}</h1>
      <input
        type="text"
        value={name}
        onChange={handleChange}
        placeholder="Enter your name"
      />
      <button onClick={handleClear}>Clear Name</button>
    </div>
  );
};

export default ExampleThree;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise: Mastering `useState` in React

In this exercise, you’ll learn how to use the `useState` hook for managing state in various scenarios, including basic usage, arrays, objects, and arrays of objects.

#### Step 1: Basic Usage of `useState`

1. Create a new file called `Counter.jsx`.
2. Inside this file, create a functional component called `Counter`.
3. Use `useState` to manage a simple counter state.
   - Initialize the state with a value of `0`.
   - Create a button to increment the counter by `1` when clicked.
   - Display the current value of the counter.

#### Step 2: `useState` with an Array of Data

1. Create a new file called `TodoList.jsx`.
2. Inside this file, create a functional component called `TodoList`.
3. Use `useState` to manage an array of todo items.
   - Initialize the state with an empty array.
   - Create a form to add new todo items to the list.
   - Display the list of todo items.

#### Step 3: `useState` with an Object of Data

1. Create a new file called `Profile.jsx`.
2. Inside this file, create a functional component called `Profile`.
3. Use `useState` to manage an object with user profile information.
   - Initialize the state with an object containing `name` and `age`.
   - Provide input fields to update the `name` and `age`.
   - Display the updated profile information.

#### Step 4: `useState` with an Array of Objects

1. Create a new file called `ShoppingList.jsx`.
2. Inside this file, create a functional component called `ShoppingList`.
3. Use `useState` to manage an array of objects, where each object represents a shopping item with `name` and `quantity`.
   - Initialize the state with an empty array.
   - Create a form to add new items to the list.
   - Display the list of shopping items.

#### Step 5: Render All Components in `App.jsx`

1. In your `App.jsx` file, import the `Counter`, `TodoList`, `Profile`, and `ShoppingList` components:

   ```jsx
   import Counter from "./Counter";
   import TodoList from "./TodoList";
   import Profile from "./Profile";
   import ShoppingList from "./ShoppingList";
   ```

2. Inside the `App` component, render all four components:

   ```jsx
   function App() {
     return (
       <div>
         <h1>React useState Examples</h1>
         <Counter />
         <TodoList />
         <Profile />
         <ShoppingList />
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
import Profile from "./components/Profile";
import ShoppingList from "./components/ShoppingList";
import TodoList from "./components/TodoList";

function App() {
  return (
    <>
      <Counter />
      <TodoList />
      <Profile />
      <ShoppingList />
    </>
  );
}

export default App;

```

```JSX

//============ Counter.jsx ============== 

import { useState } from "react";

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
};

export default Counter;

```

```JSX

//============ ShoppingList.jsx ============== 

import { useState } from "react";

const ShoppingList = () => {
  // Initialize state with an empty array
  const [items, setItems] = useState([]);
  const [name, setName] = useState("");
  const [quantity, setQuantity] = useState("");

  // Function to handle form submission
  const handleSubmit = (e) => {
    e.preventDefault();

    if (!name || !quantity) return;

    // Create a new item object
    const newItem = {
      name,
      quantity: parseInt(quantity),
    };

    // Update the state with the new item
    setItems((prevItems) => [...prevItems, newItem]);

    // Clear input fields
    setName("");
    setQuantity("");
  };

  return (
    <div>
      <h1>Shopping List</h1>
      <form onSubmit={handleSubmit}>
        <input
          type="text"
          placeholder="Item name"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
        <input
          type="number"
          placeholder="Quantity"
          value={quantity}
          onChange={(e) => setQuantity(e.target.value)}
        />
        <button type="submit">Add Item</button>
      </form>

      <ul>
        {items.map((item, index) => (
          <li key={index}>
            {item.name} - Quantity: {item.quantity}
          </li>
        ))}
      </ul>
    </div>
  );
};

export default ShoppingList;

```

```JSX

//============ Profile.jsx ============== 

import { useState } from "react";

const Profile = () => {
  // Initialize state with an object containing name and age
  const [profile, setProfile] = useState({
    name: "",
    age: "",
  });

  // Handle input changes
  const handleChange = (e) => {
    const { name, value } = e.target;
    setProfile((prevProfile) => ({
      ...prevProfile,
      [name]: value,
    }));
  };

  return (
    <div>
      <h2>User Profile</h2>
      <div>
        <label>
          Name:
          <input
            type="text"
            name="name"
            value={profile.name}
            onChange={handleChange}
          />
        </label>
      </div>
      <div>
        <label>
          Age:
          <input
            type="number"
            name="age"
            value={profile.age}
            onChange={handleChange}
          />
        </label>
      </div>
      <h3>Profile Information</h3>
      <p>Name: {profile.name}</p>
      <p>Age: {profile.age}</p>
    </div>
  );
};

export default Profile;

```

```JSX

//============ TodoList.jsx ============== 

import React, { useState } from "react";

const TodoList = () => {
  // Initialize the state with an empty array
  const [todos, setTodos] = useState([]);
  const [inputValue, setInputValue] = useState("");

  // Handle form submission to add a new todo item
  const handleSubmit = (e) => {
    e.preventDefault();
    if (inputValue.trim()) {
      setTodos([...todos, inputValue]);
      setInputValue("");
    }
  };

  // Handle input change
  const handleChange = (e) => {
    setInputValue(e.target.value);
  };

  return (
    <div>
      <h1>Todo List</h1>
      <form onSubmit={handleSubmit}>
        <input
          type="text"
          value={inputValue}
          onChange={handleChange}
          placeholder="Add a new todo"
        />
        <button type="submit">Add Todo</button>
      </form>
      <ul>
        {todos.map((todo, index) => (
          <li key={index}>{todo}</li>
        ))}
      </ul>
    </div>
  );
};

export default TodoList;

```