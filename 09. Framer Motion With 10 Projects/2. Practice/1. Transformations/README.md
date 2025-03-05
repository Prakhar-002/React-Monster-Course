
<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise 1: Basic Translation

**Objective:** Create a box that moves across the screen.

1. **Setup:** Create a simple box using a `div`.
2. **Task:** Use Framer Motion to animate the box from the left side of the screen to the right.

### Exercise 2: Vertical Movement

**Objective:** Make a circle bounce up and down.

1. **Setup:** Create a circle using CSS.
2. **Task:** Animate the circle to move vertically, bouncing at the top and bottom of the container.

### Exercise 3: Rotation Animation

**Objective:** Spin an icon continuously.

1. **Setup:** Use an SVG icon or image.
2. **Task:** Animate the icon to rotate indefinitely.

### Exercise 4: Skewed Transition

**Objective:** Animate a rectangle that skews when clicked.

1. **Setup:** Create a rectangle using tailwind CSS.
2. **Task:** On click, skew the rectangle and return to normal when clicked again.

### Exercise 5: Combined Transformations

**Objective:** Create a complex animation combining multiple transformations.

1. **Setup:** Create a shape (e.g., a square or circle).
2. **Task:** Animate the shape to move diagonally while rotating and scaling simultaneously.

### Exercise 6: Sequential Transformations

**Objective:** Create an animation sequence.

1. **Setup:** Use multiple elements (e.g., squares).
2. **Task:** Animate them in a sequence where one moves right, then the next one follows after a delay, using different transformations (e.g., move, rotate).

</br>

<h1  align="center" > 🍄 𝐓𝗋α𐓣𝗌𝖿ⱺ𝗋ꭑα𝗍𝗂ⱺ𐓣𝗌 🥠</h1>

```TSX

//============ App.tsx ============== 

import Box from "./components/1. Box";
import BouncingCircle from "./components/2. BouncingCircle";
import SpinningIcon from "./components/3. SpinningIcon";
import SkewRectangle from "./components/4. SkewRectangle";
import ComplexAnimation from "./components/5. ComplexAnimation";
import SequentialBoxes from "./components/6. SequentialBoxes";

const App = () => {
  return (
    <section className="h-screen flex justify-center items-center bg-[#0d1017]">
      {/* <Box /> */}
      {/* <BouncingCircle /> */}
      {/* <SpinningIcon /> */}
      {/* <SkewRectangle /> */}
      {/* <ComplexAnimation /> */}
      <SequentialBoxes />
    </section>
  );
};

export default App;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 1️⃣: 𝐁α𝗌𝗂𝖼 𝐓𝗋α𐓣𝗌ᥣα𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/Box.tsx ============== 

import { motion } from "framer-motion";

const Box = () => (
  <motion.div
    className="bg-blue-500 w-20 h-20"
    initial={{ x: -100 }}
    animate={{ x: 100 }}
    transition={{ duration: 2 }}
  />
);

export default Box;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 2️⃣: 𝐕𝖾𝗋𝗍𝗂𝖼αᥣ 𝐌ⱺ𝗏𝖾ꭑ𝖾𐓣𝗍 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/BouncingCircle.tsx ============== 

import { motion } from "framer-motion";

const BouncingCircle = () => (
  <motion.div
    className="bg-red-500 rounded-full w-20 h-20"
    animate={{ y: [0, -100, 0] }}
    transition={{ duration: 1, repeat: Infinity, ease: "easeInOut" }}
  />
);

export default BouncingCircle;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 3️⃣: 𝐑ⱺ𝗍α𝗍𝗂ⱺ𐓣 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/SpinningIcon.tsx ============== 

import { motion } from "framer-motion";

const SpinningIcon = () => (
  <motion.img
    src="https://repository-images.githubusercontent.com/157846876/70574400-9e6a-11e9-8708-22d4bf4c3322"
    className="w-20 h-20"
    animate={{ rotate: 360 }}
    transition={{ duration: 2, repeat: Infinity, ease: "linear" }}
  />
);

export default SpinningIcon;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 4️⃣: 𝐒𝗄𝖾ω𝖾ᑯ 𝐓𝗋α𐓣𝗌𝗂𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/SkewRectangle.tsx ============== 

import { motion } from "framer-motion";
import { useState } from "react";

const SkewRectangle = () => {
  const [isSkewed, setIsSkewed] = useState(true);

  return (
    <motion.div
      className="bg-yellow-500 w-40 h-20"
      onClick={() => setIsSkewed(!isSkewed)}
      animate={{ skewX: isSkewed ? 20 : 0 }}
      transition={{ duration: 0.5 }}
    />
  );
};

export default SkewRectangle;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 5️⃣: 𝐂ⱺꭑᑲ𝗂𐓣𝖾ᑯ 𝐓𝗋α𐓣𝗌𝖿ⱺ𝗋ꭑα𝗍𝗂ⱺ𐓣𝗌 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/ComplexAnimation.tsx ============== 

import { motion } from "framer-motion";

const ComplexAnimation = () => (
  <motion.div
    className="bg-purple-500 w-20 h-20"
    animate={{ x: 200, rotate: 360, scale: 1.5 }}
    transition={{ duration: 2 }}
  />
);

export default ComplexAnimation;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 6️⃣: 𝐒𝖾𝗊υ𝖾𐓣𝗍𝗂αᥣ 𝐓𝗋α𐓣𝗌𝖿ⱺ𝗋ꭑα𝗍𝗂ⱺ𐓣𝗌 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/SequentialBoxes.tsx ============== 

import { motion } from "framer-motion";

const SequentialBoxes = () => (
  <>
    {[...Array(3)].map((_, i) => (
      <motion.div
        key={i}
        className="bg-teal-500 w-20 h-20 m-2"
        animate={{ x: 100 }}
        transition={{ duration: 0.5, delay: i * 0.5 }}
      />
    ))}
  </>
);

export default SequentialBoxes;

```

</br>
