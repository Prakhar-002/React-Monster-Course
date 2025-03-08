<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

<!-- Convert all the code from useMotionValue practice to use the useSpring hook instead -->

</br>

<h1  align="center" > 🍄 𝐔𝗌𝖾 𝐒ρ𝗋𝗂𐓣𝗀 🥠</h1>

```TSX

//============ App.tsx ============== 
import DraggableBox from "./components/1. DraggableBox";
import HoverLinkedScale from "./components/2. HoverLinkedScale";
import SpringAnimatedPosition from "./components/3. SpringAnimatedPosition";
import DynamicRotation from "./components/4. DynamicRotation";

const App = () => {
  return (
    <section className="h-screen flex justify-center items-center bg-[#0d1017]">
      {/* <DraggableBox /> */}
      {/* <HoverLinkedScale /> */}
      {/* <SpringAnimatedPosition /> */}
      <DynamicRotation />
    </section>
  );
};

export default App;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 1️⃣: 𝐃𝗋α𝗀𝗀αᑲᥣ𝖾 𝐁ⱺ𝗑 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/627db90a-cd4d-49df-9bd7-c261e42cf298" width="300px" height="304px"/>

</h1>

```TSX

//============ components/DraggableBox.tsx ============== 

import { motion, useSpring } from "framer-motion";

const DraggableBox = () => {
  const x = useSpring(0);
  const y = useSpring(0);

  return (
    <div className="flex flex-col items-center">
      <motion.div
        drag
        dragConstraints={{ left: 0, right: 0, top: 0, bottom: 0 }}
        style={{ x, y }}
        className="w-32 h-32 bg-blue-500 rounded"
        onDrag={(_, info) => {
          x.set(info.offset.x);
          y.set(info.offset.y);
        }}
      />
      <p className="text-white">
        Position: ({x.get().toFixed(2)}, {y.get().toFixed(2)})
      </p>
    </div>
  );
};

export default DraggableBox;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 2️⃣: 𝐇ⱺ𝗏𝖾𝗋-𝐋𝗂𐓣𝗄𝖾ᑯ 𝐒𝖼αᥣ𝖾 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/36e27620-f985-49c4-bcbd-f1d95fcb858f" width="250px" height="200px"/>

</h1>

```TSX

//============ components/HoverLinkedScale.tsx ============== 

import { motion, useSpring } from "framer-motion";

const HoverLinkedScale = () => {
  const scale = useSpring(1);

  return (
    <motion.button
      onHoverStart={() => scale.set(1.2)}
      onHoverEnd={() => scale.set(1)}
      style={{ scale }}
      className="p-4 bg-blue-500 text-white rounded"
    >
      Hover Me
    </motion.button>
  );
};

export default HoverLinkedScale;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 3️⃣: 𝐒ρ𝗋𝗂𐓣𝗀-𝐀𐓣𝗂ꭑα𝗍𝖾ᑯ 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/931e20be-a35b-44e9-a82c-177a6d647f21" width="350px" height="329px"/>

</h1>

```TSX

//============ components/SpringAnimatedPosition.tsx ============== 

import { motion, useSpring } from "framer-motion";

const SpringAnimatedPosition = () => {
  const x = useSpring(0);
  const y = useSpring(0);

  const moveBox = () => {
    x.set(Math.random() * 300);
    y.set(Math.random() * 300);
  };

  return (
    <div className="relative">
      <motion.div
        style={{ x, y }}
        className="w-32 h-32 bg-blue-500 rounded"
        onClick={moveBox}
      >
        Click Me
      </motion.div>
    </div>
  );
};

export default SpringAnimatedPosition;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 4️⃣: 𝐃𝗒𐓣αꭑ𝗂𝖼 𝐑ⱺ𝗍α𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/c7dec515-5472-4d52-8383-e87819d81d77" width="250px" height="226px"/>

</h1>

```TSX

//============ components/DynamicRotation.tsx ============== 

import { motion, useSpring } from "framer-motion";

const DynamicRotation = () => {
  const rotation = useSpring(0);

  const rotateBox = () => {
    rotation.set(rotation.get() + 45);
  };

  return (
    <motion.div
      style={{ rotate: rotation }}
      className="w-32 h-32 bg-blue-500 rounded"
      onClick={rotateBox}
    >
      Click Me
    </motion.div>
  );
};

export default DynamicRotation;

```
