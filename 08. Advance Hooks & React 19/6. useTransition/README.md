
<h1  align="center" > 🍄 𝐔𝗌𝖾 𝐓𝗋α𐓣𝗌𝗂𝗍𝗂ⱺ𐓣 🥠</h1>

<h2  align="center" > 🍄 1. 𝐖𝗂𝗍ɦⱺυ𝗍 𝐔𝗌𝖾 🥠</h2>

```JSX

//============ WithoutTraction.jsx ============== 

const App = () => {
  const [activeTab, setActiveTab] = useState("home");

  const renderContent = () => {
    switch (activeTab) {
      case "home":
        return <Home />;
      case "posts":
        return <Posts />;
      case "contact":
        return <Contact />;
      default:
        return <Home />;
    }
  };

  return (
    <div>
      <div className="tabs">
        <button onClick={() => setActiveTab("home")}>Home</button>
        <button onClick={() => setActiveTab("posts")}>Posts</button>
        <button onClick={() => setActiveTab("contact")}>Contact</button>
      </div>
      <div className="content">{renderContent()}</div>
    </div>
  );
};

export default App;

```

</br>

<h2  align="center" > 🍄 2. 𝐖𝗂𝗍ɦ 𝐔𝗌𝖾 🥠</h2>

```JSX

//============ App.jsx ============== 

import { useState, useTransition } from "react";
import Home from "./components/Home";
import Posts from "./components/Posts";
import Contact from "./components/Contact";

const App = () => {
  const [activeTab, setActiveTab] = useState("home");
  const [isPending, startTransition] = useTransition();

  const handleTabChange = (tab) => {
    startTransition(() => {
      setActiveTab(tab);
    });
  };

  const renderContent = () => {
    switch (activeTab) {
      case "home":
        return <Home />;
      case "posts":
        return <Posts />;
      case "contact":
        return <Contact />;
      default:
        return <Home />;
    }
  };

  return (
    <div>
      <div className="tabs">
        <button
          className="border-2 p-4 m-2"
          onClick={() => handleTabChange("home")}
        >
          Home
        </button>
        <button
          className="border-2 p-4 m-2"
          onClick={() => handleTabChange("posts")}
        >
          Posts
        </button>
        <button
          className="border-2 p-4 m-2"
          onClick={() => handleTabChange("contact")}
        >
          Contact
        </button>
      </div>
      {isPending && <p>Loading...</p>}
      <div className="content">{renderContent()}</div>
    </div>
  );
};

export default App;

```

```JSX

//============ components/Home.jsx ============== 

const Home = () => <p>This is the Home component.</p>;
export default Home;

```

```JSX

//============ components/Content.jsx ============== 

const Contact = () => <p>This is the Contact component.</p>;
export default Contact;

```

```JSX

//============ components/Posts.jsx ============== 

const Posts = () => {
  // Generate a lot of posts
  const posts = Array.from(
    { length: 100000 },
    (_, index) => `Post ${index + 1}`
  );

  return (
    <div>
      {posts.map((post) => (
        <div key={post} className="post">
          {post}
        </div>
      ))}
    </div>
  );
};

export default Posts;

```
