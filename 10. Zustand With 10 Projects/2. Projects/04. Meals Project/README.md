
<h2  align="center" > 🕍 𝐌𝖾αᥣ𝗌 𝐏𝗋ⱺ𝗃𝖾𝖼𝗍 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/a68a0ebc-58f7-4c1f-b0b3-1ac3f41532a7" width="" height=""/>

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
      <div className="max-w-4xl mt-3 mx-auto p-6 bg-gray-200 rounded-lg shadow-md">
        <h1 className="text-3xl font-bold text-center text-gray-800 mb-6">Seafood Recipes</h1>
        <input
          type="text"
          placeholder="Search for a meal..."
          value={searchQuery}
          onChange={(e) => setSearchQuery(e.target.value)}
          className="w-full p-3 mb-6 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
        />
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          {filteredMeals.length > 0 ? (
            filteredMeals.map((meal) => (
              <div key={meal.idMeal} className="bg-white p-4 rounded-lg shadow-md">
                <img
                  src={meal.strMealThumb}
                  alt={meal.strMeal}
                  className="w-full h-40 object-cover rounded-lg mb-4"
                />
                <h2 className="text-xl font-semibold text-gray-700">{meal.strMeal}</h2>
              </div>
            ))
          ) : (
            <p className="text-center text-gray-500 col-span-full">No meals found</p>
          )}
        </div>
      </div>
    );
  }

  export default Meals;

```