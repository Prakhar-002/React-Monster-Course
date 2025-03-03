
<h1  align="center" > 🍄 𝐔𝗌𝖾 𝐒𝖼𝗋ⱺᥣᥣ  🥠</h1>

```TSX

import { motion, useMotionValueEvent, useScroll } from "framer-motion";

const Basic = () => {
  // const scroll = useScroll();
  // console.log(scroll);

  const { scrollY } = useScroll();

  useMotionValueEvent(scrollY, "change", (latest) => {
    console.log("Page scroll: ", latest);
  });

  return (
    <div>
      <motion.ul className="box">
        {/* LI * 100 */}
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
        <li></li> <li></li> <li></li> <li></li> <li></li>
      </motion.ul>
    </div>
  );
};

export default Basic;

```

<h1  align="center" >💡 𝐄𝗑αꭑρᥣ𝖾  1️⃣ </h1>

```TSX

//============ App.tsx ============== 

import ScrollAnimation from "./components/ScrollAnimation";

const App = () => {
  return (
    <div>
      <ScrollAnimation />
    </div>
  );
};
export default App;

```

```TSX

//============ components/ScrollAnimation.tsx ============== 

import { motion, useScroll, useTransform } from "framer-motion";

const ScrollAnimation = () => {
  const { scrollY } = useScroll();
  const scale = useTransform(scrollY, [0, 300], [1, 1.5]);
  const opacity = useTransform(scrollY, [0, 300], [1, 0]);

  return (
    <div className="h-screen flex items-center justify-center">
      <motion.div
        className="bg-blue-500 w-32 h-32 rounded-lg shadow-lg"
        style={{ scale, opacity }}
      ></motion.div>
      <div className="h-[150vh] w-full"></div>
    </div>
  );
};

export default ScrollAnimation;

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

import AnimationComponent from "./components/ScrollSections";

const App = () => {
  return (
    <div>
      <AnimationComponent />
      <div className="h-[200vh] bg-gray-800 flex items-center justify-center">
        <h2 className="text-white">Scroll Down</h2>
      </div>
    </div>
  );
};

export default App;

```

```TSX

//============ components/AnimationComponent.tsx ============== 

import { motion, useScroll, useTransform } from "framer-motion";

const AnimationComponent = () => {
  const { scrollY } = useScroll();

  const scale = useTransform(scrollY, [0, 1000], [1, 0.5]);
  const borderRadius = useTransform(scrollY, [0, 1000], ["0%", "50%"]);

  return (
    <div className="relative h-screen overflow-hidden">
      <motion.img
        src="https://images.unsplash.com/photo-1728408828574-70a460530093?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
        alt="Background"
        className="absolute inset-0 w-full h-full object-cover"
        style={{
          scale,
          borderRadius,
        }}
      />
      <div className="sticky top-0 h-screen flex items-center justify-center">
        <h1 className="text-white text-4xl">Scroll to Animate</h1>
      </div>
    </div>
  );
};

export default AnimationComponent;

```

```css

/* ============== CSS ==============  */

@tailwind base;
@tailwind components;
@tailwind utilities;

```