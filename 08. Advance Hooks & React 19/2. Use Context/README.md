
<h1  align="center" > 🍄 𝐔𝗌𝖾 𝐂ⱺ𐓣𝗍𝖾𝗑𝗍 🥠</h1>

<h2  align="center" > 🍄 1. 𝐖𝗂𝗍ɦⱺυ𝗍 𝐔𝗌𝖾 🥠</h2>

```TSX

//============ App.tsx ============== 

import Theme from "./components/Theme";

const App = () => {
  return (
    <div className="flex justify-center items-center w-full mt-[10rem]">
      <Theme />
    </div>
  );
};

export default App;

```

```TSX

//============ components/Theme.tsx ============== 

import { createContext, useState } from "react";
import Card from "./Card";

export const ThemeContext = createContext();

const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState("light");

  const toggleTheme = () => {
    setTheme(theme === "light" ? "dark" : "light");
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};

const Theme = () => {
  return (
    <ThemeProvider>
      <Card />
    </ThemeProvider>
  );
};

export default Theme;

```

```TSX

//============ components/Card.tsx ============== 

import { useContext } from "react";
import { ThemeContext } from "./Theme";

const Card = () => {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <div
      className={`w-[20rem] p-[2rem] ${
        theme === "light" ? "bg-white" : "bg-teal-900"
      }`}
    >
      <h1
        className={`text-teal-300 ${
          theme === "light" ? "text-black" : "text-white"
        }`}
      >
        Theme Card
      </h1>

      <p className={`${theme === "light" ? "text-black" : "text-white"}`}>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Facilis,
        cumque. Numquam exercitationem quae vitae vel veritatis similique illum
        repellat, itaque iure voluptates ut cum, facere a praesentium. Eveniet,
        ut itaque.
      </p>

      <button
        className="bg-teal-300 p-2 rounded-full text-white mt-[2rem]"
        onClick={toggleTheme}
      >
        {theme === "light" ? "Switch to Dark Mode" : "Switch to Light Mode"}
      </button>
    </div>
  );
};

export default Card;

```

</br>

<h2  align="center" > 🍄 2. 𝐖𝗂𝗍ɦ 𝐔𝗌𝖾 🥠</h2>

```TSX

//============ App.tsx ============== 

import Theme from "./components/Theme";

const App = () => {
  return (
    <div className="flex justify-center items-center w-full mt-[10rem]">
      <Theme />
    </div>
  );
};

export default App;

```

```TSX

//============ components/Theme.tsx ============== 

import { createContext, useState } from "react";
import Card from "./Card";

export const ThemeContext = createContext();

const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState("light");

  const toggleTheme = () => {
    setTheme(theme === "light" ? "dark" : "light");
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};

const Theme = () => {
  return (
    <ThemeProvider>
      <Card />
    </ThemeProvider>
  );
};

export default Theme;

```

```TSX

//============ components/Card.tsx ============== 

import { use } from "react";
import { ThemeContext } from "./Theme";

const Card = () => {
  // Now by using react 19, we don't have to use "useContext" we can replace that with "use"
  const { theme, toggleTheme } = use(ThemeContext);

  return (
    <div
      className={`w-[20rem] p-[2rem] ${
        theme === "light" ? "bg-white" : "bg-teal-900"
      }`}
    >
      <h1
        className={`text-teal-300 ${
          theme === "light" ? "text-black" : "text-white"
        }`}
      >
        Theme Card
      </h1>

      <p className={`${theme === "light" ? "text-black" : "text-white"}`}>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Facilis,
        cumque. Numquam exercitationem quae vitae vel veritatis similique illum
        repellat, itaque iure voluptates ut cum, facere a praesentium. Eveniet,
        ut itaque.
      </p>

      <button
        className="bg-teal-300 p-2 rounded-full text-white mt-[2rem]"
        onClick={toggleTheme}
      >
        {theme === "light" ? "Switch to Dark Mode" : "Switch to Light Mode"}
      </button>
    </div>
  );
};

export default Card;

```
