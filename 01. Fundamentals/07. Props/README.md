
<h3  align="center" >𝐏𝗋ⱺρ𝗌</h3>

``` JSX

// React components use props to communicate with each other. 
// Every parent component can pass some information to its child components by giving them props. 
// Props might remind you of HTML attributes, but you can pass any JavaScript value through them, including objects, arrays, and functions.

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

const User = (props) => {
  return (
    <section>
      <img src={props.img} alt={props.name} width={200} />
      <h1>Name: {props.name}</h1>
      <h2>Age: {props.age}</h2>
      <h3>Is married: {props.isMarried}</h3>
      <h4>Hobbies: {props.hobbies} </h4>
    </section>
  );
};

export default App;

```

</br>

<h3  align="center" >𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌</h3>

### Exercise: Using Props in React Components

In this exercise, you will learn how to pass and use props in React components to make them dynamic and reusable.

#### Step 1: Create a `Person` Component

1. Create a new file called `Person.jsx`.
2. Inside this file, create a functional component called `Person`.
3. This component should accept `props` and render:

   - A `<h2>` element that displays the person's name.
   - A `<p>` element that displays the person's age.

4. Use `props.name` and `props.age` to display the dynamic values passed from the parent component.

#### Step 2: Create a `Product` Component

1. Create a new file called `Product.jsx`.
2. Inside this file, create a functional component called `Product`.
3. This component should accept `props` and render:

   - A `<h2>` element that displays the product's name.
   - A `<p>` element that displays the product's price.

4. Use `props.name` and `props.price` to display the values passed from the parent component.

#### Step 3: Pass Props from `App.jsx`

1. In your `App.jsx` file, import the `Person` and `Product` components:

   ```jsx
   import Person from "./Person";
   import Product from "./Product";
   ```

2. Inside the `App` component, pass dynamic data as props to both `Person` and `Product` components:
   - Pass `name` and `age` as props to the `Person` component.
   - Pass `name` and `price` as props to the `Product` component.

</br>

<h3  align="center" >𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣</h3>

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

const Person = (props) => {
  return (
    <div>
      <h1>Name: {props.name}</h1>
      <h1>Age: {props.age}</h1>
    </div>
  );
};

export default Person;

```

```JSX

const Product = (props) => {
  return (
    <div>
      <h1>Product Name: {props.name}</h1>
      <h1>Product Price: {props.price}</h1>
    </div>
  );
};

export default Product;

```