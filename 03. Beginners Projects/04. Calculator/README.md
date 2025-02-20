
<h1  align="center" > 🍄 𝐂αᥣ𝖼υᥣα𝗍ⱺ𝗋 🥠</h1>

<h1  align="center" > 

<img  src="https://github.com/user-attachments/assets/1661fc67-7778-483d-9b3f-8d12486bc5ff" width="366px" height="500px"/>

</h1>

```JSX

//============ App.jsx ============== 

import Main from "./Main";

const App = () => {
  return (
    <div className="container">
      <Main />
    </div>
  );
};

export default App;

```

```JSX

//============ Calculator.jsx ============== 

import { useState } from "react";
import "./index.css";

function Calculator() {
  const [inputValue, setInputValue] = useState("");

  function display(value) {
    setInputValue(inputValue + value);
  }

  function calculate() {
    var answers = eval(inputValue);
    setInputValue(answers);
  }

  function clear() {
    setInputValue("");
  }

  return (
    <form class="calculator" name="calc">
      <input type="text" class="value" value={inputValue} />
      <span class="num clear" onClick={() => clear()}>
        c
      </span>
      <span onClick={() => display("/")}>/</span>
      <span onClick={() => display("*")}>*</span>
      <span onClick={() => display("7")}>7</span>
      <span onClick={() => display("8")}>8</span>
      <span onClick={() => display("9")}>9</span>
      <span onClick={() => display("-")}>-</span>
      <span onClick={() => display("4")}>4</span>
      <span onClick={() => display("5")}>5</span>
      <span onClick={() => display("6")}>6</span>
      <span className="plus" onClick={() => display("+")}>
        +
      </span>
      <span onClick={() => display("1")}>1</span>
      <span onClick={() => display("2")}>2</span>
      <span onClick={() => display("3")}>3</span>
      <span onClick={() => display("0")}>0</span>
      <span onClick={() => display("00")}>00</span>
      <span onClick={() => display(".")}>.</span>
      <span class="num equal" onClick={() => calculate()}>
        =
      </span>
    </form>
  );
}

export default Calculator;

```

<h1  align="center" >🌽 𝓬𝓼𝓼 🪻</h1>

```css

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background: #1b1b1b;
}

.calculator {
  position: relative;
  display: grid;
}

.calculator .value {
  grid-column: span 4;
  height: 100px;
  text-align: right;
  border: none;
  outline: none;
  padding: 10px;
  font-size: 18px;
}

.calculator span {
  display: grid;
  width: 60px;
  height: 60px;
  background: #292929;
  place-items: center;
  border: 1px solid rgba(0, 0, 0, 0.1);
  color: #fff;
}

.calculator span:active {
  background: rgb(255, 163, 26);
  color: #fff;
}

.calculator span.clear {
  grid-column: span 2;
  width: 120px;
  background: rgb(255, 163, 26);
  /* color: #fff; */
}

.calculator span.plus {
  grid-row: span 2;
  height: 120px;
}

.calculator span.equal {
  background: rgb(255, 163, 26);
  /* background: #03b1ff; */
}

```
