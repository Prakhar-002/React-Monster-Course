<h1  align="center" > 🍄 𝐉𝐒𝐗 𝐑𝐔𝐋𝐄𝐒 🥠</h1>

```JSX

// ********** JSX RULES **********

// 1. Return a single root element
// To return multiple elements from a component, wrap them with a single parent tag.

// ERROR
// const App = () => {
//     return (
//         <section id="section">
//         </section>
//           <h1>Welcome To React</h1>
//       );
// }

// 2. Close all the tags
// JSX requires tags to be explicitly closed: self-closing tags like <img> must become <img />, and wrapping tags like <li>oranges must be written as <li>oranges</li>.

// Error
// const App = () => {
//     return (
//         <section id="section">
//           <img >
//         </section>
//       );
// }

// 3. className
// open your DevTools and read the error message
// const App = () => {
//   return (
//     <section class="section">
//       <h1 class="title">Hello HuXn</h1>
//     </section>
//   );
// };

// 4. forHTML
// open your DevTools and read the error message
const App = () => {
  return (
    <section class="section">
      <form>
        <label for="name">Name</label>
        <input type="text" placeholder="Enter Your Name" id="name" />
      </form>
    </section>
  );
};

export default App;

```

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### JSX Rules Exercise

In this exercise, you will learn and apply the core rules of writing JSX in React.

#### Step 1: Create a New Component

1. Create a new file called `JSXRules.jsx`.
2. Inside this file, write a functional component called `JSXRules`.

The component should return a `<div>` containing the following:

- A `<h1>` element with the text `"JSX Rules"`.

- A paragraph (`<p>`) that lists at least 3 rules of JSX:
  - JSX must return a **single parent element**.
  - JSX elements must be **properly closed**.
  - JSX attributes are written using **camelCase** (e.g., `className` instead of `class`).

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```JSX

const JSXRules = () => {
  return (
    <div>
      <h1>JSX Rules</h1>
      <p>JSX must return a single parent element.</p>
      <p>JSX elements must be properly closed.</p>
      <p>
        JSX attributes are written using camelCase (e.g., className instead of
        class).
      </p>
    </div>
  );
};

export default JSXRules;

```