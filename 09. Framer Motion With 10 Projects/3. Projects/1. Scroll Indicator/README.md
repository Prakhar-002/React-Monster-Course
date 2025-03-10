<h2  align="center" > 🕍 𝐒𝖼𝗋ⱺᥣᥣ 𝚰𐓣ᑯ𝗂𝖼α𝗍ⱺ𝗋  🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/4a3fe8c3-8527-42bb-85a3-2ea944171da4" width="400px" height="319px"/>

</h1>

```TSX

//============ App.tsx ============== 

import ScrollIndicator from "./components/ScrollIndicator";

const App = () => {
  return <ScrollIndicator />;
};

export default App;

```

```TSX

//============ components/ScrollIndicator.tsx ============== 

import { motion, useScroll, useTransform } from "framer-motion";

const ScrollIndicator = () => {
  const { scrollYProgress } = useScroll();

  const lineWidth = useTransform(scrollYProgress, [0, 1], ["0%", "100%"]);

  return (
    <div className="h-[200vh] p-[20px]">
      <motion.div
        className="fixed top-0 left-0 h-[5px] bg-red-500"
        style={{
          width: lineWidth,
          transition: "width 0.1s ease",
        }}
      />

      <div className="mt-[50px]">
        {[...Array(100)].map((_, i) => (
          <p key={i} className="mt-[20px]">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua.
          </p>
        ))}
      </div>
    </div>
  );
};

export default ScrollIndicator;

```
