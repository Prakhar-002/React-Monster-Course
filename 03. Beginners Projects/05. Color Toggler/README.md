
<h1  align="center" > 🍄 𝐂ⱺᥣⱺ𝗋 𝐓ⱺ𝗀𝗀ᥣ𝖾𝗋 🥠</h1>

<h1  align="center" > 

<img  src="https://github.com/user-attachments/assets/151af254-77e2-4829-8782-d60140a59796" width="500px" height="486px"/>

</h1>

```JSX

//============ App.jsx ============== 

import ToggleBackgroundColor from "./ToggleBackgroundColor";

const App = () => {
  return <ToggleBackgroundColor />;
};

export default App;

```

```JSX

//============ ToggleBackgroundColor.jsx ============== 

import React, { useState } from "react";
import "./index.css";

function ToggleBackgroundColor() {
  const [backgroundColor, setBackgroundColor] = useState("white");
  const [textColor, setTextColor] = useState("#1b1b1b");
  const [buttonStyle, setButtonStyle] = useState("white");

  function handleClick() {
    setBackgroundColor(backgroundColor === "white" ? "#1b1b1b" : "white");
    setTextColor(textColor === "#1b1b1b" ? "#ffa31a" : "#1b1b1b");
    setButtonStyle(backgroundColor === "white" ? "#1b1b1b" : "white");
  }

  return (
    <section style={{ backgroundColor, color: textColor }}>
      <button
        onClick={handleClick}
        style={{
          buttonStyle,
          color: textColor,
          border: `2px solid ${textColor}`,
        }}
      >
        {backgroundColor == "#1b1b1b" ? "Black Theme" : "White Theme"}
      </button>
      <section className="content">
        <h1>
          Welcome To A <br /> Real World..
        </h1>
      </section>
    </section>
  );
}

export default ToggleBackgroundColor;

```

<h1  align="center" >🌽 𝓬𝓼𝓼 🪻</h1>

```css

@import url("https://fonts.googleapis.com/css2?family=Bungee+Outline&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}

body section {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

button {
  position: absolute;
  top: 20px;
  right: 20px;
  padding: 10px 20px;
  background: transparent;
  cursor: pointer;
}

section.content h1 {
  font-size: 5rem;
  font-family: "Bungee Outline", cursive;
  line-height: 80px;
}

```
