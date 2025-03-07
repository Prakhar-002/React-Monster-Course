<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Exercise 1️⃣: Simple Fade In/Out Animation

**🎯 Objective:** Create a component that fades in when it mounts and fades out when it unmounts.

**Instructions 📑:**

1. Create a component called `FadeComponent`.
2. Use `motion.div` from Framer Motion to create a div that fades in and out.
3. Use Tailwind CSS to style the div (e.g., padding, background color).
4. Add a button to toggle the visibility of `FadeComponent`.

### Exercise 2️⃣: Slide In from the Left

**🎯 Objective:** Create a sidebar that slides in from the left when a button is clicked.

**Instructions 📑:**

1. Create a sidebar component using `motion.div`.
2. Style the sidebar using Tailwind CSS (e.g., width, background color).
3. Use Framer Motion's `animate` prop to slide the sidebar in from the left.
4. Add a button to toggle the sidebar's visibility.

### Exercise 3️⃣: Modal with Transition

**🎯 Objective:** Create a modal that opens with a slide-down effect.

**Instructions 📑:**

1. Create a modal component using `motion.div`.
2. Style the modal using Tailwind CSS (e.g., background, border).
3. Use Framer Motion to animate the modal’s entrance and exit.
4. Add a button to trigger the modal.

### Exercise 4️⃣: Responsive Animations

**🎯 Objective:** Make a responsive button that animates on click.

**Instructions 📑:**

1. Create a button using `motion.button`.
2. Style the button using Tailwind CSS for different screen sizes.
3. Use Framer Motion’s `whileTap` to animate the button on click (e.g., scale down).
4. Add a hover effect using `whileHover`.

### Exercise 5️⃣: Accordion Component

**🎯 Objective:** Create an accordion component that expands and collapses on click.

**Instructions 📑:**

1. Create a component that renders a list of items, each with a title and content.
2. Use `motion.div` to animate the height of the content.
3. Style the titles and content with Tailwind CSS.

### Exercise 6️⃣: Notification Toast

**🎯 Objective:** Create a notification toast that slides in from the top when triggered.

**Instructions 📑:**

1. Create a toast notification component using `motion.div`.
2. Style the toast using Tailwind CSS.
3. Use state to control the visibility and animate its entrance and exit.

</br>

<h1  align="center" > 🍄 𝐓𝗋α𐓣𝗌𝗂𝗍𝗂ⱺ𐓣𝗌 🥠</h1>

```TSX

//============ App.tsx ============== 

import FadeComponent from "./components/1. FadeComponent";
import Sidebar from "./components/2. Sidebar";
import Modal from "./components/3. Modal";
import ResponsiveButton from "./components/4. ResponsiveButton";
import Accordion from "./components/5. Accordion";
import ToastNotification from "./components/6. ToastNotification";

const App = () => {
  return (
    <section className="h-screen flex justify-center items-center bg-[#0d1017]">
      {/* <FadeComponent /> */}
      {/* <Sidebar /> */}
      {/* <Modal /> */}
      {/* <ResponsiveButton /> */}
      {/* <Accordion /> */}
      <ToastNotification />
    </section>
  );
};

export default App;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 1️⃣: 𝐒𝗂ꭑρᥣ𝖾 𝐅αᑯ𝖾 𝚰𐓣/𝐎υ𝗍 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/5deab9a7-d5d6-417e-9547-e317879a7f20" width="250px" height="157px"/>

</h1>

```TSX

//============ components/FadeComponent.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const FadeComponent = () => {
  const [visible, setVisible] = useState(false);

  return (
    <div className="flex flex-col items-center">
      <button
        className="mb-4 p-2 bg-blue-500 text-white rounded"
        onClick={() => setVisible(!visible)}
      >
        Toggle Fade
      </button>
      {visible && (
        <motion.div
          className="p-4 bg-teal-400 text-black rounded"
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          exit={{ opacity: 0 }}
          transition={{ duration: 0.5 }}
        >
          Hello, I'm a Fading component!🥲
        </motion.div>
      )}
    </div>
  );
};

export default FadeComponent;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 2️⃣: 𝐒ᥣ𝗂ᑯ𝖾 𝚰𐓣 𝖿𝗋ⱺꭑ 𝗍ɦ𝖾 𝐋𝖾𝖿𝗍 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/9f9a8e90-d422-4ce3-8367-efbaa12587b7" width="400px" height="389px"/>

</h1>

```TSX

//============ components/Sidebar.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const Sidebar = () => {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <div className="flex">
      <button
        className="mb-4 p-2 bg-blue-500 text-white rounded"
        onClick={() => setIsOpen(!isOpen)}
      >
        Toggle Sidebar
      </button>
      <motion.div
        className={`fixed left-0 top-0 h-full bg-gray-700
         text-white p-4 ${isOpen ? "" : "-translate-x-full"}`}
        initial={{ x: "-100%" }}
        animate={{ x: isOpen ? "0%" : "-100%" }}
        transition={{ duration: 0.5 }}
      >
        <h2 className="text-lg font-bold">Sidebar</h2>
        <p>Content goes here!</p>
      </motion.div>
    </div>
  );
};

export default Sidebar;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 3️⃣: 𝐌ⱺᑯαᥣ ω𝗂𝗍ɦ 𝐓𝗋α𐓣𝗌𝗂𝗍𝗂ⱺ𐓣 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/38df15e4-a54d-40ce-8533-52a80de9e130" width="400px" height="394px"/>

</h1>

```TSX

//============ components/Modal.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const Modal = () => {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <div className="flex flex-col items-center">
      <button
        className="mb-4 p-2 bg-blue-500 text-white rounded"
        onClick={() => setIsOpen(true)}
      >
        Open Modal
      </button>
      {isOpen && (
        <motion.div
          className="fixed inset-0 bg-black bg-opacity-50 flex justify-center items-center"
          onClick={() => setIsOpen(false)}
        >
          <motion.div
            className="bg-white p-4 rounded"
            onClick={(e) => e.stopPropagation()}
            initial={{ y: "-100vh" }}
            animate={{ y: "0vh" }}
            exit={{ y: "100vh" }}
            transition={{ duration: 0.5 }}
          >
            <h2 className="text-lg font-bold">Modal Title</h2>
            <p>This is a modal window!</p>
            <button
              className="mt-4 p-2 bg-red-500 text-white rounded"
              onClick={() => setIsOpen(false)}
            >
              Close
            </button>
          </motion.div>
        </motion.div>
      )}
    </div>
  );
};

export default Modal;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 4️⃣: 𝐑𝖾𝗌ρⱺ𐓣𝗌𝗂𝗏𝖾 𝐀𐓣𝗂ꭑα𝗍𝗂ⱺ𐓣𝗌 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/ce5af972-5044-4a12-b995-48bda8657eac" width="200px" height="118px"/>

</h1>

```TSX

//============ components/ResponsiveButton.tsx ============== 

import { motion } from "framer-motion";

const ResponsiveButton = () => {
  return (
    <motion.button
      className="p-2 bg-blue-500 text-white rounded transition-transform duration-300 ease-in-out"
      whileHover={{ scale: 1.1 }}
      whileTap={{ scale: 0.9 }}
    >
      Click Me!
    </motion.button>
  );
};

export default ResponsiveButton;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 5️⃣: 𝐀𝖼𝖼ⱺ𝗋ᑯ𝗂ⱺ𐓣 𝐂ⱺꭑρⱺ𐓣𝖾𐓣𝗍 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/c151ec2e-7464-4d4f-b695-d6ffa297f2af" width="350px" height="297px"/>

</h1>

```TSX

//============ components/Accordion.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const items = [
  { title: "Item 1", content: "This is the content of item 1." },
  { title: "Item 2", content: "This is the content of item 2." },
  { title: "Item 3", content: "This is the content of item 3." },
];

const Accordion = () => {
  const [openIndex, setOpenIndex] = useState(null);

  const toggleItem = (index: any) => {
    setOpenIndex(openIndex === index ? null : index);
  };

  return (
    <div className="space-y-2">
      {items.map((item, index) => (
        <div key={index}>
          <button
            className="w-full text-left p-2 bg-gray-300 rounded focus:outline-none"
            onClick={() => toggleItem(index)}
          >
            {item.title}
          </button>
          <motion.div
            className="overflow-hidden"
            initial={{ height: 0 }}
            animate={{ height: openIndex === index ? "auto" : 0 }}
            transition={{ duration: 0.3 }}
          >
            <div className="p-2 bg-gray-200 rounded">{item.content}</div>
          </motion.div>
        </div>
      ))}
    </div>
  );
};

export default Accordion;

```

</br>

<h2  align="center" > 🕍 𝐄𝗑𝖾𝗋𝖼𝗂𝗌𝖾 6️⃣: 𝐍ⱺ𝗍𝗂𝖿𝗂𝖼α𝗍𝗂ⱺ𐓣 𝐓ⱺα𝗌𝗍 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/62dd9ae3-5006-4fa5-bd66-6dba23f87c9d" width="400px" height="392px"/>

</h1>

```TSX

//============ components/ToastNotification.tsx ============== 

import { useState } from "react";
import { motion } from "framer-motion";

const ToastNotification = () => {
  const [visible, setVisible] = useState(false);

  const showToast = () => {
    setVisible(true);
    setTimeout(() => setVisible(false), 3000);
  };

  return (
    <div className="flex flex-col items-center">
      <button
        className="mb-4 p-2 bg-blue-500 text-white rounded"
        onClick={showToast}
      >
        Show Notification
      </button>
      {visible && (
        <motion.div
          className="fixed top-4 right-4 p-4 bg-green-500 text-white rounded"
          initial={{ opacity: 0, translateY: -20 }}
          animate={{ opacity: 1, translateY: 0 }}
          exit={{ opacity: 0, translateY: -20 }}
          transition={{ duration: 0.5 }}
        >
          Notification: Action Successful!
        </motion.div>
      )}
    </div>
  );
};

export default ToastNotification;

```
