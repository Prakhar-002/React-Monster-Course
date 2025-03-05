
<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise 1: Simple Fade-In Component

**Objective:** Create a component that fades in when it appears.

**Instructions:**

1. Define a variant for the fade-in effect.
2. Create a `motion.div` that uses this variant.
3. Use Tailwind CSS for styling the component.

### Exercise 2: Navigation Menu with Slide Animation

**Objective:** Create a navigation menu that slides in from the side.

**Instructions:**

1. Define variants for the open and closed states of the menu.
2. Create a `motion.div` for the menu.
3. Style the menu with Tailwind CSS.

### Exercise 3: Tooltip with Variants

**Objective:** Create a tooltip that appears and disappears with a fade effect.

**Instructions:**

1. Define variants for the visible and hidden states of the tooltip.
2. Create a `motion.div` for the tooltip.
3. Style the tooltip with Tailwind CSS.

### Exercise 4: Toggle Switch Animation

**Objective:** Create a toggle switch that animates between "on" and "off" states.

**Instructions:**

1. Define variants for the "on" and "off" positions of the switch.
2. Create a `motion.div` that represents the switch.
3. Use Tailwind CSS for styling.

### Exercise 5: Dynamic List Animation

**Objective:** Create a list that animates items when they are added or removed.

**Instructions:**

1. Define variants for entering and exiting the list.
2. Create a dynamic list that uses `motion.div` for each item.
3. Style the list with Tailwind CSS.

</br>

<h1  align="center" > 🍄 𝐕α𝗋𝗂α𐓣𝗍𝗌 🥠</h1>

```TSX

//============ App.tsx ============== 

import FadeInComponent from "./components/1. FadeInComponent";
import SlidingMenu from "./components/2. SlidingMenu";
import Tooltip from "./components/3. Tooltip";
import ToggleSwitch from "./components/4. ToggleSwitch";
import DynamicList from "./components/5. DynamicList";

const App = () => {
  return (
    <section
      className="h-screen flex justify-center
     items-center bg-[#0d1017]"
    >
      {/* <FadeInComponent /> */}
      {/* <SlidingMenu /> */}
      {/* <Tooltip /> */}
      {/* <ToggleSwitch /> */}
      <DynamicList />
    </section>
  );
};

export default App;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 1️⃣: 𝐒𝗂ꭑρᥣ𝖾 𝐅αᑯ𝖾-𝚰𐓣 𝐂ⱺꭑρⱺ𐓣𝖾𐓣𝗍 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/FadeInComponent.tsx ============== 

import { motion } from "framer-motion";

const fadeInVariant = {
  hidden: { opacity: 0 },
  visible: { opacity: 1 },
};

const FadeInComponent = () => {
  return (
    <motion.div
      variants={fadeInVariant}
      initial="hidden"
      animate="visible"
      transition={{ duration: 0.5 }}
      className="bg-blue-500 p-4 rounded shadow"
    >
      <h2 className="text-white">Fade In Component</h2>
    </motion.div>
  );
};

export default FadeInComponent;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 2️⃣: 𝐍α𝗏𝗂𝗀α𝗍𝗂ⱺ𐓣 𝐌𝖾𐓣υ ω𝗂𝗍ɦ 𝐒ᥣ𝗂ᑯ𝖾 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/SlidingMenu.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const menuVariants = {
  closed: { x: "-100%" },
  open: { x: 0 },
};

const SlidingMenu = () => {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <div>
      <button
        onClick={() => setIsOpen(!isOpen)}
        className="p-2 bg-gray-500 text-white"
      >
        Toggle Menu
      </button>
      <motion.div
        variants={menuVariants}
        initial="closed"
        animate={isOpen ? "open" : "closed"}
        transition={{ duration: 0.3 }}
        className="fixed top-0 left-0 w-64 h-full bg-blue-600"
      >
        <ul className="p-4 text-white">
          <li>Home</li>
          <li>About</li>
          <li>Contact</li>
        </ul>
      </motion.div>
    </div>
  );
};

export default SlidingMenu;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 3️⃣: 𝐓ⱺⱺᥣ𝗍𝗂ρ ω𝗂𝗍ɦ 𝐕α𝗋𝗂α𐓣𝗍𝗌 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/Tooltip.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const tooltipVariants = {
  hidden: { opacity: 0, y: -10 },
  visible: { opacity: 1, y: 0 },
};

const Tooltip = () => {
  const [visible, setVisible] = useState(false);

  return (
    <div className="relative inline-block">
      <button
        onMouseEnter={() => setVisible(true)}
        onMouseLeave={() => setVisible(false)}
        className="p-2 bg-blue-500 text-white"
      >
        Hover over me
      </button>
      {visible && (
        <motion.div
          variants={tooltipVariants}
          initial="hidden"
          animate="visible"
          exit="hidden"
          transition={{ duration: 0.2 }}
          className="absolute bg-gray-700 text-white p-2 rounded"
        >
          Tooltip content
        </motion.div>
      )}
    </div>
  );
};

export default Tooltip;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 4️⃣: 𝐓ⱺ𝗀𝗀ᥣ𝖾 𝐒ω𝗂𝗍𝖼ɦ 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/ToggleSwitch.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const switchVariants = {
  off: { x: 0 },
  on: { x: 70 },
};

const ToggleSwitch = () => {
  const [isOn, setIsOn] = useState(false);

  return (
    <div className="relative inline-block w-36 h-16">
      <div
        className={`w-full h-full rounded-full bg-gray-300 cursor-pointer ${
          isOn ? "bg-green-500" : ""
        }`}
        onClick={() => setIsOn(!isOn)}
      />
      <motion.div
        className="absolute top-1 left-1 w-14 h-14 rounded-full bg-white shadow"
        variants={switchVariants}
        animate={isOn ? "on" : "off"}
        transition={{ type: "spring", stiffness: 300 }}
      />
    </div>
  );
};

export default ToggleSwitch;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 5️⃣: 𝐃𝗒𐓣αꭑ𝗂𝖼 𝐋𝗂𝗌𝗍 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/DynamicList.tsx ============== 

import { useState } from "react";
import { motion, AnimatePresence } from "framer-motion";

const listVariants = {
  enter: { opacity: 1, y: 0 },
  exit: { opacity: 0, y: -20 },
};

const DynamicList: React.FC = () => {
  const [items, setItems] = useState<string[]>([]);

  const addItem = () => {
    const newItem = `Item ${items.length + 1}`;
    setItems((prev) => [...prev, newItem]);
  };

  const removeItem = (index: number) => {
    setItems((prev) => prev.filter((_, i) => i !== index));
  };

  return (
    <div>
      <button onClick={addItem} className="mb-4 p-2 bg-blue-500 text-white">
        Add Item
      </button>
      <AnimatePresence>
        {items.map((item, index) => (
          <motion.div
            key={item}
            variants={listVariants}
            initial="exit"
            animate="enter"
            exit="exit"
            transition={{ duration: 0.3 }}
            className="p-2 bg-gray-200 mb-2 rounded"
            onClick={() => removeItem(index)}
          >
            {item}
          </motion.div>
        ))}
      </AnimatePresence>
    </div>
  );
};

export default DynamicList;

```
