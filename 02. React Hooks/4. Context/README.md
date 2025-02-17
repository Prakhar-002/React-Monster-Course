
<h1  align="center" > 🍄 𝐂ⱺ𐓣𝗍𝖾𝗑𝗍 𝐀𝐏𝚰 🥠</h1>

Context API is a feature that allows you to manage and
hare state across your component tree without having to
pass props down manually at every level. It's useful for
scenarios where you need to share data or functions
across many components, especially when these
components are deeply nested.

```JSX
//============ App.jsx ============== 

// 1. Importing (createContext)
import { createContext } from "react";
import ComponentA from "./ComponentA";

// 2. Creating instance of (createContext)
export const Data = createContext();
export const Data1 = createContext();

const App = () => {
  const name = "Prakhar";
  const age = 24;

  return (
    <>
      {/* 3. Wrapping our components into Provider component */}
      <Data.Provider value={name}>
        <Data1.Provider value={age}>
          <ComponentA />
        </Data1.Provider>
      </Data.Provider>
    </>
  );
};

export default App;

```

```JSX
//============ ComponentA.jsx ============== 

import ComponentB from "./ComponentB";

const ComponentA = () => {
  return <ComponentB />;
};

export default ComponentA;

```

```JSX
//============ ComponentB.jsx ============== 

import ComponentC from "./ComponentC";

const ComponentB = () => {
  return <ComponentC />;
};

export default ComponentB;

```

```JSX
//============ ComponentC.jsx ============== 

import { Data, Data1 } from "./App.jsx";

const ComponentC = () => {
  return (
    <>
      {/* 4. Consuimg/Accessing Data */}
      <Data.Consumer>
        {(name) => {
          // return <h1>My name is: {name}</h1>;
          return (
            <Data1.Consumer>
              {(age) => {
                return (
                  <h1>
                    My name is: {name} and I'm {age} years old.
                  </h1>
                );
              }}
            </Data1.Consumer>
          );
        }}
      </Data.Consumer>
    </>
  );
};

export default ComponentC;

```

<h1  align="center" > 🍄 υ𝗌𝖾𝐂ⱺ𐓣𝗍𝖾𝗑𝗍 𝐇ⱺⱺ𝗄 🥠</h1>

useContext Hook allows us to access the context values
provided by a Context object directly within a functional
component. Context provides a way to pass data through
the component tree without having to pass props down
manually at every level.


```JSX
//============ App.jsx ============== 

import ComponentA from "./ComponentA";

// 1. Importing (createContext)
import { createContext } from "react";

// 2. Creating instance of (createContext)
export const Data = createContext();
export const Data1 = createContext();

const App = () => {
  const name = "HuXn";
  const Age = 18;

  return (
    <>
      <Data.Provider value={name}>
        <Data1.Provider value={Age}>
          <ComponentA />
        </Data1.Provider>
      </Data.Provider>
    </>
  );
};

export default App;

```

```JSX
//============ ComponentA.jsx ============== 

import ComponentB from "./ComponentB";

const ComponentA = () => {
  return <ComponentB />;
};

export default ComponentA;

```


```JSX
//============ ComponentB.jsx ============== 

import ComponentC from "./ComponentC";

const ComponentB = () => {
  return <ComponentC />;
};

export default ComponentB;

```

```JSX
//============ ComponentC.jsx ============== 

import { useContext } from "react";
import { Data, Data1 } from "./App";

const ComponentC = () => {
  const userName = useContext(Data);
  const Age = useContext(Data1);

  return (
    <h1>
      My name is: {userName} & I'm {Age} years old.
    </h1>
  );
};

export default ComponentC;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise: Using Context and `useContext` in React

In this exercise, you will learn how to:

- Create a Context
- Use `useContext` to access data from the Context
- Share state and functions between components without using props

#### Step 1: Creating a Context

1. Create a new file called `UserContext.js`.
2. Inside this file, create a `UserContext` and a `UserProvider` component that will hold the shared state.

#### Step 2: Using `useContext` in Components

1. Create a new file called `UserProfile.jsx`.
2. Inside this file, create a functional component called `UserProfile`. This component will access the user data from `UserContext` using the `useContext` hook.

#### Step 3: Updating Context Data

1. Create a new file called `UpdateUser.jsx`.
2. Inside this file, create a functional component called `UpdateUser` that allows the user to update their name.

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```JSX
//============ App.jsx ============== 

import { UserProvider } from "./UserContext";
import UserProfile from "./components/UserProfile";
import UpdateUser from "./components/UpdateUser";

const App = () => {
  return (
    <UserProvider>
      <UserProfile />
      <UpdateUser />
    </UserProvider>
  );
};

export default App;

```

```JSX
//============ UserContext.jsx ============== 

import { createContext, useState } from "react";

// Create a Context
const UserContext = createContext();

// Create a Provider component
const UserProvider = ({ children }) => {
  const [user, setUser] = useState({ name: "John Doe" });

  const updateUser = (newName) => {
    setUser({ name: newName });
  };

  return (
    <UserContext.Provider value={{ user, updateUser }}>
      {children}
    </UserContext.Provider>
  );
};

export { UserContext, UserProvider };

```

```JSX
//============ components/UpdateUser.jsx ============== 

import { useContext, useState } from "react";
import { UserContext } from "../UserContext";

const UpdateUser = () => {
  const { updateUser } = useContext(UserContext);
  const [newName, setNewName] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();
    if (newName.trim()) {
      updateUser(newName);
      setNewName("");
    }
  };

  return (
    <div>
      <h2>Update User Name</h2>
      <form onSubmit={handleSubmit}>
        <input
          type="text"
          value={newName}
          onChange={(e) => setNewName(e.target.value)}
          placeholder="Enter new name"
        />
        <button type="submit">Update</button>
      </form>
    </div>
  );
};

export default UpdateUser;

```

```JSX
//============ components/UserProfile.jsx ============== 

import { useContext } from "react";
import { UserContext } from "../UserContext";

const UserProfile = () => {
  const { user } = useContext(UserContext);

  return (
    <div>
      <h1>User Profile</h1>
      <p>Name: {user.name}</p>
    </div>
  );
};

export default UserProfile;

```