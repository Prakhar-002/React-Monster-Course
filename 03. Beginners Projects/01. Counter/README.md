<h1  align="center" > 🍄 𝐂ⱺυ𐓣𝗍𝖾𝗋 🥠</h1>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/0581af91-f38f-40bc-b7d6-2ff04f1d1d50" width="500px" height="362px"/>

</h1>

```JSX

//============ App.jsx ============== 

import Counter from "./Counter";

const App = () => {
  return <Counter />;
};

export default App;

```

```JSX

//============ Components/Counter.jsx ============== 

import React, { useState } from "react";
import "./style.css";

function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => setCount(count + 1);
  const decrement = () => setCount(count - 1);

  return (
    <>
      <div className="container">
        <h1 className="number">{count}</h1>
      </div>

      <section className="btns-container">
        <button onClick={increment} className="increment">
          +
        </button>
        <button onClick={decrement} className="increment">
          -
        </button>
      </section>
    </>
  );
}

export default Counter;

```

<h1  align="center" >🌽 𝓬𝓼𝓼 🪻</h1>

```css

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  background: #000;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: #fff;
}

.container .number {
  font-size: 6rem;
}

.btns-container {
  width: 40rem;
  display: flex;
  justify-content: space-around;
  margin-top: 5rem;
}

.increment {
  padding: 10px 20px;
  border-radius: 100px;
  font-size: 2rem;
  background: #141517;
  color: #fff;
  cursor: pointer;
}

```
