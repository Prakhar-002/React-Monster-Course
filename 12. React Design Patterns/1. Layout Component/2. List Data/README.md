
<h1  align="center" > 🍄 𝐋𝗂𝗌𝗍 𝐃α𝗍α 🥠</h1>

``` JSX
//============ ⚛️App.tsx ============== 

import GamesInfo from "./components/GamesInfo";
import MoviesInfo from "./components/MoviesInfo";
import RenderList from "./components/RenderList";
import { games, movies } from "./data/data";

const App = () => {
  return (
    <>
      <RenderList
        data={games}
        resourceName="games"
        dataToRender={GamesInfo}
      />

      <hr />
      <br />
      <br />

      <RenderList
        data={movies}
        resourceName="movies"
        dataToRender={MoviesInfo}
      />
    </>
  );
};

export default App;

```

</br>

``` JSX
//============ 🗂️components/⚛️RenderList.tsx ============== 

interface RenderListProps {
  data: any[];
  resourceName: string;
  dataToRender: any;
}

const RenderList = ({
  data,
  resourceName,
  dataToRender: ItemComponent,
}: RenderListProps) => {
  return (
    <div>
      {data.map((item, i) => (
        <ItemComponent key={i} {...{ [resourceName]: item }} />
      ))}
    </div>
  );
};

export default RenderList;

```

</br>

``` JSX
//============ 🗂️components/⚛️GamesInfo.tsx ============== 

interface GamesInfo {
  games: {
    gameName: string;
    gameRating: number;
    gameGenre: string;
    gameLanguages: string[];
  };
}

const GamesInfo = ({ games }: GamesInfo) => {
  const { gameName, gameRating, gameGenre, gameLanguages } = games;

  return (
    <div>
      <h1>Game Name: {gameName}</h1>
      <p>Game Rating: {gameRating}</p>
      <p>Game Genre: {gameGenre}</p>
      <ul>
        Languages:
        {gameLanguages.map((l: string) => (
          <li>{l}</li>
        ))}
      </ul>
    </div>
  );
};

export default GamesInfo;

```

</br>

``` JSX
//============ 🗂️components/⚛️MoviesInfo.tsx ============== 

interface MoviesInfo {
  movies: {
    movieTitle: string;
    moviePrice: number;
    movieDescription: string;
    movieRating: number;
  };
}

const MoviesInfo = ({ movies }: MoviesInfo) => {
  const { movieTitle, moviePrice, movieDescription, movieRating } = movies;

  return (
    <>
      <h1>{movieTitle}</h1>
      <p>Price: {moviePrice}</p>
      <p>Description: {movieDescription}</p>
      <p>Ratings: {movieRating}</p>
    </>
  );
};

export default MoviesInfo;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

## **Challenge: Build a Product Display Application**

### **Challenge 1: Container Component - Build `RenderList`**

Your first challenge is to create a **container component** that can dynamically render a list of items based on the props it receives. In this case, you'll be rendering a list of products.

#### Steps:

1. Create a new component named `RenderList.tsx`.
2. This component should accept the following props:

   - `data`: An array of items (products).
   - `resourceName`: The name of the resource for the items (e.g., `"product"`).
   - `dataToRender`: The component that should be used to render each item (e.g., `ProductInfo`).

3. In the component:

   - Use the `.map()` method to iterate over the `data` array.
   - For each item in the list, pass the individual item to the `dataToRender` component as a prop (using `resourceName` to determine the key).

   **Expected Outcome:**

   - The `RenderList` component should be capable of rendering any array of data passed to it using a dynamic rendering component.

---

### **Challenge 2: Presentational Component - Build `ProductInfo`**

Now, you need to create a **presentational component** that will display the details of each individual product. The goal here is to make the UI clean and reusable for any product object passed to it.

#### Steps:

1. Create a new component named `ProductInfo.tsx`.
2. This component will receive a `product` prop, which is an object containing:

   - `name`: Product name (string)
   - `description`: Product description (string)
   - `price`: Product price (string)
   - `rating`: Product rating (number)
   - `imageUrl`: Product image URL (string)

3. Inside the component:

   - Display the product's `imageUrl` as an image.
   - Display the `name`, `description`, and `price` in styled elements.
   - Render the `rating` as a series of stars (5 stars total). You can use the Unicode star character (`&#9733;`) and fill in the stars based on the rating.

---

### **Challenge 3: Product Data - Use Sample Data Which Is Already Provided**

---

### **Challenge 4: Main App Component - Render Lists for Each Category**

#### Steps:

1. In `App.tsx`, import the `RenderList` component and the data arrays (`electronics`, `clothing`, `homeGoods`).
2. Render the `RenderList` component for each category (electronics, clothing, and homeGoods).

   - For each category, pass the respective data array to the `RenderList` component via the `data` prop.
   - Pass `"product"` as the `resourceName` prop to dynamically pass each product.
   - Pass `ProductInfo` as the `dataToRender` prop to render the individual product details.

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

</br>

``` JSX
//============ ⚛️App.tsx ============== 

import ProductInfo from "./components/ProductInfo";
import RenderList from "./components/RenderList";
import { electronics, clothing, homeGoods } from "./data/data";

const App = () => {
  return (
    <div className="flex flex-wrap justify-center items-center">
      <RenderList
        data={electronics}
        resourceName="product"
        dataToRender={ProductInfo}
      />

      <RenderList
        data={clothing}
        resourceName="product"
        dataToRender={ProductInfo}
      />

      <RenderList
        data={homeGoods}
        resourceName="product"
        dataToRender={ProductInfo}
      />
    </div>
  );
};

export default App;

```

</br>

``` JSX
//============ 🗂️components/⚛️RenderList.tsx ============== 

interface RenderListProps {
  data: any[];
  resourceName: string;
  dataToRender: any;
}

const RenderList = ({
  data,
  resourceName,
  dataToRender: ItemComponent,
}: RenderListProps) => {
  return (
    <div className="product-list">
      {data.map((item, i) => (
        <ItemComponent key={i} {...{ [resourceName]: item }} />
      ))}
    </div>
  );
};

export default RenderList;

```

</br>

``` JSX
//============ 🗂️components/⚛️ProductInfo.tsx ============== 

interface ProductInfo {
  product: {
    name: string;
    description: string;
    price: string;
    rating: number;
    imageUrl: string;
  };
}

const ProductInfo = ({ product }: ProductInfo) => {
  const { name, description, price, rating, imageUrl } = product;

  const renderStars = (rating: number) => {
    const stars = [];
    for (let i = 0; i < 5; i++) {
      stars.push(
        <span
          key={i}
          className={`text-lg ${
            i < rating ? "text-yellow-400" : "text-gray-300"
          }`}
        >
          &#9733;
        </span>
      );
    }
    return stars;
  };

  return (
    <div className="flex items-center w-[30rem] m-[2rem] bg-white shadow-lg rounded-lg overflow-hidden hover:scale-105 transition-transform duration-300">
      {/* Image */}
      <img
        src={imageUrl}
        alt={name}
        className="w-52 h-56 object-cover rounded-t-lg"
      />

      <div className="flex flex-col">
        <h2 className="text-xl font-semibold text-gray-800 mt-4  px-4">
          {name}
        </h2>

        <p className="text-sm text-gray-600 mt-2 px-4">{description}</p>

        <p className="text-lg font-bold text-gray-900 mt-3  px-4">{price}</p>

        <div className="flex mt-2  px-4">{renderStars(rating)}</div>
      </div>
    </div>
  );
};

export default ProductInfo;

```
