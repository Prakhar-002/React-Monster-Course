<h2  align="center" > 🕍 𝐇ⱺ𝗋𝗂ƶⱺ𐓣𝗍αᥣ 𝐒𝖼𝗋ⱺᥣᥣ 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ App.tsx ============== 

import ScrollCarousel from "./components/ScrollCarousel";

const App = () => {
  return <ScrollCarousel />;
};

export default App;

```

```TSX

//============ components/ScrollCarousel.tsx ============== 

import { motion, useScroll, useTransform } from "framer-motion";
import { useRef } from "react";
import Card from "./Card";
import { cards } from "../utils/data";

const ScrollCarousel = () => {
  const targetRef = useRef(null);

  const { scrollYProgress } = useScroll({
    target: targetRef,
  });

  const x = useTransform(scrollYProgress, [0, 1], ["1%", "-95%"]);

  return (
    <section ref={targetRef} className="relative h-[300vh] bg-neutral-900">
      <div className="sticky top-0 flex h-screen items-center overflow-hidden">
        <motion.div style={{ x }} className="flex gap-4">
          {cards.map((card) => (
            <Card card={card} />
          ))}
        </motion.div>
      </div>
    </section>
  );
};

export default ScrollCarousel;

```

```TSX

//============ components/Card.tsx ============== 

const Card = ({ card }: any) => {
  return (
    <div
      key={card.id}
      className="group relative w-[10rem] h-[10rem] overflow-hidden bg-neutral-200"
    >
      <div
        style={{
          backgroundImage: `url(${card.url})`,
          backgroundSize: "cover",
          backgroundPosition: "center",
        }}
        className="absolute inset-0 z-0 transition-transform duration-300 group-hover:scale-110"
      ></div>
    </div>
  );
};

export default Card;

```

```TS

//============ utils/data.ts ============== 

export const cards = [
  {
    url: "https://images.unsplash.com/photo-1458668383970-8ddd3927deed?q=80&w=3867&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    url: "https://images.unsplash.com/photo-1506744038136-46273834b3fb?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    url: "https://images.unsplash.com/photo-1500673922987-e212871fec22?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    url: "https://images.unsplash.com/photo-1445964047600-cdbdb873673d?q=80&w=3784&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    url: "https://images.unsplash.com/photo-1482784160316-6eb046863ece?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    url: "https://images.unsplash.com/photo-1493246507139-91e8fad9978e?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    url: "https://images.unsplash.com/photo-1473448912268-2022ce9509d8?q=80&w=3841&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
];

```
