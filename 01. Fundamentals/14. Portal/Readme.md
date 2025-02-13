
<h3  align="center" >𝐏ⱺ𝗋𝗍αᥣ</h3>

``` JSX

import CopyInput from "./components/CopyInput";

const App = () => {
  return (
    <div>
      <CopyInput />
    </div>
  );
};
export default App;

```

```HTML

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite + React + TS</title>
  </head>
  <body>
    <div id="root"></div>
    <div id="portal-popup"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>

```

```JSX

import { useState } from "react";
import PopupContent from "./PopupContent";

const CopyInput = () => {
  const [inputValue, setInputValue] = useState("");
  const [copied, setCopied] = useState(false);

  const handleCopy = () => {
    navigator.clipboard.writeText(inputValue).then(() => {
      setCopied(true);
      setTimeout(() => setCopied(false), 2000);
    });
  };

  return (
    <div style={{ position: "relative", marginTop: "6rem" }}>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
        className="border-2 "
      />
      <button onClick={handleCopy}>Copy</button>
      <PopupContent copied={copied} />
    </div>
  );
};

export default CopyInput;

```

```JSX

import { createPortal } from "react-dom";

const PopupContent = ({ copied }) => {
  return createPortal(
    <section>
      {copied && (
        <div style={{ position: "absolute", bottom: "3" }}>
          Copied to clipboard
        </div>
      )}
    </section>,
    document.querySelector("#portal-popup")
  );
};
export default PopupContent;

```