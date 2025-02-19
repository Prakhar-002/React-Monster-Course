
<h1  align="center" > 🍄 υ𝗌𝖾𝚰ᑯ 🥠</h1>

```JSX

//============ App.jsx ============== 

import UniqueID from "./components/UniqueID";

const App = () => {
  return (
    <div>
      <UniqueID />
      <p>
        Lorem ipsum, dolor sit amet consectetur adipisicing elit. Fugit
        consequatur quos quidem cupiditate voluptatem aliquam consequuntur
        excepturi placeat, officia eos commodi et voluptatum beatae quis dicta
        repellat vero maiores nulla.
      </p>
      <UniqueID />
    </div>
  );
};
export default App;

```

```JSX

//============ components/UniqueID.jsx ============== 

import { useId, useState } from "react";

const UniqueID = () => {
  const id = useId();

  return (
    <div>
      <label htmlFor={`${id}-email`}>Email</label>
      <input type="email" id={`${id}-email`} />

      <br />
      <label htmlFor={`${id}-name`}>Name</label>
      <input type="text" id={`${id}-name`} />
    </div>
  );
};

export default UniqueID;

```
