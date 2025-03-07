<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise 1️⃣: Swipeable Card

**🎯 Objective:** Create a card that can be swiped left or right to remove it from the view.

**Instructions 📑:**

1. Create a `motion.div` to represent the card.
2. Use Framer Motion's `useDrag` to detect swipe gestures.
3. Animate the card's position based on the swipe.

### Exercise 2️⃣: Draggable Box

**🎯 Objective:** Create a box that can be dragged around the screen.

**Instructions 📑:**

1. Create a `motion.div` that represents the box.
2. Use Framer Motion's `drag` functionality to allow dragging.
3. Style the box with Tailwind CSS.

### Exercise 3️⃣: Rotate on Drag

**🎯 Objective:** Create a box that rotates when dragged.

**Instructions 📑:**

1. Create a `motion.div` that represents the box.
2. Use the `onDrag` event to calculate the rotation angle.
3. Animate the rotation of the box based on the drag movement.

### Exercise 4️⃣: Tap to Change Color

**🎯 Objective:** Create a box that changes color when tapped.

**Instructions 📑:**

1. Create a `motion.div` for the box.
2. Use the `onTap` event to change the box's color.
3. Use Tailwind CSS for styling.

### Exercise 5️⃣: Long Press to Change Size

**🎯 Objective:** Create a box that changes its size when long-pressed.

**Instructions 📑:**

1. Create a `motion.div` that represents the box.
2. Use the `onTap` event to detect long presses.
3. Animate the size change when the box is long-pressed.

### Exercise 6️⃣: Gesture-Based Image Gallery

**🎯 Objective:** Create an image gallery that can be navigated using vertical swipe gestures.

**Instructions 📑:**

1. Create a `motion.div` for the gallery that contains the images.
2. Implement swipe gestures to navigate between images vertically (up and down).
3. Use `AnimatePresence` for smooth transitions between images.

</br>

<h1  align="center" > 🍄 𝐆𝖾𝗌𝗍υ𝗋𝖾𝗌 🥠</h1>

```TSX

//============ App.tsx ============== 

import SwipeableCard from "./components/1. SwipeableCard";
import DraggableBox from "./components/2. DraggableBox";
import RotateOnDrag from "./components/3. RotateOnDrag";
import TapToChangeColor from "./components/4. TapToChangeColor";
import LongPressToChangeSize from "./components/5. LongPressToChangeSize";
import GestureBasedImageGallery from "./components/6. GestureBasedImageGallery";

const App = () => {
  return (
    <section
      className="h-screen flex justify-center
     items-center bg-[#0d1017]"
    >
      {/* <SwipeableCard /> */}
      {/* <DraggableBox /> */}
      {/* <RotateOnDrag /> */}
      {/* <TapToChangeColor /> */}
      {/* <LongPressToChangeSize /> */}
      <GestureBasedImageGallery />
    </section>
  );
};

export default App;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 1️⃣: 𝐒ω𝗂ρ𝖾αᑲᥣ𝖾 𝐂α𝗋ᑯ 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/SwipeableCard.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const SwipeableCard = () => {
  const [isRemoved, setIsRemoved] = useState(false);

  const handleSwipe = (_: any, info: any) => {
    if (info.offset.x > 100) {
      setIsRemoved(true);
    } else if (info.offset.x < -100) {
      setIsRemoved(true);
    }
  };

  return (
    <motion.div
      drag="x"
      dragConstraints={{ left: -100, right: 100 }}
      onDragEnd={handleSwipe}
      className={`w-64 h-32 bg-blue-500 rounded-lg shadow-lg flex items-center justify-center text-white ${
        isRemoved ? "hidden" : ""
      }`}
    >
      Swipe me!
    </motion.div>
  );
};

export default SwipeableCard;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 2️⃣: 𝐃𝗋α𝗀𝗀αᑲᥣ𝖾 𝐁ⱺ𝗑 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/DraggableBox.tsx ============== 

import { motion } from "framer-motion";

const DraggableBox = () => {
  return (
    <motion.div
      drag
      dragConstraints={{ left: 0, right: 300, top: 0, bottom: 300 }}
      className="w-32 h-32 bg-green-500 rounded-lg shadow-lg"
    >
      Drag me!
    </motion.div>
  );
};

export default DraggableBox;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 3️⃣: 𝐑ⱺ𝗍α𝗍𝖾 ⱺ𐓣 𝐃𝗋α𝗀 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/RotateOnDrag.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const RotateOnDrag = () => {
  const [rotation, setRotation] = useState(0);

  const handleDrag = (_: any, info: any) => {
    const newRotation = rotation + info.offset.x;
    setRotation(newRotation);
  };

  return (
    <motion.div
      drag
      onDrag={handleDrag}
      style={{ rotate: rotation }}
      className="w-32 h-32 bg-red-500 rounded-lg flex items-center justify-center"
    >
      Drag me!
    </motion.div>
  );
};

export default RotateOnDrag;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 4️⃣: 𝐓αρ 𝗍ⱺ 𝐂ɦα𐓣𝗀𝖾 𝐂ⱺᥣⱺ𝗋 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/TapToChangeColor.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const colors = ["bg-blue-500", "bg-green-500", "bg-red-500", "bg-yellow-500"];

const TapToChangeColor = () => {
  const [colorIndex, setColorIndex] = useState(0);

  const handleTap = () => {
    setColorIndex((prev) => (prev + 1) % colors.length);
  };

  return (
    <motion.div
      onTap={handleTap}
      className={`w-32 h-32 ${colors[colorIndex]} rounded-lg flex items-center justify-center`}
    >
      Tap me!
    </motion.div>
  );
};

export default TapToChangeColor;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 5️⃣: 𝐋ⱺ𐓣𝗀 𝐏𝗋𝖾𝗌𝗌 𝗍ⱺ 𝐂ɦα𐓣𝗀𝖾 𝐒𝗂ƶ𝖾 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/LongPressToChangeSize.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const LongPressToChangeSize = () => {
  const [isLarge, setIsLarge] = useState(false);

  const handleLongPressStart = () => setIsLarge(true);
  const handleLongPressEnd = () => setIsLarge(false);

  return (
    <motion.div
      onTapStart={handleLongPressStart}
      onTapCancel={handleLongPressEnd}
      onTap={handleLongPressEnd}
      className={`w-32 h-32 bg-blue-500 rounded-lg
       flex items-center justify-center transition-all
        duration-300 cursor-pointer ${isLarge ? "w-48 h-48" : ""}`}
    >
      Long Press Me!
    </motion.div>
  );
};

export default LongPressToChangeSize;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 6️⃣: 𝐆𝖾𝗌𝗍υ𝗋𝖾-𝐁α𝗌𝖾ᑯ 𝚰ꭑα𝗀𝖾 𝐆αᥣᥣ𝖾𝗋𝗒 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ components/GestureBasedImageGallery.tsx ============== 

import { useState } from "react";
import { motion, AnimatePresence } from "framer-motion";

const images = [
  "https://images.unsplash.com/photo-1507936580189-3816b4abf640?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  "https://images.unsplash.com/photo-1528183429752-a97d0bf99b5a?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  "https://images.unsplash.com/photo-1448518340475-e3c680e9b4be?q=80&w=3200&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
];

const GestureBasedImageGallery = () => {
  const [currentIndex, setCurrentIndex] = useState(0);

  const handleSwipe = (_: any, info: any) => {
    if (info.offset.y > 100) {
      setCurrentIndex((prev) => (prev - 1 + images.length) % images.length);
    } else if (info.offset.y < -100) {
      setCurrentIndex((prev) => (prev + 1) % images.length);
    }
  };

  return (
    <div className="relative w-72 h-72 overflow-hidden">
      <AnimatePresence>
        <motion.img
          key={currentIndex}
          src={images[currentIndex]}
          alt={`Slide ${currentIndex}`}
          drag="y"
          dragConstraints={{ top: 0, bottom: 0 }}
          onDragEnd={handleSwipe}
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          exit={{ opacity: 0 }}
          className="w-full h-full rounded"
        />
      </AnimatePresence>
    </div>
  );
};

export default GestureBasedImageGallery;

```

</br>
