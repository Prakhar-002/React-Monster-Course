
<h3  align="center" >𝐋𝗂𝗌𝗍 ⱺ𝖿 𝐃α𝗍α</h3>

``` JSX

// Let's iterate over lists and render them to the DOM.

// Example 1
// const App = () => {
//   const numbers = [1, 2, 3, 4, 5];

//   return (
//     <main>
//       {numbers.map((number) => (
//         <ul key={Math.random()}>
//           <li>{number}</li>
//         </ul>
//       ))}
//     </main>
//   );
// };

// Example 2
// const App = () => {
//   const usersInfo = [
//     {
//       username: "HuXn",
//       email: "test@gmail.com",
//       location: "USA",
//     },
//     {
//       username: "John",
//       email: "jd@gmail.com",
//       location: "Arab",
//     },
//     {
//       username: "Alex",
//       email: "alexmersion@gmail.com",
//       location: "India",
//     },
//   ];

//   return (
//     <section>
//       {usersInfo.map((user) => (
//         <ul key={Math.random()}>
//           <li>{user.username}</li>
//           <li>{user.email}</li>
//           <li>{user.location}</li>
//         </ul>
//       ))}
//     </section>
//   );
// };

// Example 3
import "./Shopping.css";

const Shopping = ({ items }) => {
  return (
    <section>
      <ol>
        {items.map((item) => (
          <li key={Math.random() * 5}>{item}</li>
        ))}
      </ol>
    </section>
  );
};

const App = () => {
  return (
    <section>
      <Shopping
        items={["Wireless Earbuds", "Power Bank", "New SSD", "Hoddie"]}
      />
    </section>
  );
};

export default App;

```

```css

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  background: rgb(227, 255, 255);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

ol {
  list-style: none;
  font-family: sans-serif;
  width: 500px;
}

li {
  background: rgb(247, 255, 255);
  font-weight: bold;
  margin: 10px;
  padding: 2rem;
  box-shadow: 1px 1px 2px 1px #ccc;
  transition: 1s ease;
}

li:hover {
  transform: scale(1.1);
}

```

</br>

<h3  align="center" >𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌</h3>

### Exercise: Rendering a List of Data with `.map()`

In this exercise, you will learn how to render a list of items using the `.map()` method in JSX.

#### Step 1: Create a `UserList` Component

1. Create a new file called `UserList.jsx`.
2. Inside this file, create a functional component called `UserList`.
3. In the component, create a `users` array with the following objects, where each object represents a user with `id`, `name`, and `age`:

   ```javascript
   const users = [
     { id: 1, name: "Alice", age: 25 },
     { id: 2, name: "Bob", age: 30 },
     { id: 3, name: "Charlie", age: 22 },
   ];
   ```

4. Use the `.map()` method to render a list of users. Each user's `name` and `age` should be displayed inside a `<div>` element. Use the `id` as the unique `key` for each list item.

#### Step 2: Create a `ProductList` Component

1. Create a new file called `ProductList.jsx`.
2. Inside this file, create a functional component called `ProductList`.
3. Create a `products` array with the following objects, where each object represents a product with `id`, `name`, and `price`:

   ```javascript
   const products = [
     { id: 1, name: "Phone", price: "$699" },
     { id: 2, name: "Laptop", price: "$1200" },
     { id: 3, name: "Headphones", price: "$199" },
   ];
   ```

4. Use the `.map()` method to render the list of products. Each product’s `name` and `price` should be displayed inside a `<div>` element. Use the `id` as the `key` for each product.

#### Step 3: Render the Components in `App.jsx`

1. In your `App.jsx` file, import the `UserList` and `ProductList` components:

   ```jsx
   import UserList from "./UserList";
   import ProductList from "./ProductList";
   ```

2. Inside the `App` component's return statement, render both the `UserList` and `ProductList` components:

   ```jsx
   function App() {
     return (
       <div>
         <UserList />
         <ProductList />
       </div>
     );
   }

   export default App;
   ```


</br>

<h3  align="center" >𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣</h3>

```JSX

//============ App.jsx ============== 

import ProductList from "./components/ProductList";
import UserList from "./components/UserList";

function App() {
  return (
    <>
      {/* <UserList /> */}
      <ProductList />
    </>
  );
}

export default App;

```

```JSX

//============ ProductList.jsx ============== 

const ProductList = () => {
  const products = [
    { id: 1, name: "Phone", price: "$699" },
    { id: 2, name: "Laptop", price: "$1200" },
    { id: 3, name: "Headphones", price: "$199" },
  ];

  return (
    <div>
      {products.map((p) => (
        <div key={p.id}>
          <h1>Name: {p.name}</h1>
          <h1>Price: {p.price}</h1>
        </div>
      ))}
    </div>
  );
};

export default ProductList;

```

```JSX

//============ UserList.jsx ============== 

const UserList = () => {
  const users = [
    { id: 1, name: "Alice", age: 25 },
    { id: 2, name: "Bob", age: 30 },
    { id: 3, name: "Charlie", age: 22 },
  ];

  return (
    <div>
      {users.map((user) => (
        <div key={user.id}>
          <h1>Name: {user.name}</h1>
          <h1>Age: {user.age}</h1>
        </div>
      ))}
    </div>
  );
};

export default UserList;

```
