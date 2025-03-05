
<h1  align="center" > 🍄 𝐔𝗌𝖾 𝐒ρ𝗋𝗂𐓣𝗀  🥠</h1>

### The useSpring hook allows us to create smooth, spring-based animations. It provides a way to manage animated values that follow a spring physics model, resulting in more natural and fluid motion compared to linear animations.

<h2  align="center" >💡 𝐄𝗑αꭑρᥣ𝖾  1️⃣ </h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/4b8ed050-64b4-4256-a799-cc39499612ab" width="400px" height="389px"/>

</h1>

```TSX

//============ App.tsx ============== 

import RangeSlider from "./components/RangeSlider";

const App = () => {
  return <RangeSlider />;
};

export default App;

```

```TSX

//============ components/RangeSlider.tsx ============== 

import { motion, useSpring } from "framer-motion";
import { ChangeEvent } from "react";

const RangeSlider = () => {
  const scale = useSpring(1);

  const changeHandler = (e: ChangeEvent<HTMLInputElement>) =>
    scale.set(parseFloat(e.target.value));

  return (
    <div>
      <motion.button className="box" style={{ scale }} />
      <div className="mt-[6rem]">
        <input
          type="range"
          min={0.5}
          max={5}
          step={0.01}
          defaultValue={1}
          onChange={changeHandler}
        />
      </div>
    </div>
  );
};

export default RangeSlider;

```

```css

/* ============== CSS ==============  */

@tailwind base;
@tailwind components;
@tailwind utilities;

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  background-color: #0d1017;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.box {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
  background-color: yellow;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #fff;
  font-size: 24px;
  text-align: center;
}

```

</br>

<h2  align="center" > 💡 𝐄𝗑αꭑρᥣ𝖾 2️⃣ </h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/96d709a2-8abd-4357-a52a-b299abf2669c" width="400px" height="397px"/>

</h1>

```TSX

//============ App.tsx ============== 

import ColorChanger from "./components/RangeSlider";

const App = () => {
  return <ColorChanger />;
};
export default App;

```

```TSX

//============ components/ColorChanger.tsx ============== 

import { motion, useSpring, useTransform } from "framer-motion";
import { ChangeEvent } from "react";

const ColorChanger = () => {
  const hue = useSpring(0, { stiffness: 300, damping: 30 });
  const backgroundColor = useTransform(hue, (h) => `hsl(${h}, 100%, 50%)`);

  const changeHandler = (e: ChangeEvent<HTMLInputElement>) => {
    hue.set(parseFloat(e.target.value));
  };

  return (
    <div>
      <motion.div
        className="color-box"
        style={{ backgroundColor, width: 200, height: 200, borderRadius: 16 }}
      />
      <div className="mt-4">
        <input
          type="range"
          min={0}
          max={360}
          step={1}
          defaultValue={0}
          onChange={changeHandler}
        />
      </div>
    </div>
  );
};

export default ColorChanger;

```

```css

/* ============== CSS ==============  */

@tailwind base;
@tailwind components;
@tailwind utilities;

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  background-color: #0d1017;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.box {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
  background-color: yellow;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #fff;
  font-size: 24px;
  text-align: center;
}

```