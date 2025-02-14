
<h1  align="center" > 🍄 υ𝗌𝖾𝐒𝗍α𝗍𝖾 🥠</h1>

```JSX

//============ App.jsx ============== 

import { useState } from "react";

const App = () => {
  // --------------------------------------------
  // const [initialValue, setInitialValue] = useState(0);
  // const [initialValue, setInitialValue] = useState("HuXn");
  // const [initialValue, setInitialValue] = useState(["one", "two", "three"]);
  // const [initialValue, setInitialValue] = useState({
  //   one: "Alex",
  //   two: "John",
  //   three: "HuXn",
  // });
  // --------------------------------------------

  const [counter, setCounter] = useState(0);

  const increment = () => setCounter(counter + 1);
  const decrement = () => setCounter(counter - 1);

  return (
    <section>
      <h1>{counter}</h1>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
    </section>
  );
};

export default App;

```

</br>

```CSS

/* ============ Style.css ==============  */

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