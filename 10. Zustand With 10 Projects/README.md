
<h1  align="center" > 🍄 𝐙υ𝗌𝗍α𐓣ᑯ 🥠</h1>

<h3  align="center" > 

<img src="https://github.com/user-attachments/assets/3be11d48-0c79-48d1-9a76-24b1eaf01fcb" width="250px" height="250px"/>

</br>
</br>

Zustand is a lightweight state management library for React
applications. It helps you manage and share state across
different parts of your app without needing to pass props
through many layers or use complex solutions.

</h3>

```TSX

//============ Main.tsx ============== 

import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import App from "./App.tsx";

createRoot(document.getElementById("root")!).render(
  <StrictMode>
    <App />
  </StrictMode>
);

```

```TS

//============ store.ts ============== 

import { create } from "zustand";

type CounterStore = {
  count: number;
  increment: () => void;
  decrement: () => void;
};

export const useCounterStore = create<CounterStore>((set) => ({
  count: 0,
  increment: () => {
    set((state) => ({ count: state.count + 1 }));
  },

  decrement: () => {
    set((state) => ({ count: state.count - 1 }));
  },
}));

```

```TSX

//============ App.tsx ============== 

import OtherComponent from "./OtherComponent";
import { useCounterStore } from "./store";

const App = () => {
  const count = useCounterStore((state) => state.count);

  return (
    <div>
      <h1>Count: {count}</h1>
      <OtherComponent />
    </div>
  );
};

export default App;

```

```TSX

//============ OtherComponent.tsx ============== 

import { useCounterStore } from "./store";

const OtherComponent = () => {
  const increment = useCounterStore((state) => state.increment);
  const decrement = useCounterStore((state) => state.decrement);

  return (
    <div>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
};

export default OtherComponent;

```