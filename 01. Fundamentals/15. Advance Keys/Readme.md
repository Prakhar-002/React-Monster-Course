
<h1  align="center" > 🍄 𝐀ᑯ𝗏α𐓣𝖼𝖾 𝐊𝖾𝗒𝗌 🥠</h1>

``` JSX

//============ App.jsx ============== 

import Switcher from "./components/Switcher";

const App = () => {
  return (
    <div>
      <Switcher />
    </div>
  );
};
export default App;

```

```JSX

//============ Switcher.jsx ============== 

import { useState } from "react";

const Switcher = () => {
  const [sw, setSw] = useState(false);

  return (
    <div>
      {sw ? (
        <span className="bg-black text-white p-5 rounded m-2">Dark</span>
      ) : (
        <span className="bg-slate-300 text-black p-5 rounded m-2">Light</span>
      )}

      <br />
      <input
        type="text"
        className="border-4 rounded"
        key={sw ? "dark" : "light"}
      />
      <button onClick={() => setSw((s) => !s)}>Switch</button>
    </div>
  );
};

export default Switcher;

```
