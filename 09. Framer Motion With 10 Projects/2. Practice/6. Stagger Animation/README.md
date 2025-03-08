<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise 1️⃣: Staggered List Items

**🎯 Objective:** Create a list of items that animate into view with a staggered effect.

**Instructions 📑:**

1. Create an array of items (e.g., strings).
2. Use `motion.div` to display each item.
3. Implement a stagger effect so that each item appears one after the other when the component mounts.

### Exercise 2️⃣: Staggered Image Gallery

**🎯 Objective:** Create an image gallery where images fade in with a staggered effect when loaded.

**Instructions 📑:**

1. Create an array of image URLs.
2. Use `motion.img` to display each image.
3. Implement a staggered effect for images to fade in as they load.

### Exercise 3️⃣: Staggered Button Press

**🎯 Objective:** Create a set of buttons that animate into view with a staggered effect when hovered over.

**Instructions 📑:**

1. Create a set of buttons.
2. Use `motion.button` to animate each button.
3. Implement a staggered animation effect when hovering over the button container.

### Exercise 4️⃣: Staggered Grid Layout

**🎯 Objective:** Create a grid of items that animate into view with a staggered effect.

**Instructions 📑:**

1. Create an array of items to be displayed in a grid format.
2. Use `motion.div` for each grid item.
3. Implement a staggered effect so that each grid item animates in with a slight delay relative to its position.

### Exercise 5️⃣: Staggered Text Reveal

**🎯 Objective:** Create a title where each letter animates into view with a staggered effect.

**Instructions 📑:**

1. Split a string into an array of characters.
2. Use `motion.span` to display each character.
3. Implement a staggered animation effect for the characters to appear one after the other.

</br>

<h1  align="center" > 🍄 𝐒𝗍α𝗀𝗀𝖾𝗋 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣 🥠</h1>

```TSX

//============ App.tsx ============== 

import StaggeredList from "./components/1. StaggeredList";
import StaggeredImageGallery from "./components/2. StaggeredImageGallery";
import StaggeredButtonPress from "./components/3. StaggeredButtonPress";
import StaggeredGridLayout from "./components/4. StaggeredGridLayout";
import StaggeredTextReveal from "./components/5. StaggeredTextReveal";

const App = () => {
  return (
    <section className="h-screen flex justify-center items-center bg-[#0d1017]">
      {/* <StaggeredList /> */}
      {/* <StaggeredImageGallery /> */}
      {/* <StaggeredButtonPress /> */}
      {/* <StaggeredGridLayout /> */}
      <StaggeredTextReveal />
    </section>
  );
};

export default App;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 1️⃣: 𝐒𝗍α𝗀𝗀𝖾𝗋𝖾ᑯ 𝐋𝗂𝗌𝗍 𝚰𝗍𝖾ꭑ𝗌 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/8644af18-a73d-4ebf-83bf-312cf426a5b2" width="258px" height="400px"/>

</h1>

```TSX

//============ components/StaggeredList.tsx ============== 

import { motion } from "framer-motion";

const items = ["Item 1", "Item 2", "Item 3", "Item 4", "Item 5"];

const staggerVariants = {
  hidden: { opacity: 0 },
  visible: { opacity: 1 },
};

const StaggeredList = () => {
  return (
    <motion.ul
      initial="hidden"
      animate="visible"
      variants={{
        visible: {
          transition: { staggerChildren: 0.2 },
        },
      }}
    >
      {items.map((item, index) => (
        <motion.li
          key={index}
          variants={staggerVariants}
          className="mb-2 p-5 bg-yellow-300"
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

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 2️⃣: 𝐒𝗍α𝗀𝗀𝖾𝗋𝖾ᑯ 𝚰ꭑα𝗀𝖾 𝐆αᥣᥣ𝖾𝗋𝗒 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/617e2c4e-c789-48ad-ac65-fa1db4ab9a06" width="269px" height="400px"/>

</h1>

```TSX

//============ components/StaggeredImageGallery.tsx ============== 

import { motion } from "framer-motion";

const images = [
  "https://images.unsplash.com/photo-1507936580189-3816b4abf640?q=80&w=3870&auto=format&fit=crop",
  "https://images.unsplash.com/photo-1528183429752-a97d0bf99b5a?q=80&w=3870&auto=format&fit=crop",
  "https://images.unsplash.com/photo-1448518340475-e3c680e9b4be?q=80&w=3200&auto=format&fit=crop",
];

const staggerVariants = {
  hidden: { opacity: 0 },
  visible: { opacity: 1 },
};

const StaggeredImageGallery = () => {
  return (
    <motion.div
      className="flex"
      initial="hidden"
      animate="visible"
      variants={{
        visible: {
          transition: { staggerChildren: 0.3 },
        },
      }}
    >
      {images.map((src, index) => (
        <motion.img
          key={index}
          src={src}
          alt={`Image ${index}`}
          variants={staggerVariants}
          className="w-[20rem] h-auto ml-[2rem] rounded "
        />
      ))}
    </motion.div>
  );
};

export default StaggeredImageGallery;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 3️⃣: 𝐒𝗍α𝗀𝗀𝖾𝗋𝖾ᑯ 𝐁υ𝗍𝗍ⱺ𐓣 𝐏𝗋𝖾𝗌𝗌 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/ce477a7d-beff-4f37-b658-cb6f30a6d262" width="300px" height="167px"/>

</h1>

```TSX

//============ components/StaggeredButtonPress.tsx ============== 

import { motion } from "framer-motion";

const buttons = ["Button 1", "Button 2", "Button 3", "Button 4"];

const StaggeredButtonPress = () => {
  return (
    <motion.div
      className="flex space-x-4"
      whileHover={{ transition: { staggerChildren: 0.2 } }}
    >
      {buttons.map((label, index) => (
        <motion.button
          key={index}
          className="p-2 bg-blue-500 text-white rounded"
          whileHover={{ scale: 1.1 }}
        >
          {label}
        </motion.button>
      ))}
    </motion.div>
  );
};

export default StaggeredButtonPress;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 4️⃣: 𝐒𝗍α𝗀𝗀𝖾𝗋𝖾ᑯ 𝐆𝗋𝗂ᑯ 𝐋α𝗒ⱺυ𝗍 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/46966612-8a8c-4d7e-b9d0-dc290ad772ac" width="350px" height="229px"/>

</h1>

```TSX

//============ components/StaggeredGridLayout.tsx ============== 

import { motion } from "framer-motion";

const items = ["Item 1", "Item 2", "Item 3", "Item 4", "Item 5", "Item 6"];

const staggerVariants = {
  hidden: { opacity: 0 },
  visible: { opacity: 1 },
};

const StaggeredGridLayout = () => {
  return (
    <motion.div
      className="grid grid-cols-3 gap-4"
      initial="hidden"
      animate="visible"
      variants={{
        visible: {
          transition: { staggerChildren: 0.2 },
        },
      }}
    >
      {items.map((item, index) => (
        <motion.div
          key={index}
          variants={staggerVariants}
          className="p-4 bg-gray-200 rounded"
        >
          {item}
        </motion.div>
      ))}
    </motion.div>
  );
};

export default StaggeredGridLayout;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 5️⃣: 𝐒𝗍α𝗀𝗀𝖾𝗋𝖾ᑯ 𝐓𝖾𝗑𝗍 𝐑𝖾𝗏𝖾αᥣ 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/6f269175-10a5-4e5e-b237-5b4f3cc3a80c" width="250px" height="137px"/>

</h1>

```TSX

//============ components/StaggeredTextReveal.tsx ============== 

import { motion } from "framer-motion";

const text = "Hello World!";

const staggerVariants = {
  hidden: { opacity: 0 },
  visible: { opacity: 1 },
};

const StaggeredTextReveal = () => {
  return (
    <motion.h1
      className="text-4xl font-bold text-white"
      initial="hidden"
      animate="visible"
      variants={{
        visible: {
          transition: { staggerChildren: 0.1 },
        },
      }}
    >
      {text.split("").map((char, index) => (
        <motion.span key={index} variants={staggerVariants}>
          {char}
        </motion.span>
      ))}
    </motion.h1>
  );
};

export default StaggeredTextReveal;

```
