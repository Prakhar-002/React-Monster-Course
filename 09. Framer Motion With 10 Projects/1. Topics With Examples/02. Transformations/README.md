
<h1  align="center" > 🍄 𝐓𝗋α𐓣𝗌𝖿ⱺ𝗋ꭑα𝗍𝗂ⱺ𐓣𝗌  🥠</h1>

## Transformations

Transformations allow you to change the shape, size, and position of elements on a webpage.

```TSX

import { motion } from "framer-motion";

const Transformations = () => {
  return (
    <div>
      {/* <motion.div className="box" animate={{ x: 100 }} /> */}
      {/* <motion.div className="box" animate={{ y: 100 }} /> */}

      {/* <motion.div className="box" animate={{ rotateX: 60 }} /> */}
      {/* <motion.div className="box" animate={{ rotateY: 60 }} /> */}
      {/* <motion.div className="box" animate={{ rotate: 20 }} /> */}

      {/* <motion.div className="box" animate={{ scaleX: 2 }} /> */}
      {/* <motion.div className="box" animate={{ scaleY: 2 }} /> */}
      {/* <motion.div className="box" animate={{ scale: 2 }} /> */}

      {/* <motion.div className="box" animate={{ skewX: 20 }} /> */}
      {/* <motion.div className="box" animate={{ skewY: 20 }} /> */}
      <motion.div className="box" animate={{ skew: 20 }} />
    </div>
  );
};

export default Transformations;

```

```TSX

  <motion.div className="box" animate={{ rotate: 20 }} />

```

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/8f98f402-2d99-42a7-9212-3982cdb0562a" width="400px" height="355px"/>

</h1>

```TSX

  <motion.div className="box" animate={{ scale: 2 }} />

```

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/20c9587a-ea4a-4fe0-93fa-6d8e1a952d4f" width="400px" height="365px"/>

</h1>

```TSX

  <motion.div className="box" animate={{ skew: 20 }} />

```

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/ab8d7c86-5133-4d47-83ec-2a11cd617d1f" width="400px" height="367px"/>

</h1>
