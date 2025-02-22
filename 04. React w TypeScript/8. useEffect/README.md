
<h1  align="center" > 🍄 υ𝗌𝖾𝐄𝖿𝖿𝖾𝖼𝗍 🥠</h1>

```TSX

//============ App.tsx ============== 

"use client";

import MyComponent from "@/components/MyComponent";

export default function Home() {
  return (
    <>
      <MyComponent />
    </>
  );
}

```

```TSX

//============ components/MyComponent.tsx ============== 

import { useState, useEffect } from "react";

type Product = {
  id: number;
  title: string;
  description: string;
  price: number;
  discountPercentage: number;
  rating: number;
  stock: number;
  brand: string;
  category: string;
  thumbnail: string;
  images: string[];
};

const MyComponent = () => {
  // State with type annotation
  const [data, setData] = useState<Product | null>(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch("https://dummyjson.com/product/1");
        const result = await response.json();
        setData(result);
      } catch (error) {
        console.error("Error fetching data:", error);
      }
    };

    fetchData();
  }, []);

  return (
    <div>
      {data ? (
        <div>
          <p>ID: {data.id}</p>
          <p>Title: {data.title}</p>
          <p>description: {data.description}</p>
          <p>price: {data.price}</p>
          <p>discountPercentage: {data.discountPercentage}</p>
          <p>rating: {data.rating}</p>
          <p>stock: {data.stock}</p>
          <p>brand: {data.brand}</p>
          <p>category: {data.category}</p>
          <p>thumbnail: {data.thumbnail}</p>
          {data.images.map((img) => (
            <img src={img} />
          ))}
        </div>
      ) : (
        <p>Loading...</p>
      )}
    </div>
  );
};

export default MyComponent;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

# useEffect Types

## Objective

Create a React component that fetches user data from an API using `useEffect`, stores the data in a state variable using `useState`, and displays the data. You'll define TypeScript types to ensure type safety throughout the component.

## Requirements

1. **Create a new React component named `UserList`.**

2. **Fetch data from the following API endpoint:**

   ```
   https://jsonplaceholder.typicode.com/users
   ```

   This endpoint returns a list of users, with each user object containing `id`, `name`, `username`, `email`, and `phone`.

3. **Define TypeScript types** for the user data. The data structure should include:

   - `id`: number
   - `name`: string
   - `username`: string
   - `email`: string
   - `phone`: string

4. **Use the `useEffect` hook** to fetch data from the API when the component mounts.

5. **Use the `useState` hook** to store the fetched data. Ensure you type the state to match the user data.

6. **Render the list of users** in a simple HTML table. Each row should display the user's `name`, `username`, `email`, and `phone`.

7. **Verify your component:**
   - Ensure that it correctly fetches the data and handles loading and error states.
   - Confirm that the user data is displayed in a table format.

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```TSX

//============ App.tsx ============== 

import UserList from "./components/UserList";

const App = () => {
  return (
    <div>
      <UserList />
    </div>
  );
};

export default App;

```

```TSX

//============ components/UserList.tsx ============== 

import { useEffect, useState } from "react";

interface User {
  id: number;
  name: string;
  username: string;
  email: string;
  phone: string;
}

const UserList = () => {
  const [users, setUsers] = useState<User[]>([]);
  const [loading, setLoading] = useState<boolean>(true);
  const [error, setError] = useState<string | null>(null);

  useEffect(() => {
    const fetchUsers = async () => {
      try {
        const response = await fetch(
          "https://jsonplaceholder.typicode.com/users"
        );
        if (!response.ok) {
          throw new Error("Network response was not ok");
        }
        const data: User[] = await response.json();
        setUsers(data);
      } catch (error) {
        setError(error instanceof Error ? error.message : "An error occurred");
      } finally {
        setLoading(false);
      }
    };

    fetchUsers();
  }, []);

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;

  return (
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Username</th>
          <th>Email</th>
          <th>Phone</th>
        </tr>
      </thead>
      <tbody>
        {users.map((user) => (
          <tr key={user.id}>
            <td>{user.name}</td>
            <td>{user.username}</td>
            <td>{user.email}</td>
            <td>{user.phone}</td>
          </tr>
        ))}
      </tbody>
    </table>
  );
};

export default UserList;

```