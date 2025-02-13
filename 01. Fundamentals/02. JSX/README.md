
<h3  align="center" >𝐉𝐒𝐗</h3>

```JSX

const App = () => {
  return (
    <section id="section">
      <h1>My Website</h1>
      <article>
        <h2>Welcome To React</h2>
        <p className="text">Paragraph Content</p>
      </article>
    </section>
  );
};

export default App;

// ------------------------------------
// Go to babel 👇 and past your code and checkout the result.
// https://babeljs.io/repl

// import React from "react";

// const App = () => {
//   return React.createElement(
//     "section",
//     {
//       id: "section",
//     },
//     React.createElement("h1", null, "My Website"),
//     React.createElement(
//       "article",
//       null,
//       React.createElement("h2", null, "Welcome To React"),
//       React.createElement(
//         "p",
//         {
//           class: "text",
//         },
//         "Paragraph Content"
//       )
//     )
//   );
// };

// export default App;

```

</br>

<h3  align="center" >𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌</h3>

In this exercise, you will practice writing basic JSX code and rendering it in a React app.

#### Step 1: Create a New Component

1. Create a new file called `WelcomeMessage.jsx`.
2. Inside this file, write a functional component called `WelcomeMessage`.
3. The component should return a `<div>` that contains:
   - A `<h1>` element that displays the message: `"Hello, World!"`
   - A `<p>` element that displays the message: `"Welcome to learning JSX!"`

#### Step 2: Render the Component in App.jsx

1. Open the `App.jsx` file.
2. Import the `WelcomeMessage` component at the top of the file:
3. Inside the `App` component's return statement, render the

#### Step 3: Run the Application

1. Run the app in your development environment.
2. You should see the `"Hello, World!"` message along with `"Welcome to learning JSX!"` displayed in your browser.

</br>

<h3  align="center" >𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣</h3>

```JSX

const WelcomeMessage = () => {
  return (
    <div>
      <h1>Hello, World!</h1>
      <p>Welcome to learning JSX!</p>
    </div>
  );
};

export default WelcomeMessage;

```