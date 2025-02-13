
<h3  align="center" >𝐄𝗏𝖾𐓣𝗍𝗌</h3>

``` JSX

// Example 1
const Button = () => {
  // const handleClick = () => console.log("You Clicked Me");
  const handleClick = () => console.log(Math.round(Math.random() * 10));
  return <button onClick={handleClick}>Click</button>;
};

// Example 2
const Copy = () => {
  function copyHandler() {
    console.log("Stop Stealing My Content.");
  }

  return (
    <p onCopy={copyHandler}>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium
      voluptatibus libero, eius odit modi doloremque quos magni tempora. Debitis
      laborum exercitationem perferendis. Veritatis fuga, quod quasi accusamus
      eveniet voluptates suscipit.
    </p>
  );
};

// Example 3
const Move = () => {
  function moveHandler() {
    alert("Mouse Move Event Fired");
    console.log("Mouse Move Event Fired");
  }

  return (
    <p onMouseOver={moveHandler}>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium
      voluptatibus libero, eius odit modi doloremque quos magni tempora. Debitis
      laborum exercitationem perferendis. Veritatis fuga, quod quasi accusamus
      eveniet voluptates suscipit.
    </p>
  );
};

const App = () => {
  // return <Button />;
  // return <Copy />;
  return <Move />;
};

export default App;

```

</br>

<h3  align="center" >𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌</h3>

# ⚠️ DO THIS EXERCISE WHEN YOU LEARN "useState" hook ⚠️

### Challenge: Handling Events in React

#### Step 1: Create an `EventDemo` Component

1. Create a new file called `EventDemo.jsx`.
2. Inside this file, create a functional component called `EventDemo`.
3. The component should render the following elements:

   - A `<button>` that, when clicked, updates the text of a `<p>` element to "Button Clicked!".
   - A `<div>` containing a `<p>` element. When text inside the `<p>` element is copied, the text should change to "Text Copied!".
   - A `<div>` containing a `<p>` element. When the mouse hovers over the `<p>` element, the background color should change to light yellow.

#### Step 2: Render the `EventDemo` Component in `App.jsx`

1. In your `App.jsx` file, import the `EventDemo` component:

   ```jsx
   import EventDemo from "./EventDemo";
   ```

2. Inside the `App` component, render the `EventDemo` component:

   ```jsx
   function App() {
     return (
       <div>
         <h1>React Event Handling Challenge</h1>
         <EventDemo />
       </div>
     );
   }

   export default App;
   ```
