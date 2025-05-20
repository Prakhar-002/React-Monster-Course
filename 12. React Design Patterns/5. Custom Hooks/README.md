
<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

## **React Custom Hook Challenge: Build a Project Using Custom Hooks**

### **Step 1: Create a Custom Hook for Local Storage (useLocalStorage)**

#### **Objective**:

- Write a custom hook that manages the localStorage.
- This hook will allow you to store and retrieve values from the browser's localStorage.

---

### **Step 2: Create a Custom Hook for Fetching Data (useFetch)**

#### **Objective**:

- Create a custom hook to fetch data from an API.

---

### **Step 3: Create a Custom Hook for Form Handling (useForm)**

#### **Objective**:

- Create a custom hook to handle form inputs and submission.

---

### **Step 4: Create a Custom Hook for Debouncing (useDebounce)**

#### **Objective**:

- Create a custom hook to debounce a value (useful for input fields that call API on change).

---

### **Step 5: Create a Custom Hook to Track Previous Value (usePrevious)**

#### **Objective**:

- Create a custom hook to track the previous value of a variable.

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

</br>

```JSX
//============ ⚛️App.tsx ==============

import { useState } from "react";
import useLocalStorage from "./hooks/useLocalStorage";
import useFetch from "./hooks/useFetch";
import useForm from "./hooks/useForm";
import useDebounce from "./hooks/useDebounce";
import usePrevious from "./hooks/usePrevious";

const App = () => {
  const [storedValue, setStoredValue] = useLocalStorage("username", "");

  const { data, loading, error } = useFetch<any>(
    "https://jsonplaceholder.typicode.com/posts"
  );

  const { values, handleChange, handleSubmit } = useForm({
    username: "",
    email: "",
  });

  const [inputValue, setInputValue] = useState("");
  const debouncedInput = useDebounce(inputValue, 500);

  const previousValue = usePrevious(inputValue);

  const handleInputChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    setInputValue(e.target.value);
  };

  return (
    <div className="App p-4">
      <h1 className="text-3xl mb-4">Custom Hooks in Action</h1>

      <div className="mb-4">
        <h2 className="text-xl">Form Handling Example</h2>
        <form onSubmit={handleSubmit}>
          <input
            className="border p-2 mb-2"
            type="text"
            name="username"
            value={values.username}
            onChange={handleChange}
            placeholder="Username"
          />
          <input
            className="border p-2 mb-2"
            type="email"
            name="email"
            value={values.email}
            onChange={handleChange}
            placeholder="Email"
          />
          <button type="submit" className="border p-2">
            Submit
          </button>
        </form>
      </div>

      <div className="mb-4">
        <h2 className="text-xl">Debounced Input Example</h2>
        <input
          className="border p-2"
          type="text"
          value={inputValue}
          onChange={handleInputChange}
          placeholder="Type to debounce"
        />
        <p>Debounced Value: {debouncedInput}</p>
        <p>Previous Value: {previousValue}</p>
      </div>

      <div className="mb-4">
        <h2 className="text-xl">Local Storage Example</h2>
        <input
          className="border p-2"
          type="text"
          value={storedValue}
          onChange={(e) => setStoredValue(e.target.value)}
          placeholder="Set Local Storage"
        />
      </div>

      <div className="mb-4">
        <h2 className="text-xl">Fetch Data Example</h2>
        {loading && <p>Loading...</p>}
        {error && <p>Error: {error}</p>}
        {data && <pre>{JSON.stringify(data, null, 2)}</pre>}
      </div>
    </div>
  );
};

export default App;

```

</br>

```JSX
//============ 🗂️hooks/⚛️useLocalStorage.ts ==============

import { useState } from "react";

const useLocalStorage = <T>(key: string, initialValue: T) => {
  const [storedValue, setStoredValue] = useState<T>(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error(error);
      return initialValue;
    }
  });

  const setValue = (value: T) => {
    try {
      setStoredValue(value);
      window.localStorage.setItem(key, JSON.stringify(value));
    } catch (error) {
      console.error(error);
    }
  };

  return [storedValue, setValue] as const;
};

export default useLocalStorage;

```

</br>

```JSX
//============ 🗂️hooks/⚛️useFetch.ts ==============

import { useState, useEffect } from "react";

const useFetch = <T>(url: string) => {
  const [data, setData] = useState<T | null>(null);
  const [loading, setLoading] = useState<boolean>(true);
  const [error, setError] = useState<string | null>(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch(url);
        if (!response.ok) {
          throw new Error("Network response was not ok");
        }
        const result: T = await response.json();
        setData(result);
      } catch (error: any) {
        setError(error.message);
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

</br>

```JSX
//============ 🗂️hoots/⚛️useForm.ts ==============

import { useState } from "react";

const useForm = <T>(initialValues: T) => {
  const [values, setValues] = useState<T>(initialValues);

  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    setValues({
      ...values,
      [e.target.name]: e.target.value,
    });
  };

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    console.log(values);
  };

  return { values, handleChange, handleSubmit };
};

export default useForm;

```

</br>

```JSX
//============ 🗂️hoots/⚛️useDebounce.ts ==============

import { useState, useEffect } from "react";

const useDebounce = <T>(value: T, delay: number) => {
  const [debouncedValue, setDebouncedValue] = useState<T>(value);

  useEffect(() => {
    const handler = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    return () => {
      clearTimeout(handler);
    };
  }, [value, delay]);

  return debouncedValue;
};

export default useDebounce;

```

</br>

```JSX
//============ 🗂️hoots/⚛️usePrevious.ts ==============

import { useRef, useEffect } from "react";

const usePrevious = <T>(value: T) => {
  const ref = useRef<T>();

  useEffect(() => {
    ref.current = value;
  }, [value]);

  return ref.current;
};

export default usePrevious;

```

