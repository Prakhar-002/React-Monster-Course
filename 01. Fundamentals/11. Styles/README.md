
<h1  align="center" > 🍄 𝐒𝗍𝗒ᥣ𝖾𝗌 🥠</h1>

<h2  align="center" >𝚰𐓣ᥣ𝗂𐓣𝖾 𝐒𝗍𝗒ᥣ𝖾𝗌</h2>

```JSX

// Adding Style

// 1. use double curly braces {{property: value}}
// you'd also need to use camelCase convention for styling.

// const App = () => {
//   return (
//     <section>
//       <h1 style={{ color: "white", backgroundColor: "teal", padding: "2rem" }}>
//         Inline Style
//       </h1>
//     </section>
//   );
// };

// 2. Separate Styles and then interpolate it.
const App = () => {
  const styles = { color: "white", backgroundColor: "teal", padding: "2rem" };

  return (
    <section>
      <h1 style={styles}>Inline Style</h1>
    </section>
  );
};

export default App;

```

<h2  align="center" >𝐒𝖾ρα𝗋α𝗍𝖾 𝐒𝗍𝗒ᥣ𝖾𝗌</h2>

```JSX

import "./index.css";

const App = () => {
  return (
    <section>
      <h1>Separate File For Styling</h1>
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
  background: rgb(107, 181, 32);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

h1 {
  font-family: sans-serif;
  border: 2px solid #ccc;
  padding: 20px;
}

```

<h2  align="center" >𝚰𝖼ⱺ𐓣𝗌</h2>

```JSX

// 👉 https://react-icons.github.io/react-icons
// 👉 npm install react-icons --save
// 👉 import { AiOutlineHourglass } from "react-icons/ai";
// 👉  <AiOutlineHourglass />

import { AiOutlineHourglass } from "react-icons/ai";

const App = () => {
  return (
    <h1>
      <AiOutlineHourglass />
    </h1>
  );
};

export default App;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise: Styling Components in React

In this exercise, you'll learn how to apply styles using different methods in React components, including inline styles, style objects, and React icons.

#### Step 1: Create a `StyledCard` Component with Inline Styles

1. Create a new file called `StyledCard.jsx`.
2. Inside this file, create a functional component called `StyledCard`.
3. Use inline styles to style the component:

   - Set the background color to light blue.
   - Set padding to `20px`.
   - Set border radius to `10px`.
   - Set text color to dark blue.

4. Render a `<div>` with a title and description inside it.

#### Step 2: Create a `ProfileCard` Component with Separate Style Object

1. Create a new file called `ProfileCard.jsx`.
2. Inside this file, create a functional component called `ProfileCard`.
3. Define a `styles` object to hold the CSS properties:

   - Set the background color to light gray.
   - Set padding to `15px`.
   - Set border radius to `8px`.
   - Set text color to black.

4. Apply the `styles` object to the `<div>` using the `style` attribute.

5. Render a `<div>` with a title and description inside it.

#### Step 3: Create a `IconComponent` Using React Icons

1. Install `react-icons` if you haven’t already:

   ```bash
   npm install react-icons
   ```

2. Create a new file called `IconComponent.jsx`.
3. Inside this file, create a functional component called `IconComponent`.
4. Import an icon from `react-icons`, such as `FaBeer` from `react-icons/fa`.

5. Style the icon using inline styles:

   - Set the font size to `30px`.
   - Set the color to gold.

6. Render the icon with a title.

#### Step 4: Render All Components in `App.jsx`

1. In your `App.jsx` file, import the `StyledCard`, `ProfileCard`, and `IconComponent` components:

   ```jsx
   import StyledCard from "./StyledCard";
   import ProfileCard from "./ProfileCard";
   import IconComponent from "./IconComponent";
   ```

2. Inside the `App` component, render all three components:

   ```jsx
   function App() {
     return (
       <div>
         <StyledCard />
         <ProfileCard />
         <IconComponent />
       </div>
     );
   }

   export default App;
   ```

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```JSX

//============ App.jsx ============== 

import IconComponent from "./components/IconComponent";
import ProfileCard from "./components/ProfileCard";
import StyledCard from "./components/StyledCard";

function App() {
  return (
    <>
      <StyledCard />
      <ProfileCard />
      <IconComponent />
    </>
  );
}

export default App;

```

```JSX

//============ StyledCard.jsx ============== 

const StyledCard = () => {
  // Set the background color to light blue.
  // Set padding to 20px.
  // Set border radius to 10px.
  // Set text color to dark blue.

  return (
    <div
      style={{
        backgroundColor: "lightblue",
        padding: "20px",
        borderRadius: "10px",
        color: "darkblue",
      }}
    >
      <h1 style={{ fontSize: "2rem", marginBottom: "2rem" }}>Styled Card</h1>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur
        consequatur deserunt accusantium laborum. Totam ab in eos. Eos
        laboriosam dolorum commodi quia sapiente inventore beatae fugit qui
        recusandae ipsa ea quae asperiores, corrupti libero! Ut rerum maiores
        soluta harum nihil magnam asperiores libero placeat, nostrum animi natus
        laudantium. Molestiae esse neque enim exercitationem hic inventore sint
        non debitis a quam.
      </p>
    </div>
  );
};

export default StyledCard;

```

```JSX

//============ ProfileCard.jsx ============== 

const ProfileCard = () => {
  // Set the background color to light gray.
  // Set padding to 15px.
  // Set border radius to 8px.
  // Set text color to black.

  const styles = {
    backgroundColor: "lightgray",
    padding: "15px",
    borderRadius: "8px",
    color: "black",
  };

  return (
    <div style={styles}>
      <h1>Hello World</h1>
      <p>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Laudantium
        voluptatem placeat incidunt animi debitis, officiis iure illo voluptatum
        itaque ratione!
      </p>
    </div>
  );
};

export default ProfileCard;

```

```JSX

//============ IconComponent.jsx ============== 

import { FaBeer } from "react-icons/fa";

const IconComponent = () => {
  return (
    <div>
      <FaBeer />
      <FaBeer size={30} />
      <FaBeer size={30} color="gold" />
    </div>
  );
};

export default IconComponent;

```