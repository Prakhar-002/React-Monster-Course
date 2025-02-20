
<h1  align="center" > 🍄 𝐓𝖾𝗌𝗍𝗂ꭑⱺ𐓣𝗂αᥣ𝗌 🥠</h1>

<h1  align="center" > 

<img  src="https://github.com/user-attachments/assets/7a153609-7de6-41a4-ba25-14f79fd4dc38" width="600" height="346"/>

</h1>

```JSX

//============ App.jsx ============== 

import Testimonials from "./Testimonials";

function App() {
  return <Testimonials />;
}

export default App;

```

```JSX

//============ Testimonials.jsx ============== 

import React, { useState } from "react";
import "./index.css";

function Testimonials() {
  const [currentIndex, setCurrentIndex] = useState(0);
  const testimonials = [
    {
      quote: "This is the best product I've ever used!",
      author: "Jane Doe",
    },
    {
      quote: "I highly recommend this product to everyone!",
      author: "John Smith",
    },
    {
      quote: "This product has completely changed my life!",
      author: "Bob Johnson",
    },
  ];

  const handlePrevClick = () => {
    setCurrentIndex(
      (currentIndex + testimonials.length - 1) % testimonials.length
    );
  };

  const handleNextClick = () => {
    setCurrentIndex((currentIndex + 1) % testimonials.length);
  };

  return (
    <div className="testimonials">
      <div className="testimonials-quote">
        {testimonials[currentIndex].quote}
      </div>
      <div className="testimonials-author">
        - {testimonials[currentIndex].author}
      </div>
      <div className="testimonials-nav">
        <button onClick={handlePrevClick}>Prev</button>
        <button onClick={handleNextClick}>Next</button>
      </div>
    </div>
  );
}

export default Testimonials;

```

<h1  align="center" >🌽 𝓬𝓼𝓼 🪻</h1>

```css

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #e8faff;
}

.testimonials {
  margin: 0 auto;
  text-align: center;
  font-family: sans-serif;
  border-radius: 10px;
  padding: 40px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: #f0fdfe;
}

.testimonials-quote {
  font-size: 22px;
  font-style: italic;
  margin-bottom: 10px;
  color: #666;
}

.testimonials-author {
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 20px;
  color: #333;
}

.testimonials-nav {
  display: flex;
  justify-content: space-between;
}

.testimonials-nav button {
  padding: 10px 20px;
  border: none;
  background-color: #82e5ee;
  color: #fff;
  font-size: 16px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.testimonials-nav button:hover {
  background-color: #037680;
}

.testimonials-nav button:active {
  transform: scale(0.95);
}

```
