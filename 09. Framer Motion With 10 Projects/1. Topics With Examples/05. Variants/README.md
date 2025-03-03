
<h1  align="center" > 🍄 𝐕α𝗋𝗂α𐓣𝗍𝗌  🥠</h1>

Variants are a way to define different states or styles for our animations in a more organized way. Think of them as predefined animation setups that we can switch between easily.

## ⭐ Define Variants

Create a set of named styles (like "hidden," "visible," etc.) that describe how the element should look or behave in each state.

## ⭐ Use Variants

Apply these variants to our animated component, making it easy to switch between states without repeating code.

```TSX

import { useState } from "react";
import { motion } from "framer-motion";

const variants = {
  hidden: { opacity: 0, scale: 0.8 },
  visible: { opacity: 1, scale: 1 },
  exit: { opacity: 0, scale: 0.5 },
};

const Variants = () => {
  const [isVisible, setIsVisible] = useState(true);

  return (
    <motion.div
      variants={variants}
      initial="hidden"
      animate={isVisible ? "visible" : "hidden"}
      exit="exit"
      transition={{ duration: 1 }}
      onClick={() => setIsVisible(!isVisible)}
      className="box"
    ></motion.div>
  );
};

export default Variants;

```

<h1  align="center" >💡 𝐄𝗑αꭑρᥣ𝖾  1️⃣ </h1>

```TSX

//============ App.tsx ============== 

import AnimatedShape from "./components/ExampleOne";

const App = () => {
  return <AnimatedShape />;
};

export default App;

```

```TSX

//============ components/ExampleOne.tsx ============== 

import { motion } from "framer-motion";

const AnimatedShape = () => {
  const boxVariants = {
    initial: { scale: 1, rotate: 0, skew: 0 },
    hover: {
      scale: 1.2,
      rotate: 15,
      skew: "10deg",
      transition: { duration: 0.3 },
    },
    click: { scale: 0.9, rotate: -15, transition: { duration: 0.3 } },
  };

  return (
    <div className="flex items-center justify-center h-screen bg-gray-100">
      <motion.div
        className="w-40 h-40 bg-blue-500 rounded-lg"
        variants={boxVariants}
        initial="initial"
        whileHover="hover"
        whileTap="click"
      />
    </div>
  );
};

export default AnimatedShape;

```

</br>

<h1  align="center" > 💡 𝐄𝗑αꭑρᥣ𝖾 2️⃣ </h1>

```TSX

//============ App.tsx ============== 

import FlippingCard from "./components/FlippingCard";

const App = () => {
  return (
    <div className="min-h-screen flex items-center justify-center bg-gray-100">
      <FlippingCard />
    </div>
  );
};

export default App;

```

```TSX

//============ components/LoadingSpinner.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const cardVariants = {
  front: { rotateY: 0 },
  back: { rotateY: 180 },
};

const FlippingCard = () => {
  const [isFlipped, setIsFlipped] = useState(false);

  return (
    <motion.div
      className="perspective-1000"
      onClick={() => setIsFlipped(!isFlipped)}
    >
      <motion.div
        className="w-64 h-40 bg-white rounded-lg shadow-lg overflow-hidden transform-style-preserve-3d"
        variants={cardVariants}
        initial="front"
        animate={isFlipped ? "back" : "front"}
        transition={{ duration: 0.6 }}
      >
        <motion.div className="absolute inset-0 bg-white flex items-center justify-center text-xl font-bold">
          Front Side
        </motion.div>
        <motion.div className="absolute inset-0 bg-blue-500 flex items-center justify-center text-white text-xl font-bold rotate-y-180">
          Back Side
        </motion.div>
      </motion.div>
    </motion.div>
  );
};

export default FlippingCard;

```

```css

/* ============== CSS ==============  */

@tailwind base;
@tailwind components;
@tailwind utilities;

.perspective-1000 {
  perspective: 1000px;
}

.transform-style-preserve-3d {
  transform-style: preserve-3d;
}

```