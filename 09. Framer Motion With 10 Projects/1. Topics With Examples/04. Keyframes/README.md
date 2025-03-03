
<h1  align="center" > 🍄 𝐊𝖾𝗒𝖿𝗋αꭑ𝖾𝗌  🥠</h1>

```TSX

import { motion } from "framer-motion";

const Keyframes = () => {
  return (
    <div>
      <motion.div
        animate={{
          scale: [1, 2, 2, 3, 4, 3, 2, 1],
          rotate: [0, 0, 270, 270, 0],
          borderRadius: ["20%", "20%", "50%", "50%", "20%"],
        }}
        transition={{ duration: 5 }}
        className="box"
      />
    </div>
  );
};
export default Keyframes;

```

<h1  align="center" >💡 𝐄𝗑αꭑρᥣ𝖾  1️⃣ </h1>

```TSX

//============ App.tsx ============== 

import PulsingButton from "./components/PulsingButton";

const App = () => {
  return (
    <div className="min-h-screen flex items-center justify-center bg-gray-100">
      <PulsingButton />
    </div>
  );
};

export default App;

```

```TSX

//============ components/PulsingButton.tsx ============== 

import { motion } from "framer-motion";

const PulsingButton = () => {
  return (
    <motion.button
      className="px-4 py-2 text-white bg-blue-500 rounded outline-none"
      animate={{
        scale: [1, 1.1, 1],
        backgroundColor: ["#3b82f6", "#60a5fa", "#3b82f6"],
      }}
      transition={{
        duration: 0.8,
        ease: "easeInOut",
        repeat: Infinity,
      }}
    >
      Click Me!
    </motion.button>
  );
};

export default PulsingButton;

```

```css

/* ============== CSS ==============  */

@tailwind base;
@tailwind components;
@tailwind utilities;

```

</br>

<h1  align="center" > 💡 𝐄𝗑αꭑρᥣ𝖾 2️⃣ </h1>

```TSX

//============ App.tsx ============== 

import BouncingLoader from "./components/LoadingSpinner";

const App = () => {
  return (
    <div className="min-h-screen flex items-center justify-center bg-[#0d1017]">
      <BouncingLoader />
    </div>
  );
};

export default App;

```

```TSX

//============ components/PulsingButton.tsx ============== 

import { motion } from "framer-motion";

const BouncingLoader = () => {
  return (
    <div className="flex justify-center items-center space-x-2">
      {[...Array(3)].map((_, index) => (
        <motion.div
          key={index}
          className="w-4 h-4 bg-teal-500 rounded-full"
          animate={{
            y: [0, -15, 0],
          }}
          transition={{
            duration: 0.6,
            ease: "easeInOut",
            repeat: Infinity,
            repeatDelay: index * 0.2,
          }}
        />
      ))}
    </div>
  );
};

export default BouncingLoader;

```

```css

/* ============== CSS ==============  */

@tailwind base;
@tailwind components;
@tailwind utilities;

```