<h2  align="center" > 🕍 𝐋ⱺαᑯ𝖾𝗋 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ App.tsx ============== 

import Loader from "./components/Loader";

function App() {
  return (
    <div>
      <Loader />
    </div>
  );
}

export default App;

```

```TSX

//============ components/Loader.tsx ============== 

import { motion } from "framer-motion";

const Loader = () => {
  return (
    <div className="flex  items-center justify-center h-screen">
      <motion.div
        className="relative w-16 h-16 border-4 border-t-4 border-blue-500 border-solid rounded-full"
        animate={{ rotate: 360 }}
        transition={{ duration: 1, repeat: Infinity, ease: "linear" }}
      >
        <motion.div
          className="absolute inset-0 border-4 border-blue-300 border-solid rounded-full"
          style={{ borderTopColor: "transparent" }}
          animate={{ opacity: [1, 0.5, 1] }}
          transition={{ duration: 1, repeat: Infinity, ease: "easeInOut" }}
        />
      </motion.div>
    </div>
  );
};

export default Loader;

```
