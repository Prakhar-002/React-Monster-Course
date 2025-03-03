
<h1  align="center" > 🍄 𝐔𝗌𝖾 𝐓𝗋α𐓣𝗌𝖿ⱺ𝗋ꭑ  🥠</h1>

```TSX

import { motion, useScroll, useTransform } from "framer-motion";

const App = () => {
  const { scrollY } = useScroll();
  const rotate = useTransform(scrollY, [0, 100], [0, 360]);

  return (
    <div className="box">
      <motion.div className="box" style={{ rotate }} />

      <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
    </div>
  );
};
export default App;

```

</br>

<h1  align="center" >💡 𝐄𝗑αꭑρᥣ𝖾  1️⃣ </h1>

```TSX

//============ App.tsx ============== 

import DraggableBox from "./components/DraggableBox";

const App = () => {
  return <DraggableBox />;
};
export default App;

```

```TSX

//============ components/DraggableBox.tsx ============== 

import { motion, useMotionValue, useTransform } from "framer-motion";

const DraggableBox = () => {
  const x = useMotionValue(0);
  const y = useMotionValue(0);
  const backgroundColor = useTransform(x, [-100, 100], ["#ff0000", "#00ff00"]);

  return (
    <motion.div
      drag
      dragConstraints={{ left: -200, right: 200, top: -200, bottom: 200 }}
      style={{ x, y, backgroundColor }}
      className="w-32 h-32 flex items-center justify-center rounded-lg shadow-lg cursor-pointer"
    >
      <span className="text-white">Drag me!</span>
    </motion.div>
  );
};

export default DraggableBox;

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
