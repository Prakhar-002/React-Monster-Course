
<h1  align="center" > 🍄 𝐌𝖾αᥣ𝗌 𝐀𝐏𝚰 𝐏𝗋ⱺ𝗃𝖾𝖼𝗍 🥠</h1>

![image](https://github.com/user-attachments/assets/fd2542b0-e8ee-4af3-a34a-e68d867ec0e1)

```JSX

//============ App.jsx ============== 

import Meal from "./Meal";

const App = () => {
  return <Meal />;
};

export default App;

```

```JSX

//============ Components/Meal.jsx ============== 

import axios from "axios";
import { useState, useEffect } from "react";
import "./style.css";

function Meal() {
  const [items, setItems] = useState([]);

  useEffect(() => {
    axios
      .get("https://www.themealdb.com/api/json/v1/1/filter.php?c=Seafood")
      .then((res) => {
        // console.log(res.data);
        setItems(res.data.meals);
      })
      .catch((err) => {
        console.log(err);
      });
  }, []);

  const itemsList = items.map(({ strMeal, strMealThumb, idMeal }) => {
    return (
      <section className="card">
        <img src={strMealThumb} />
        <section className="content">
          <p>{strMeal}</p>
          <p>#{idMeal}</p>
        </section>
      </section>
    );
  });

  return <div className="items-container">{itemsList}</div>;
}

export default Meal;

```

<h1  align="center" >🌽 𝓬𝓼𝓼 🪻</h1>

```css

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.items-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  margin: 10px;
}

.card {
  background: rgb(255, 249, 249);
  font-size: 12px;
  color: rgb(68, 68, 68);
  margin: 10px;
  padding: 30px;
  transition: 1s ease;
  cursor: pointer;
}

.card:hover {
  transform: scale(1.1);
}

.content {
  display: flex;
  justify-content: space-between;
  font-family: sans-serif;
  margin-top: 20px;
}

p {
  font-weight: bold;
}

img {
  border-radius: 5px;
  height: 200px;
  width: 300px;
}

```
