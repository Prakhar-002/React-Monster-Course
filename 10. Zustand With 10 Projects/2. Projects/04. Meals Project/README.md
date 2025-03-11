
<h2  align="center" > 🕍 𝐌𝖾αᥣ𝗌 𝐏𝗋ⱺ𝗃𝖾𝖼𝗍 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

</br>

```TS

//============ store.ts ============== 

import { create } from "zustand";

interface Meal {
  idMeal: string;
  strMeal: string;
  strMealThumb: string;
}

interface StoreState {
  meals: Meal[];
  searchQuery: string;
  setMeals: (meals: Meal[]) => void;
  setSearchQuery: (query: string) => void;
}

export const useStore = create<StoreState>((set) => ({
  meals: [],
  searchQuery: "",
  setMeals: (meals: Meal[]) => set({ meals }),
  setSearchQuery: (query: string) => set({ searchQuery: query }),
}));

```

```TSX

//============ App.tsx ============== 

import Meals from "./components/Meals";

const App = () => {
  return (
    <div>
      <Meals />
    </div>
  );
};

export default App;

```

```TSX

//============ components/Meals.tsx ============== 

import { useEffect } from "react";
import { useStore } from "../store";

function Meals() {
  const { meals, searchQuery, setMeals, setSearchQuery } = useStore();

  useEffect(() => {
    const fetchMeals = async () => {
      try {
        const response = await fetch(
          "https://www.themealdb.com/api/json/v1/1/filter.php?c=Seafood"
        );
        const data = await response.json();
        setMeals(data.meals);
      } catch (error) {
        console.error("Error fetching data:", error);
      }
    };

    fetchMeals();
  }, [setMeals]);

  const filteredMeals = meals.filter((meal) =>
    meal.strMeal.toLowerCase().includes(searchQuery.toLowerCase())
  );

  return (
    <div>
      <h1>Seafood Recipes</h1>
      <input
        type="text"
        placeholder="Search for a meal..."
        value={searchQuery}
        onChange={(e) => setSearchQuery(e.target.value)}
      />
      <div>
        {filteredMeals.length > 0 ? (
          filteredMeals.map((meal) => (
            <div key={meal.idMeal}>
              <h2>{meal.strMeal}</h2>
              <img src={meal.strMealThumb} alt={meal.strMeal} />
            </div>
          ))
        ) : (
          <p>No meals found</p>
        )}
      </div>
    </div>
  );
}

export default Meals;

```