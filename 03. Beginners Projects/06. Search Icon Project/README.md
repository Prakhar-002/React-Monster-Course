
<h1  align="center" > 🍄 𝐒𝖾α𝗋𝖼ɦ 𝚰𝖼ⱺ𐓣 𝐏𝗋ⱺ𝗃𝖾𝖼𝗍 🥠</h1>

<h1  align="center" > 

<img  src="https://github.com/user-attachments/assets/57207291-332e-4daf-b2dc-09885ce3d782" width="500px" height="342px"/>

</h1>

```JSX

//============ App.jsx ============== 

import HiddenSearchBar from "./HiddenSearchBar";

const App = () => {
  return <HiddenSearchBar />;
};

export default App;

```

```JSX

//============ HiddenSearchBar.jsx ============== 

import React, { useState } from "react";
import { FaSearch } from "react-icons/fa";
import "./index.css";

function HiddenSearchBar() {
  const [showInput, setShowInput] = useState(false);
  const [bgColor, setBgColor] = useState("white");

  const handleClick = (e) => {
    setBgColor("#1a1a1a");
    if (e.target.className === "container") {
      setShowInput(false);
      setBgColor("#fff");
    }
  };

  return (
    <section
      className="container"
      style={{ backgroundColor: bgColor }}
      onClick={handleClick}
    >
      {showInput ? (
        <input type="text" placeholder="Search..." />
      ) : (
        <FaSearch onClick={() => setShowInput(true)} />
      )}
    </section>
  );
}

export default HiddenSearchBar;

```

<h1  align="center" >🌽 𝓬𝓼𝓼 🪻</h1>

```css

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

section {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  transition: 0.7s ease;
}

button {
  position: absolute;
  top: 20px;
  right: 20px;
  padding: 10px 20px;
  background: transparent;
  cursor: pointer;
}

input {
  padding: 13px 12px;
  background: transparent;
  outline: none;
  border: 1px solid #fff;
  color: #fff;
  border-radius: 2px;
  box-shadow: 2px 2px 2px 1px rgb(35, 35, 35);
}

```
