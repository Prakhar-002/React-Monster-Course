
<h1  align="center" > 🍄 ωɦ𝗂ᥣ𝖾 𝚰𐓣 𝐕𝗂𝖾ω  🥠</h1>

### The whilelnView prop is used to trigger animations when an element comes into the viewport. It allows us to define how an element should animate while it is visible on the screen. It enables us to create engaging animations that activate when the user scrolls to a specific part of your webpage.

<h1  align="center" > 🍄 𝐕𝗂𝖾ωρⱺ𝗋𝗍 𝐏𝗋ⱺρ  🥠</h1>

### The viewport prop is used to customize how animations are triggered based on the visibility of an element in the viewport. It allows us to specify settings that affect when and how animations occur as elements scroll into or out of view.

<h2  align="center" >💡 𝐄𝗑αꭑρᥣ𝖾  1️⃣ </h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/4ff401a9-7c61-470d-ad97-b63b6a0dc3fd" width="400px" height="242px"/>

</h1>

```TSX

//============ App.tsx ============== 

import AnimatedCard from "./components/AnimatedGallery";

const App = () => {
  return (
    <div>
      <h1 className="text-center text-3xl mb-4">
        Scroll Down to See the Animation
      </h1>
      <div className="h-screen" />
      <AnimatedCard />
    </div>
  );
};
export default App;

```

```TSX

//============ components/AnimatedCard.tsx ============== 

import { motion } from "framer-motion";

const AnimatedCard = () => {
  return (
    <div className="flex justify-center items-start mt-[30rem]">
      <div className="h-[200vh] w-full flex justify-center items-center">
        <motion.div
          initial={{ scale: 0.5, opacity: 0 }}
          whileInView={{
            scale: 1.1,
            opacity: 1,
            y: -200,
          }}
          transition={{ duration: 0.5 }}
          className="bg-white rounded-lg p-6 shadow-lg text-center"
        >
          <h2 className="text-2xl font-bold mb-2 text-black">Amazing Card</h2>
          <p className="text-gray-600">
            This card animates beautifully into view!
          </p>
        </motion.div>
      </div>
    </div>
  );
};

export default AnimatedCard;

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

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/bc8f96a2-1258-4747-b142-acb62ed623e1" width="400px" height="534px"/>

</h1>

```TSX

//============ App.tsx ============== 

import AnimatedBoxes from "./components/AnimatedGallery";

const App = () => {
  return (
    <div className="mt-[170rem]">
      <AnimatedBoxes />
    </div>
  );
};

export default App;

```

```TSX

//============ components/AnimatedBoxes.tsx ============== 

import { motion } from "framer-motion";

const boxes = Array.from({ length: 6 }, (_, index) => index + 1);

const AnimatedBoxes = () => {
  return (
    <div className="flex flex-col items-center justify-center min-h-screen ">
      <h1 className="text-4xl font-bold mb-10">Scroll to Animate</h1>
      <div className="space-y-6">
        {boxes.map((box) => (
          <motion.div
            key={box}
            className="w-64 h-64 bg-blue-500 flex items-center justify-center text-white text-xl rounded-lg shadow-lg"
            initial={{ opacity: 0, scale: 0.5 }}
            whileInView={{ opacity: 1, scale: 1 }}
            viewport={{ once: false }}
            transition={{ duration: 0.5, ease: "easeInOut" }}
          >
            Box {box}
          </motion.div>
        ))}
      </div>
    </div>
  );
};

export default AnimatedBoxes;

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