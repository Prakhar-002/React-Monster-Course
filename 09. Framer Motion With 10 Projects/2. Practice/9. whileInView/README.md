<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise 1️⃣: Staggered Fade and Slide In

**🎯 Objective:** Create a list of items that fade and slide in staggered when they come into view.

**Instructions:** 📑

1. Create an array of items to display.
2. Use a `motion.ul` for the list and `motion.li` for each item.
3. Implement staggered animations using `variants` and the `transition` prop.

### Exercise 2️⃣: Card Flip Animation

**🎯 Objective:** Create a card that flips when it comes into view, revealing its back side.

**Instructions:** 📑

1. Create a card component with a front and back side.
2. Use `whileInView` to animate the rotation along the Y-axis.
3. Style with Tailwind CSS.

### Exercise 3️⃣: Complex Timeline Animation

**🎯 Objective:** Create a sequence of animations that occurs when a section comes into view, including rotation, scaling, and fading.

**Instructions:** 📑

1. Set up multiple elements that will animate in a sequence.
2. Use variants for complex animations.
3. Control timing with the `transition` property.

### Exercise 4️⃣: Interactive Hover and In-View Animation

**🎯 Objective:** Create a grid of cards that scale and change color when hovered over and animate in when in view.

**Instructions:** 📑

1. Create a grid layout of cards.
2. Use `whileInView` for entrance animations.
3. Add hover effects with Tailwind and Framer Motion.

</br>

<h1  align="center" > 🍄 𝐖ɦ𝗂ᥣ𝖾 𝚰𐓣 𝐕𝗂𝖾ω 🥠</h1>

```TSX

//============ App.tsx ============== 

import StaggeredList from "./components/1. StaggeredList";
import CardFlip from "./components/2. CardFlip";
import TimelineAnimation from "./components/3. TimelineAnimation";
import InteractiveCards from "./components/4. InteractiveCards";

const App = () => {
  return (
    <section className="h-[150rem] flex justify-center items-center bg-[#0d1017]">
      {/* <StaggeredList /> */}
      {/* <CardFlip /> */}
      {/* <TimelineAnimation /> */}
      <InteractiveCards />
    </section>
  );
};

export default App;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 1️⃣: 𝐒𝗍α𝗀𝗀𝖾𝗋𝖾ᑯ 𝐅αᑯ𝖾 α𐓣ᑯ 𝐒ᥣ𝗂ᑯ𝖾 𝚰𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/4237fcbd-ad47-46a0-aef3-5e6e1f1f53fc" width="237px" height="400px"/>

</h1>

```TSX

//============ components/StaggeredList.tsx ============== 

import { motion } from "framer-motion";

const StaggeredList = () => {
  const items = ["Item 1", "Item 2", "Item 3", "Item 4", "Item 5"];

  const listVariants = {
    hidden: { opacity: 0 },
    visible: { opacity: 1 },
  };

  return (
    <motion.ul
      className="flex flex-col items-center"
      initial="hidden"
      whileInView="visible"
      variants={listVariants}
      transition={{ staggerChildren: 0.3 }}
    >
      {items.map((item, index) => (
        <motion.li
          key={index}
          className="bg-blue-500 p-4 text-white my-2 rounded-lg"
          initial={{ opacity: 0, y: 20 }}
          whileInView={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.5 }}
        >
          {item}
        </motion.li>
      ))}
    </motion.ul>
  );
};

export default StaggeredList;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 2️⃣: 𝐂α𝗋ᑯ 𝐅ᥣ𝗂ρ 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/b03274d4-33b2-44a8-a81f-7b0dd3ac77cf" width="426px" height="500px"/>

</h1>

```TSX

//============ components/CardFlip.tsx ============== 

import { motion } from "framer-motion";

const CardFlip = () => {
  return (
    <motion.div className="perspective-1000 w-64 h-64">
      <motion.div
        className="relative w-full h-full"
        initial={{ rotateY: 0 }}
        whileInView={{ rotateY: 180 }}
        transition={{ duration: 0.6 }}
        style={{ transformStyle: "preserve-3d" }}
      >
        <div className="absolute w-full h-full bg-blue-500 text-white flex items-center justify-center rounded-lg">
          Front
        </div>
        <div
          className="absolute w-full h-full bg-green-500 text-white flex items-center justify-center rounded-lg"
          style={{ transform: "rotateY(180deg)" }}
        >
          Back
        </div>
      </motion.div>
    </motion.div>
  );
};

export default CardFlip;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 3️⃣: 𝐂ⱺꭑρᥣ𝖾𝗑 𝐓𝗂ꭑ𝖾ᥣ𝗂𐓣𝖾 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/a3465ffa-9989-4ae5-9ed8-997416d4552b" width="400px" height="316px"/>

</h1>

```TSX

//============ components/TimelineAnimation.tsx ============== 

import { motion } from "framer-motion";

const TimelineAnimation = () => {
  const itemVariants = {
    hidden: { opacity: 0, scale: 0.5, rotate: 180 },
    visible: { opacity: 1, scale: 1, rotate: 0 },
  };

  return (
    <motion.div
      className="flex items-center"
      initial="hidden"
      whileInView="visible"
      transition={{ staggerChildren: 0.5 }}
    >
      {[1, 2, 3].map((item) => (
        <motion.div
          key={item}
          variants={itemVariants}
          className="bg-purple-500 ml-[2rem] p-4 text-white my-2 rounded-lg"
        >
          Item {item}
        </motion.div>
      ))}
    </motion.div>
  );
};

export default TimelineAnimation;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 4️⃣: Interactive Hover and In-View Animation 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/676f8880-e024-4408-b0d1-248dbb6578df" width="250px" height="202px"/>

</h1>

```TSX

//============ components/InteractiveCards.tsx ============== 

import { motion } from "framer-motion";

const InteractiveCards = () => {
  return (
    <div className="grid grid-cols-2 gap-4">
      {[1, 2, 3, 4].map((item) => (
        <motion.div
          key={item}
          className="bg-blue-500 p-6 text-white text-center rounded-lg"
          initial={{ scale: 0.8 }}
          whileInView={{ scale: 1 }}
          whileHover={{ scale: 1.1, backgroundColor: "#3b82f6" }}
          transition={{ duration: 0.3 }}
        >
          <h3 className="text-2xl">Card {item}</h3>
        </motion.div>
      ))}
    </div>
  );
};

export default InteractiveCards;

```
