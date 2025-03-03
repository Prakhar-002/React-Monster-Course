
<h1  align="center" > 🍄 𝐒𝗍α𝗀𝗀𝖾𝗋 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣  🥠</h1>

<h2  align="center" >💡 𝐄𝗑αꭑρᥣ𝖾  1️⃣ </h2>

```TSX

//============ App.tsx ============== 

import StaggerAnimation from "./components/Stagger";

const App = () => {
  return (
    <div>
      <StaggerAnimation />
    </div>
  );
};
export default App;

```

```TSX

//============ components/StaggerAnimation.tsx ============== 

import { motion } from "framer-motion";

const parentVariants = {
  hidden: { opacity: 0 },
  visible: {
    opacity: 1,
    transition: {
      staggerChildren: 0.8,
    },
  },
};

const childVariants = {
  hidden: { opacity: 0, y: 20 },
  visible: { opacity: 1, y: 0 },
};

const StaggerAnimation = () => {
  return (
    <motion.div variants={parentVariants} initial="hidden" animate="visible">
      {[...Array(5)].map((_, index) => (
        <motion.div
          className="box mt-[2rem]"
          key={index}
          variants={childVariants}
        />
      ))}
    </motion.div>
  );
};

export default StaggerAnimation;

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

<h2  align="center" > 💡 𝐄𝗑αꭑρᥣ𝖾 2️⃣ </h2>

```TSX

//============ App.tsx ============== 

import AnimatedGallery from "./components/AnimatedGallery";

const App = () => {
  return (
    <div>
      <AnimatedGallery />
    </div>
  );
};
export default App;

```

```TSX

//============ components/AnimatedGallery.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const galleryImages = [
  "https://images.unsplash.com/photo-1523712999610-f77fbcfc3843?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  "https://images.unsplash.com/photo-1506744038136-46273834b3fb?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  "https://images.unsplash.com/photo-1426604966848-d7adac402bff?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  "https://images.unsplash.com/photo-1490682143684-14369e18dce8?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  "https://images.unsplash.com/photo-1445964047600-cdbdb873673d?q=80&w=3784&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
];

const parentVariants = {
  hidden: { opacity: 0 },
  visible: {
    opacity: 1,
    transition: {
      staggerChildren: 0.5,
      staggerDirection: 1,
    },
  },
};

const childVariants = {
  hidden: { opacity: 0, y: 20 },
  visible: { opacity: 1, y: 0 },
};

const AnimatedGallery = () => {
  const [showImages, setShowImages] = useState(false);

  const handleClick = () => {
    setShowImages((prev) => !prev);
  };

  return (
    <div>
      <button
        onClick={handleClick}
        className="mb-[2rem] p-4 rounded-lg bg-yellow-300 text-black font-bold"
      >
        {showImages ? "Hide Images" : "Show Images"}
      </button>

      <motion.div
        variants={parentVariants}
        initial="hidden"
        animate={showImages ? "visible" : "hidden"}
        className="flex"
      >
        {galleryImages.map((image, index) => (
          <motion.img
            key={index}
            src={image}
            alt={`Gallery Image ${index + 1}`}
            variants={childVariants}
            className="ml-[2rem] w-[300px] rounded"
          />
        ))}
      </motion.div>
    </div>
  );
};

export default AnimatedGallery;

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