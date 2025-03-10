<h2  align="center" > 🕍 𝐃𝗋α𝗀𝗀αᑲᥣ𝖾 𝐂α𝗋ᑯ𝗌 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/31ef2f50-91ba-46ed-810e-ebc526e7cba5" width="600px" height="684px"/>

</h1>

```TSX

//============ App.tsx ============== 

import DraggableCard from "./components/DraggableCard";

const App = () => {
  return (
    <div>
      <div className="flex justify-center items-center h-[100vh] bg-[#f3f3f3]">
        <DraggableCard
          style={{
            background: "linear-gradient(135deg, #f093fb 0%, #f5576c 100%)",
          }}
        >
          Card 1
        </DraggableCard>
        <DraggableCard
          style={{
            background: "linear-gradient(135deg, #5ee7df 0%, #b490ca 100%)",
          }}
        >
          Card 2
        </DraggableCard>
        <DraggableCard
          style={{
            background: "linear-gradient(135deg, #ff9a9e 0%, #fecfef 99%)",
          }}
        >
          Card 3
        </DraggableCard>
      </div>
    </div>
  );
};

export default App;

```

```TSX

//============ components/DraggableCard.tsx ============== 

import { motion } from "framer-motion";
import { CSSProperties, ReactNode } from "react";

interface DraggableCardProps {
  children: ReactNode;
  style?: CSSProperties;
}

const DraggableCard = ({ children, style }: DraggableCardProps) => {
  return (
    <motion.div
      drag
      dragConstraints={{ left: -200, right: 200, top: -200, bottom: 200 }}
      whileHover={{ scale: 1.1 }}
      whileTap={{ scale: 0.9 }}
      className="rounded-2xl shadow-lg p-5 m-2 w-52 h-72
       flex items-center justify-center text-white text-xl"
      style={style}
    >
      {children}
    </motion.div>
  );
};

export default DraggableCard;

```
