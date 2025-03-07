<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise 1️⃣: Bouncing Ball

**🎯 Objective:** Create a bouncing ball animation using keyframes.

**Instructions 📑:**

1. Create a simple circular div to represent a ball.
2. Use Framer Motion's `keyframes` to create a bouncing effect.
3. Style the ball with Tailwind CSS for color and size.

### Exercise 2️⃣: Pulsating Effect

**🎯 Objective:** Create a pulsating effect on a button using keyframes.

**Instructions 📑:**

1. Create a button using a `motion.button`.
2. Use keyframes to animate the scale of the button, making it pulse.
3. Apply Tailwind CSS for styling the button.

### Exercise 3️⃣: Color Change Animation

**🎯 Objective:** Create a component that changes color using keyframes.

**Instructions 📑:**

1. Create a square div that changes color continuously.
2. Use keyframes to define multiple colors for the animation.
3. Style the square with Tailwind CSS.

### Exercise 4️⃣: Sliding Text

**🎯 Objective:** Create a text component that slides in from the left using keyframes.

**Instructions 📑:**

1. Create a text component that animates in from the left.
2. Use keyframes to define the movement from off-screen to its final position.
3. Apply Tailwind CSS for styling the text.

### Exercise 5️⃣: Zigzag Animation

**🎯 Objective:** Create a zigzag animation for a box moving across the screen.

**Instructions 📑:**

1. Create a square box using `motion.div`.
2. Use keyframes to animate the box in a zigzag pattern horizontally.
3. Style the box with Tailwind CSS.

### Exercise 6️⃣: Wave Effect

**🎯 Objective:** Create a wave effect using a series of boxes.

**Instructions 📑:**

1. Create a series of boxes in a row.
2. Use keyframes to animate each box with a slight delay to create a wave effect.
3. Style the boxes with Tailwind CSS.

### Exercise 7️⃣: Background Animation

**🎯 Objective:** Create a background that changes color using keyframes.

**Instructions 📑:**

1. Create a full-screen div that acts as a background.
2. Use keyframes to animate the background color through multiple colors.
3. Style the div with Tailwind CSS to ensure it covers the screen.

</br>

<h1  align="center" > 🍄 𝐊𝖾𝗒𝖿𝗋αꭑ𝖾𝗌 🥠</h1>

```TSX

//============ App.tsx ============== 

import BouncingBall from "./components/1. BouncingBall";
import PulsatingButton from "./components/2. PulsatingButton";
import ColorChangeSquare from "./components/3. ColorChangeSquare";
import SlidingText from "./components/4. SlidingText";
import ZigzagAnimation from "./components/5. ZigzagAnimation";
import WaveEffect from "./components/6. WaveEffect";
import AnimatedBackground from "./components/7. AnimatedBackground";

const App = () => {
  return (
    <section className="h-screen flex justify-center items-center bg-[#0d1017]">
      {/* <BouncingBall /> */}
      {/* <PulsatingButton /> */}
      {/* <ColorChangeSquare /> */}
      {/* <SlidingText /> */}
      {/* <ZigzagAnimation /> */}
      {/* <WaveEffect /> */}
      <AnimatedBackground />
    </section>
  );
};

export default App;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 1️⃣: 𝐁ⱺυ𐓣𝖼𝗂𐓣𝗀 𝐁αᥣᥣ 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/BouncingBall.tsx ============== 

import { motion } from "framer-motion";

const BouncingBall = () => {
  return (
    <motion.div
      className="w-16 h-16 bg-yellow-400 rounded-full"
      animate={{
        y: [0, -100, 0],
      }}
      transition={{
        duration: 1,
        repeat: Infinity,
        repeatType: "loop",
        ease: "easeInOut",
      }}
    />
  );
};

export default BouncingBall;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 2️⃣: Pulsating Effect 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/PulsatingButton.tsx ============== 

import { motion } from "framer-motion";

const PulsatingButton = () => {
  return (
    <motion.button
      className="p-4 bg-green-500 text-white rounded"
      animate={{
        scale: [1, 1.1, 1],
      }}
      transition={{
        duration: 1,
        repeat: Infinity,
        repeatType: "loop",
        ease: "easeInOut",
      }}
    >
      Pulse Me
    </motion.button>
  );
};

export default PulsatingButton;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 3️⃣: 𝐂ⱺᥣⱺ𝗋 𝐂ɦα𐓣𝗀𝖾 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/ColorChangeSquare.tsx ============== 

import { motion } from "framer-motion";

const ColorChangeSquare = () => {
  return (
    <motion.div
      className="w-32 h-32"
      animate={{
        backgroundColor: ["#FF0000", "#00FF00", "#0000FF", "#FF0000"],
      }}
      transition={{
        duration: 3,
        ease: "linear",
        repeat: Infinity,
      }}
    />
  );
};

export default ColorChangeSquare;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 4️⃣: 𝐒ᥣ𝗂ᑯ𝗂𐓣𝗀 𝐓𝖾𝗑𝗍 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/SlidingText.tsx ============== 

import { motion } from "framer-motion";

const SlidingText = () => {
  return (
    <motion.h1
      className="text-2xl font-bold text-white"
      initial={{ x: "-100%" }}
      animate={{ x: 0 }}
      transition={{ duration: 1 }}
    >
      Slide In Text
    </motion.h1>
  );
};

export default SlidingText;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 5️⃣: 𝐙𝗂𝗀ƶα𝗀 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/ZigzagAnimation.tsx ============== 

import { motion } from "framer-motion";

const ZigzagAnimation = () => {
  return (
    <motion.div
      className="w-16 h-16 bg-green-500"
      animate={{
        x: [0, 50, 0, -50, 0],
        y: [0, -50, 0, 50, 0],
      }}
      transition={{
        duration: 2,
        repeat: Infinity,
        ease: "easeInOut",
      }}
    />
  );
};

export default ZigzagAnimation;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 6️⃣: 𝐖α𝗏𝖾 𝐄𝖿𝖿𝖾𝖼𝗍 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/WaveEffect.tsx ============== 

import { motion } from "framer-motion";

const WaveEffect = () => {
  const boxes = Array.from({ length: 5 });

  return (
    <div className="flex space-x-2">
      {boxes.map((_, index) => (
        <motion.div
          key={index}
          className="w-16 h-16 bg-purple-500"
          animate={{ y: [0, -20, 0] }}
          transition={{
            duration: 0.6,
            repeat: Infinity,
            repeatType: "reverse",
            delay: index * 0.1,
          }}
        />
      ))}
    </div>
  );
};

export default WaveEffect;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 7️⃣: 𝐁α𝖼𝗄𝗀𝗋ⱺυ𐓣ᑯ 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/AnimatedBackground.tsx ============== 

import { motion } from "framer-motion";

const AnimatedBackground = () => {
  return (
    <motion.div
      className="w-screen h-screen"
      animate={{
        backgroundColor: ["#FF0000", "#00FF00", "#0000FF", "#FF0000"],
      }}
      transition={{
        duration: 5,
        ease: "linear",
        repeat: Infinity,
      }}
    />
  );
};

export default AnimatedBackground;

```
