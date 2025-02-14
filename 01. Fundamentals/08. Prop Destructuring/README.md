
<h1  align="center" > 🍄 𝐏𝗋ⱺρ 𝐃𝖾𝗌𝗍𝗋υ𝖼𝗍υ𝗋𝗂𐓣𝗀 🥠</h1>


``` JSX

const App = () => {
  return (
    <User
      img="https://avatars.githubusercontent.com/u/85052811?v=4"
      name="HuXn WebDev"
      age={18}
      isMarried={false}
      hobbies={["Coding", "Reading", "Sleeping"]}
    />
  );
};

const User = ({ img, name, age, isMarried, hobbies }) => {
  return (
    <section>
      <img src={img} alt={name} width={200} />
      <h1>Name: {name}</h1>
      <h2>Age: {age}</h2>
      <h3>Is married: {isMarried}</h3>
      <h4>Hobbies: {hobbies} </h4>
    </section>
  );
};

export default App;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise: Props Destructuring in React Components

In this exercise, you will learn how to use **destructuring** to simplify how you access props in React components.

#### Step 1: Create a `Person` Component with Props Destructuring

1. Create a new file called `Person.jsx`.
2. Inside this file, create a functional component called `Person`.
3. Destructure the `name` and `age` props directly in the function parameters and render:
   - A `<h2>` element that displays the person's name.
   - A `<p>` element that displays the person's age.

#### Step 2: Create a `Product` Component with Props Destructuring

1. Create a new file called `Product.jsx`.
2. Inside this file, create a functional component called `Product`.
3. Destructure the `name` and `price` props in the function parameters and render:
   - A `<h2>` element that displays the product's name.
   - A `<p>` element that displays the product's price.

#### Step 3: Pass Props from `App.jsx`

1. In your `App.jsx` file, import the `Person` and `Product` components:

   ```jsx
   import Person from "./Person";
   import Product from "./Product";
   ```

2. Inside the `App` component, pass the `name` and `age` props to the `Person` component, and `name` and `price` props to the `Product` component.

Example:

```jsx
function App() {
  return (
    <div>
      {/* Passing props to Person */}
      <Person name="John Doe" age={28} />
      <Person name="Jane Smith" age={32} />

      {/* Passing props to Product */}
      <Product name="Laptop" price="$1200" />
      <Product name="Smartphone" price="$699" />
    </div>
  );
}

export default App;
```

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```JSX

//============ App.jsx ============== 

import Person from "./components/Person";
import Product from "./components/Product";

function App() {
  return (
    <>
      <Person name="HuXn" age={22} />
      <Product name="Iphone" price={30000} />
    </>
  );
}

export default App;

```

```JSX

const Person = ({ name, age }) => {
  return (
    <div>
      <h1>Name: {name}</h1>
      <h1>Age: {age}</h1>
    </div>
  );
};

export default Person;

```

```JSX

const Product = ({ name, price }) => {
  return (
    <div>
      <h1>Product Name: {name}</h1>
      <h1>Product Price: {price}</h1>
    </div>
  );
};

export default Product;

```
