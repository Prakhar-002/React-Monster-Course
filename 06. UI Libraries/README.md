
<h1  align="center" > 🍄 𝐃α𝗌𝗂𝗒𝐔𝚰 🌼</h1>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/2518987c-05ea-4b7b-bacc-63e72597bff2"/>

</h1>

```TS

1. npm i -D daisyui@latest

2. https://tailwindcss.com/docs/guides/vite

3. tailwind.config 👇

import daisyui from "daisyui"

module.exports = {
  //...
  plugins: [
    daisyui,
  ],
}

```

</br>

<h1  align="center" > 🍄 𝐑αᑯ𝗂𝗑 🌼</h1>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/78bfde56-2c55-4b13-8ceb-3bb823efe756"/>

</h1>

```bash

https://www.radix-ui.com/themes/docs/overview/getting-started

```


```TSX

//============ Main.tsx ============== 

import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import App from "./App.jsx";
import "@radix-ui/themes/styles.css";
import { Theme } from "@radix-ui/themes";

createRoot(document.getElementById("root")).render(
  <StrictMode>
    <Theme accentColor="yellow">
      <App />
    </Theme>
  </StrictMode>
);

```

```TSX

//============ App.tsx ============== 

import { Flex, Text, Button } from "@radix-ui/themes";

function App() {
  return (
    <Flex direction="column" gap="2">
      <Text>Hello from Radix Themes :)</Text>
      <Button>Let's go</Button>
    </Flex>
  );
}

export default App;

```

</br>

<h1  align="center" > 🍄 𝐒ɦαᑯ𝖼𐓣 𝐔𝚰 🌼</h1>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/ef3ba710-6471-4ee6-9cb6-dce0a6257c8b"/>

</h1>

</br>

      https://ui.shadcn.com/docs/installation/vite
