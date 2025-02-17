
<h1  align="center" > 🍄 𝐏𝗋ⱺρ 𝐃𝗋𝗂ᥣᥣ𝗂𐓣𝗀 🥠</h1>

```JSX

//============ App.jsx ============== 

import ComponentA from "./ComponentA";

const App = () => {
  const name = "Prakhar";
  return <ComponentA name={name} />;
};

export default App;

```

```JSX

//============ ComponentA.jsx ============== 

import ComponentB from "./ComponentB";

const ComponentA = ({ name }) => {
  return <ComponentB name={name} />;
};

export default ComponentA;

```

```JSX

//============ ComponentB.jsx ============== 

import ComponentC from "./ComponentC";

const ComponentB = ({ name }) => {
  return <ComponentC name={name} />;
};

export default ComponentB;

```

```JSX

//============ ComponentC.jsx ============== 

const ComponentC = ({ name }) => {
  return <h1>{name}</h1>;
};

export default ComponentC;

```