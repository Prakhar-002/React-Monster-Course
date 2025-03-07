
<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise 1️⃣: Draggable Box

**🎯 Objective:** Create a draggable box that updates its position using `useMotionValue`.

**Instructions:** 📑

1. Create a `motion.div` that can be dragged around.
2. Use `useMotionValue` to track the x and y position of the box.
3. Display the current position of the box as text.

### Exercise 2️⃣: Hover-Linked Scale

**🎯 Objective:** Create a button that scales up when hovered, using `useMotionValue`.

**Instructions:** 📑

1. Create a `motion.button`.
2. Use `useMotionValue` to control the scale of the button.
3. Update the scale value on hover and reset it when not hovered.

### Exercise 3️⃣: Spring-Animated Position

**🎯 Objective:** Create a box that springs to a new position when clicked, using `useMotionValue`.

**Instructions:** 📑

1. Create a `motion.div` that can be clicked to move to a new position.
2. Use `useMotionValue` to control the x and y position.
3. Animate the box to the new position with a spring effect.

### Exercise 4️⃣: Dynamic Rotation

**🎯 Objective:** Create a component that rotates based on a motion value.

**Instructions:** 📑

1. Create a `motion.div` that rotates when a button is clicked.
2. Use `useMotionValue` to track the rotation angle.
3. Animate the rotation of the box based on the motion value.

</br>

<h1  align="center" > 🍄 𝐔𝗌𝖾 𝐌ⱺ𝗍𝗂ⱺ𐓣 𝐕αᥣυ𝖾 🥠</h1>

```TSX

//============ App.tsx ============== 

import DraggableBox from "./components/1. DraggableBox";
import HoverLinkedScale from "./components/2. HoverLinkedScale";
import SpringAnimatedPosition from "./components/3. SpringAnimatedPosition";
import DynamicRotation from "./components/4. DynamicRotation";

const App = () => {
  return (
    <section className="h-screen flex justify-center items-center bg-[#0d1017]">
      {/* <DraggableBox /> */}
      {/* <HoverLinkedScale /> */}
      {/* <SpringAnimatedPosition /> */}
      <DynamicRotation />
    </section>
  );
};

export default App;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 1️⃣: 𝐃𝗋α𝗀𝗀αᑲᥣ𝖾 𝐁ⱺ𝗑 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/DraggableBox.tsx ============== 

import { motion, useMotionValue } from "framer-motion";

const DraggableBox = () => {
  const x = useMotionValue(0);
  const y = useMotionValue(0);

  return (
    <div className="flex flex-col items-center">
      <motion.div
        drag
        style={{ x, y }}
        className="w-32 h-32 bg-blue-500 rounded"
      />
      <p className="text-white">
        Position: ({x.get().toFixed(2)}, {y.get().toFixed(2)})
      </p>
    </div>
  );
};

export default DraggableBox;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 2️⃣: 𝐇ⱺ𝗏𝖾𝗋-𝐋𝗂𐓣𝗄𝖾ᑯ 𝐒𝖼αᥣ𝖾 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/HoverLinkedScale.tsx ============== 

import { motion, useMotionValue } from "framer-motion";

const HoverLinkedScale = () => {
  const scale = useMotionValue(1);

  return (
    <motion.button
      onHoverStart={() => scale.set(1.2)}
      onHoverEnd={() => scale.set(1)}
      style={{ scale }}
      className="p-4 bg-blue-500 text-white rounded"
    >
      Hover Me
    </motion.button>
  );
};

export default HoverLinkedScale;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 3️⃣: 𝐒ρ𝗋𝗂𐓣𝗀-𝐀𐓣𝗂ꭑα𝗍𝖾ᑯ 𝐏ⱺ𝗌𝗂𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/SpringAnimatedPosition.tsx ============== 

import { motion, useMotionValue } from "framer-motion";

const SpringAnimatedPosition = () => {
  const x = useMotionValue(0);
  const y = useMotionValue(0);

  const moveBox = () => {
    x.set(Math.random() * 300);
    y.set(Math.random() * 300);
  };

  return (
    <div className="relative">
      <motion.div
        style={{ x, y }}
        className="w-32 h-32 bg-blue-500 rounded"
        onClick={moveBox}
      >
        Click Me
      </motion.div>
    </div>
  );
};

export default SpringAnimatedPosition;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 4️⃣: 𝐃𝗒𐓣αꭑ𝗂𝖼 𝐑ⱺ𝗍α𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/DynamicRotation.tsx ============== 

import { motion, useMotionValue } from "framer-motion";

const DynamicRotation = () => {
  const rotation = useMotionValue(0);

  const rotateBox = () => {
    rotation.set(rotation.get() + 45);
  };

  return (
    <motion.div
      style={{ rotate: rotation }}
      className="w-32 h-32 bg-blue-500 rounded"
      onClick={rotateBox}
    >
      Click Me
    </motion.div>
  );
};

export default DynamicRotation;

```
