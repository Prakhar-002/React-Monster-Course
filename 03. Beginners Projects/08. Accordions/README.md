
<h1  align="center" > 🍄 𝐀𝖼𝖼ⱺ𝗋ᑯ𝗂ⱺ𐓣𝗌 🥠</h1>

<h1  align="center" > 

<img  src="https://github.com/user-attachments/assets/c58dc1fe-b368-47a1-baae-fa3e5fe8c16a" width="500px" height="418px"/>

</h1>

```JSX

//============ App.jsx ============== 

import Accordion from "./Accordion";
import { accordionData } from "./utils/content";

const App = () => {
  return (
    <div>
      <div className="accordion">
        {accordionData.map(({ title, content }) => (
          <Accordion title={title} content={content} />
        ))}
      </div>
    </div>
  );
};

export default App;

```

```JSX

//============ Accordion.jsx ============== 

import { useState } from "react";
import "./index.css";

const Accordion = ({ title, content }) => {
  const [isActive, setIsActive] = useState(false);

  return (
    <section className="accordion-card" key={Math.random()}>
      <div className="header" onClick={() => setIsActive(!isActive)}>
        <div>{title}</div>
        <p className="icon">{isActive ? "-" : "+"}</p>
      </div>

      <div className="content">
        {isActive && <p className="card-info">{content}</p>}
      </div>
    </section>
  );
};

export default Accordion;

```

```JS

//============ utils/content.js ============== 

export const accordionData = [
  {
    title: "What Is HTML?",
    content: `The HyperText Markup Language or HTML is the standard markup language for documents designed to be displayed in a web browser. It can be assisted by technologies such as Cascading Style Sheets and scripting languages such as JavaScript.`,
  },
  {
    title: "What Is React?",
    content: `React is a free and open-source front-end JavaScript library for building user interfaces based on UI components. It is maintained by Meta and a community of individual developers and companies.`,
  },
  {
    title: "What Is Node.js?",
    content: `Node.js is a cross-platform, open-source server environment that can run on Windows, Linux, Unix, macOS, and more. Node.js is a back-end JavaScript runtime environment, runs on the V8 JavaScript Engine, and executes JavaScript code outside a web browser.`,
  },
  {
    title: "What Is Golang?",
    content: `Go is a statically typed, compiled programming language designed at Google by Robert Griesemer, Rob Pike, and Ken Thompson. It is syntactically similar to C, but with memory safety, garbage collection, structural typing, and CSP-style concurrency`,
  },
];

```

<h1  align="center" >🌽 𝓬𝓼𝓼 🪻</h1>

```css

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: rgb(36, 36, 36);
  color: #fff;
  font-family: sans-serif;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.container {
  border: 2px solid white;
}

.accordion-card {
  margin: 20px;
  padding: 20px;
  background: rgb(73, 73, 73);
}

.header {
  display: flex;
  justify-content: space-between;
  width: 40rem;
}

.card-title {
  display: flex;
  justify-content: space-between;
  width: 50rem;
}

.icon {
  font-size: 1.5rem;
  cursor: pointer;
}

p.card-info {
  width: 30rem;
  padding: 20px 0;
  line-height: 1.3;
}

```
