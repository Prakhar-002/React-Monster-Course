
<h1  align="center" > 🍄 𝐔𝗌𝖾 𝐌ⱺ𝗍𝗂ⱺ𐓣 𝐕αᥣυ𝖾  🥠</h1>

```TSX

import { useMotionValue, motion, useMotionValueEvent } from "framer-motion";

const MotionValueComponent = () => {
  const x = useMotionValue(0);

  useMotionValueEvent(x, "animationStart", () => {
    console.log("animation started on x");
  });

  useMotionValueEvent(x, "change", (latest) => {
    console.log("x changed to", latest);
  });

  return (
    <motion.div
      className="box"
      drag
      dragConstraints={{ left: 0, right: 200 }}
      style={{ x }}
    />
  );
};

export default MotionValueComponent;

```

<h1  align="center" >💡 𝐄𝗑αꭑρᥣ𝖾  1️⃣ </h1>

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

import { motion, useMotionValue } from "framer-motion";
import { ChangeEvent } from "react";

const RangeSlider = () => {
  const scale = useMotionValue(1);

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

<h1  align="center" > 💡 𝐄𝗑αꭑρᥣ𝖾 2️⃣ </h1>

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

import { motion, useMotionValue, useTransform } from "framer-motion";
import { ChangeEvent } from "react";

const ColorChanger = () => {
  const hue = useMotionValue(0);
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