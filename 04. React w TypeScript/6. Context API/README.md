
<h1  align="center" > 🍄 𝐂ⱺ𐓣𝗍𝖾𝗑𝗍 𝐀𝐏𝚰 🥠</h1>

<h2  align="center" > 💡 𝐄𝗑αꭑρᥣ𝖾 1️⃣ 🧋</h2>

```TSX

//============ App.tsx ============== 

"use client";

import MyComponent from "@/components/MyComponent";
import { MyContextProvider } from "@/context/MyContext";

export default function Home() {
  return (
    <>
      <MyContextProvider>
        <MyComponent />
      </MyContextProvider>
    </>
  );
}

```

```TSX

//============ components/MyComponent.tsx ============== 

import { useContext } from "react";
import MyContext from "../context/MyContext";

const MyComponent = () => {
  const context = useContext(MyContext);

  if (!context) {
    throw new Error("MyComponent must be used within a MyContextProvider");
  }

  const { value, setValue } = context;

  return (
    <div>
      <p>Value: {value}</p>
      <input
        type="text"
        value={value}
        onChange={(e) => setValue(e.target.value)}
      />
    </div>
  );
};

export default MyComponent;

```

```TSX

//============ context/MyContext.tsx ============== 

import { createContext, type ReactNode, useState, FC } from "react";

// Define a type for your context data
type MyContextData = {
  value: string;
  setValue: (newValue: string) => void;
};

// Create a context with an initial value
const MyContext = createContext<MyContextData | undefined>(undefined);

// Create a provider component
type MyContextProviderProps = {
  children: ReactNode;
};

export const MyContextProvider: FC<MyContextProviderProps> = ({ children }) => {
  const [value, setValue] = useState<string>("");

  const contextValue: MyContextData = {
    value,
    setValue,
  };

  return (
    <MyContext.Provider value={contextValue}>{children}</MyContext.Provider>
  );
};

export default MyContext;

```

<h2  align="center" > 💡 𝐄𝗑αꭑρᥣ𝖾 2️⃣ 🧋</h2>

```TSX

//============ App.tsx ============== 

"use client";

import MyComponent from "@/components/MyComponent";
import MyProvider from "@/context/MyContext";

export default function Home() {
  return (
    <>
      <MyProvider>
        <MyComponent />
      </MyProvider>
    </>
  );
}

```

```TSX

//============ components/MyComponent.tsx ============== 

import { useContext } from "react";
import { MyContext } from "../context/MyContext";

const MyComponent: React.FC = () => {
  const { count, increment, decrement } = useContext(MyContext);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
};

export default MyComponent;

```

```TSX

//============ context/MyContext.tsx ============== 

import { createContext, useState, type ReactNode, type FC } from "react";

// Step 1: Create a context
interface MyContextProps {
  count: number;
  increment: () => void;
  decrement: () => void;
}

export const MyContext = createContext<MyContextProps>({
  count: 0,
  increment: () => {},
  decrement: () => {},
});

// Step 2: Create a provider component
interface MyProviderProps {
  children: ReactNode;
}

const MyProvider: FC<MyProviderProps> = ({ children }) => {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  const decrement = () => {
    setCount(count - 1);
  };

  return (
    <MyContext.Provider value={{ count, increment, decrement }}>
      {children}
    </MyContext.Provider>
  );
};

export default MyProvider;

```