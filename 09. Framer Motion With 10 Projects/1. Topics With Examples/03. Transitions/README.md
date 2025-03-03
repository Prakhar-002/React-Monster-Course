
<h1  align="center" > 🍄 𝐓𝗋α𐓣𝗌𝗂𝗍𝗂ⱺ𐓣𝗌  🥠</h1>

Transitions are the effects that control how animations happen. Think of them as the "rules" for how an element moves or changes.

```TSX

import { motion } from "framer-motion";

// Duration  👉  How long the animation takes.
// Easing    👉  The speed curve of the animation.
// Delay     👉  How long to wait before starting the animation.

const Transitions = () => {
  return (
    <div>
      <motion.div
        className="box"
        initial={{ x: 0 }}
        animate={{ x: 100 }}
        // transition={{ delay: 2 }}
        // transition={{ duration: 2 }}
        // transition={{ duration: 2, ease: "easeIn" }}
        // transition={{ duration: 2, ease: "easeOut" }}
        // transition={{ duration: 2, ease: "easeInOut" }}
        transition={{ duration: 2, ease: "linear" }}
      />
    </div>
  );
};

export default Transitions;

```


```TSX

  <motion.div className="box" transition={{ duration: 2, ease: "linear" }} />

```

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/f8068dbd-3b89-480d-bdb2-a183188f3353" width="400px" height="331px"/>

</h1>
