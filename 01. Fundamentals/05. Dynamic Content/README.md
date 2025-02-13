
<h1  align="center" >𝐄ꭑᑲ𝖾ᑯᑯ𝗂𐓣𝗀 𝐃𝗒𐓣αꭑ𝗂𝖼 𝐂ⱺ𐓣𝗍𝖾𐓣𝗍</h1>

``` JSX

// ********** Embedding Dynamic Content **********

const App = () => {
  const myName = "HuXn WebDev";
  const multiply = (a, b) => a + b;
  const specialClass = "simple-class";

  return (
    <section>
      {/* Rendering Expression */}
      <p>2 + 2 = {2 + 2}</p>
      {/* Rendering Variable Value */}
      <h1>{myName}</h1>
      {/* Rendering Array */}
      <p>My Friends List: {["Alex", "John", "Waheed", "Jordan"]}</p>
      {/* Rendering Function Value */}
      <p>2 * 2 = {multiply(2, 2)}</p>
      {/* Rendering Class */}
      <p className={specialClass}>This is special class</p>
    </section>
  );
};

export default App;

```

</br>

<h1  align="center" >𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌</h1>

### Exercise: Using Dynamic Content with `{}` in JSX

In this exercise, you'll learn how to inject dynamic data into JSX using curly braces `{}`.

#### Step 1: Create a `Greeting` Component

1. Create a new file called `Greeting.jsx`.
2. Inside this file, create a functional component named `Greeting`.
3. The `Greeting` component should return a `<div>` containing:

   - A `<h1>` element that dynamically displays a greeting message.
   - A `<p>` element that dynamically displays the current date.

4. Use JavaScript expressions inside `{}` to dynamically render the following:
   - A `name` variable containing a name, such as `"John"`.
   - A `new Date()` object to display the current date.

#### Step 2: Create a `ProductInfo` Component

1. Create a new file called `ProductInfo.jsx`.
2. Inside this file, create a functional component named `ProductInfo`.
3. The `ProductInfo` component should return a `<div>` that dynamically displays product details:

   - Use a `product` object that contains the following properties:
     - `name`: `"Laptop"`,
     - `price`: `$1200`,
     - `availability`: `"In stock"`

4. Display the product name, price, and availability using `{}`.

#### Step 3: Render Components in `App.jsx`

1. In your `App.jsx` file, import the `Greeting` and `ProductInfo` components:

   ```jsx
   import Greeting from "./Greeting";
   import ProductInfo from "./ProductInfo";
   ```

2. Inside the `App` component's return statement, render both components:

   ```jsx
   function App() {
     return (
       <div>
         <Greeting />
         <ProductInfo />
       </div>
     );
   }

   export default App;
   ```

</br>

<h1  align="center" >𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣</h1>

```JSX

//============ App.jsx ============== 

import Greeting from "./components/Greeting";
import ProductInfo from "./components/ProductInfo";

function App() {
  return (
    <>
      <Greeting />
      <ProductInfo />
    </>
  );
}

export default App;

```

```JSX

//============ Greeting.jsx ============== 

const Greeting = () => {
  const greet = "Hello";
  const date = new Date();

  return (
    <div>
      <h1>{greet}</h1>
      <p>Date: {date.getDate()}</p>
    </div>
  );
};

export default Greeting;

```

```JSX

//============ ProductInfo.jsx ============== 

const ProductInfo = () => {
  const product = {
    name: "Laptop",
    price: 1200,
    availability: "In stock",
  };

  return (
    <div>
      <h1>Name: {product.name}</h1>
      <h1>Price: $ {product.price}</h1>
      <h1>Availability: {product.availability}</h1>
    </div>
  );
};
export default ProductInfo;

```