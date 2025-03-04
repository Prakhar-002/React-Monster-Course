
<h1  align="center" > 🍄 𝐆𝖾𝗌𝗍υ𝗋𝖾𝗌  🥠</h1>

### Gestures allow us to add interactive animations based on user actions like `dragging`, `hovering`, or `tapping`. It makes our components respond to how users interact with them.

<h2  align="center" > 🕍  𝐖ɦ𝗂ᥣ𝖾 𝐇ⱺ𝗏𝖾𝗋  🏄‍♀️</h2>

```TSX

<motion.div
    whileHover={{ scale: 1.2, rotate: 10 }}
    transition={{ type: "spring", stiffness: 300 }}
    className="box"
/> 

```

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/a66b6e45-19a7-44fc-8c04-7d90b800fc4b" width="400px" height="338px"/>

</h1>

<h2  align="center" > 🕍 𝐖ɦ𝗂ᥣ𝖾 𝐓αρ 🏄‍♀️</h2>

```TSX

<motion.div
    whileTap={{ scale: 0.8, backgroundColor: "orange" }}
    transition={{ type: "spring", stiffness: 300 }}
    className="box"
/>

```

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/18210361-b957-4147-8e1b-2e0f56bc886d" width="400px" height="336px"/>

</h1>

<h2  align="center" > 🕍 𝐖ɦ𝗂ᥣ𝖾 𝐃𝗋α𝗀  🏄‍♀️</h2>

```TSX

<motion.div
    drag
    whileDrag={{ scale: 1.1, backgroundColor: "orange" }}
    transition={{ type: "spring", stiffness: 300 }}
    className="box"
/>

```

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/bf28da70-b758-4915-85cd-be233e697c0f" width="400px" height="391px"/>

</h1>

```TSX

import { motion } from "framer-motion";

const Gestures = () => {
  return (
    <div>
      {/* whileHover */}
      {/* <motion.div
      whileHover={{ scale: 1.2, rotate: 10 }}
      transition={{ type: "spring", stiffness: 300 }}
      className="box"
    /> */}
      {/* ------------------- */}

      {/* ------------------- */}
      {/* whileTap */}
      {/* <motion.div
      whileTap={{ scale: 0.8, backgroundColor: "orange" }}
      transition={{ type: "spring", stiffness: 300 }}
      className="box"
    /> */}

      {/* ------------------- */}
      {/* whileDrag */}
      {/* <motion.div
        drag
        whileDrag={{ scale: 1.1, backgroundColor: "orange" }}
        transition={{ type: "spring", stiffness: 300 }}
        className="box"
      /> */}

      {/* ------------------- */}
      {/* whileDrag Constraints */}
      <motion.div
        drag
        dragConstraints={{
          top: -50,
          left: -50,
          right: 50,
          bottom: 50,
        }}
        transition={{ type: "spring", stiffness: 300 }}
        style={{ width: 100, height: 100, backgroundColor: "purple" }}
      />
    </div>
  );
};

export default Gestures;

```

<h1  align="center" >💡 𝐄𝗑αꭑρᥣ𝖾  1️⃣ </h1>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ App.tsx ============== 

import AnimatedCard from "./components/AnimatedCard";

const App = () => {
  return (
    <div className="min-h-screen bg-gray-100 flex items-center justify-center">
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
    <motion.div
      className="max-w-sm mx-auto bg-white rounded-lg shadow-lg overflow-hidden cursor-pointer"
      initial={{ scale: 1, rotate: 0 }}
      whileHover={{ scale: 1.05, rotate: 3 }}
      whileTap={{ scale: 0.95 }}
      drag
      dragConstraints={{ left: -50, right: 50, top: -50, bottom: 50 }}
      dragElastic={0.2}
      transition={{ type: "spring", stiffness: 300 }}
    >
      <img
        className="w-full h-48 object-cover"
        src="https://images.unsplash.com/photo-1728408828574-70a460530093?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
        alt="Card Image"
      />
      <div className="p-6">
        <h2 className="text-xl font-semibold mb-2">Dynamic Card Title</h2>
        <p className="text-gray-700 mb-4">
          This is a simple card with Framer Motion animations and Tailwind CSS
          styling.
        </p>
        <button className="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600 transition">
          Learn More
        </button>
      </div>
    </motion.div>
  );
};

export default AnimatedCard;

```

</br>

<h1  align="center" > 💡 𝐄𝗑αꭑρᥣ𝖾 2️⃣ </h1>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ App.tsx ============== 

import ImageGallery from "./components/ImageGallery";

const App = () => {
  return (
    <div className="min-h-screen bg-gray-100 flex items-center justify-center">
      <ImageGallery />
    </div>
  );
};

export default App;

```

```TSX

//============ components/ImageGallery.tsx ============== 

import { motion } from "framer-motion";

const images = [
  {
    src: "https://images.unsplash.com/photo-1446034295857-c39f8844fad4?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    caption: "Caption for Image 1",
  },
  {
    src: "https://images.unsplash.com/photo-1519681393784-d120267933ba?q=80&w=3870&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    caption: "Caption for Image 2",
  },
  {
    src: "https://images.unsplash.com/photo-1559666126-84f389727b9a?q=80&w=3877&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    caption: "Caption for Image 3",
  },
];

const ImageGallery = () => {
  return (
    <div className="w-[80%] flex">
      {images.map((image, index) => (
        <motion.div
          key={index}
          className="relative m-[1rem] overflow-hidden rounded-lg shadow-lg"
          whileHover={{ scale: 1.05 }}
        >
          <img src={image.src} alt={image.caption} className="w-full h-auto" />
          <motion.div
            className="absolute inset-0 flex items-center justify-center bg-black bg-opacity-50 text-white opacity-0 hover:opacity-100 transition-opacity duration-300 cursor-pointer"
            whileHover={{ opacity: 1 }}
          >
            <p className="text-lg">{image.caption}</p>
          </motion.div>
        </motion.div>
      ))}
    </div>
  );
};

export default ImageGallery;

```
