
<h1  align="center" > 🍄 𝐌υᥣ𝗍𝗂ρᥣ𝖾 𝐂ⱺꭑρⱺ𐓣𝖾𐓣𝗍𝗌 🥠</h1>


``` JSX

//============ APP.jsx ============== 

import Greetings from "./components/Greetings";
import Add from "./components/Add";

const App = () => {
  return (
    <>
      <Greetings />
      <Add />
    </>
  );
};

export default App;

```

```JSX

//============ Add.jsx ============== 

const Add = () => {
  return <div>Add</div>;
};

export default Add;

```

```JSX

//============ Greetings.jsx ============== 

const Greetings = () => {
  return <div>Greetings</div>;
};

export default Greetings;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

<h2  align="center" >Exercise: Rendering Multiple Components and Nesting Components</h2>

In this exercise, you will learn how to create multiple components and render one component inside another.

#### Step 1: Create a `Header` Component

1. Create a new file called `Header.jsx`.
2. Inside this file, create a functional component named `Header`.
3. The `Header` component should return a `<header>` element with the following:
   - A `<h1>` element with the text `"Welcome to My Website!"`
   - A `<nav>` element containing three links (`<a>`) with the text `"Home"`, `"About"`, and `"Contact"`.

#### Step 2: Create a `Footer` Component

1. Create a new file called `Footer.jsx`.
2. Inside this file, create a functional component named `Footer`.
3. The `Footer` component should return a `<footer>` element with a `<p>` containing the text `"© 2024 My Website"`.

#### Step 3: Create a `MainContent` Component

1. Create a new file called `MainContent.jsx`.
2. Inside this file, create a functional component named `MainContent`.
3. The `MainContent` component should return a `<main>` element containing:
   - A `<h2>` element with the text `"Main Content"`.
   - A `<p>` element with any text of your choice.

#### Step 4: Render Components Inside `App.jsx`

1. In your `App.jsx` file, import the `Header`, `MainContent`, and `Footer` components:

   ```jsx
   import Header from "./Header";
   import MainContent from "./MainContent";
   import Footer from "./Footer";
   ```

2. Inside the `App` component's return statement, render the three components inside a single `<div>`, in the following order:
   - `Header`
   - `MainContent`
   - `Footer`

Your `App.jsx` should look like this:

```jsx
function App() {
  return (
    <div>
      <Header />
      <MainContent />
      <Footer />
    </div>
  );
}

export default App;
```

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```JSX

//============ APP.jsx ============== 

import Header from "./components/Header";
import Footer from "./components/Footer";
import MainContent from "./components/MainContent";

function App() {
  return (
    <>
      <Header />
      <MainContent />
      <Footer />
    </>
  );
}

export default App;

```

```JSX

//============ Header.jsx ============== 

const Header = () => {
  return (
    <header>
      <h1>Welcome to My Website!</h1>
      <nav>
        <a href="">Home</a>
        <a href="">About</a>
        <a href="">Contact</a>
      </nav>
    </header>
  );
};

export default Header;

```

```JSX

//============ MainContent.jsx ============== 

const MainContent = () => {
  return (
    <main>
      <h2>Main Content</h2>
      <p>This is the main content.</p>
    </main>
  );
};

export default MainContent;

```

```JSX

//============ Footer.jsx ============== 

const Footer = () => {
  return (
    <footer>
      <p>© 2024 My Website</p>
    </footer>
  );
};

export default Footer;

```
