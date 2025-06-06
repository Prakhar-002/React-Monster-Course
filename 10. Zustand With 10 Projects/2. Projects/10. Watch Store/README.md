
<h2  align="center" > 🕍 𝐖α𝗍𝖼ɦ 𝐒𝗍ⱺ𝗋𝖾 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/5e4d1b0a-aea3-4d74-a7f7-799862ea80ef" width="" height=""/>

</h1>

</br>

```TS

//============ store.ts ============== 

import { create } from "zustand";

interface ProductState {
  productStates: Record<
    string,
    {
      currentImage: string;
      hover: boolean;
    }
  >;
  setProductImage: (productId: string, image: string) => void;
  setProductHover: (productId: string, hover: boolean) => void;
  initializeProduct: (productId: string, initialImage: string) => void;
}

interface FilterState {
  selectedCountries: string[];
  selectedColors: string[];
  selectedPriceRange: { min: number; max: number } | null;
  setSelectedCountries: (countries: string[]) => void;
  setSelectedColors: (colors: string[]) => void;
  setSelectedPriceRange: (range: { min: number; max: number } | null) => void;
  clearFilters: () => void;
}

export const useProductStore = create<ProductState>((set) => ({
  productStates: {},
  setProductImage: (productId, image) =>
    set((state) => ({
      productStates: {
        ...state.productStates,
        [productId]: { ...state.productStates[productId], currentImage: image },
      },
    })),
  setProductHover: (productId, hover) =>
    set((state) => ({
      productStates: {
        ...state.productStates,
        [productId]: { ...state.productStates[productId], hover },
      },
    })),
  initializeProduct: (productId, initialImage) =>
    set((state) => ({
      productStates: {
        ...state.productStates,
        [productId]: { currentImage: initialImage, hover: false },
      },
    })),
}));

export const useFilterStore = create<FilterState>((set) => ({
  selectedCountries: [],
  selectedColors: [],
  selectedPriceRange: null,
  setSelectedCountries: (countries) => set({ selectedCountries: countries }),
  setSelectedColors: (colors) => set({ selectedColors: colors }),
  setSelectedPriceRange: (range) => set({ selectedPriceRange: range }),
  clearFilters: () =>
    set({
      selectedCountries: [],
      selectedColors: [],
      selectedPriceRange: null,
    }),
}));

```

```TSX

//============ App.tsx ============== 

import ProductCard from "./components/ProductCard";
import { data } from "./db/data";
import Sidebar from "./components/Sidebar";
import { useFilterStore } from "./store";

interface Product {
  id: string;
  country: string;
  img: Record<string, string>;
  price: number;
}

const App = () => {
  const { selectedCountries, selectedColors, selectedPriceRange } =
    useFilterStore((state) => state);

  const filteredData = data.filter((item: Product) => {
    const matchesColor =
      selectedColors.length === 0 ||
      Object.keys(item.img).some((color) => selectedColors.includes(color));

    const matchesCountry =
      selectedCountries.length === 0 ||
      selectedCountries.includes(item.country);

    const matchesPrice = selectedPriceRange
      ? item.price >= selectedPriceRange.min &&
        item.price <= selectedPriceRange.max
      : true;

    return matchesColor && matchesCountry && matchesPrice;
  });

  return (
    <>
      <Sidebar />

      <div className="p-4 flex flex-wrap justify-center items-center bg-[#F5F5F5] min-h-screen">
        {filteredData.map((product: any) => (
          <ProductCard key={product.id} product={product} />
        ))}
      </div>
    </>
  );

};

export default App;

```

```TSX

//============ components/Sidebar.tsx ============== 

import { useState } from "react";
import { FiChevronDown, FiX } from "react-icons/fi";
import { useFilterStore } from "../store";
import { data } from "../db/data";
import Navigation from "./Navigation";

interface FilterState {
  selectedCountries: string[];
  selectedColors: string[];
  selectedPriceRange: { min: number; max: number } | null;
  setSelectedCountries: (countries: string[]) => void;
  setSelectedColors: (colors: string[]) => void;
  setSelectedPriceRange: (range: { min: number; max: number } | null) => void;
  clearFilters: () => void;
}

interface Product {
  country: string;
  img: Record<string, string>;
  price: number;
}

const Sidebar = () => {
  const [isOpen, setIsOpen] = useState<boolean>(false);
  const [countryDropdown, setCountryDropdown] = useState<boolean>(false);
  const [colorDropdown, setColorDropdown] = useState<boolean>(false);
  const [priceDropdown, setPriceDropdown] = useState<boolean>(false);

  const {
    selectedCountries,
    selectedColors,
    selectedPriceRange,
    setSelectedCountries,
    setSelectedColors,
    setSelectedPriceRange,
    clearFilters,
  } = useFilterStore<FilterState>((state) => state);

  const toggleSidebar = () => setIsOpen(!isOpen);

  const toggleCountryDropdown = () => setCountryDropdown(!countryDropdown);
  const toggleColorDropdown = () => setColorDropdown(!colorDropdown);
  const togglePriceDropdown = () => setPriceDropdown(!priceDropdown);

  const handleCountrySelection = (country: string) => {
    setSelectedCountries(
      selectedCountries.includes(country)
        ? selectedCountries.filter((c) => c !== country)
        : [...selectedCountries, country]
    );
  };

  const handleColorSelection = (color: string) => {
    setSelectedColors(
      selectedColors.includes(color)
        ? selectedColors.filter((c) => c !== color)
        : [...selectedColors, color]
    );
  };

  const handlePriceRangeSelection = (
    range: { min: number; max: number; label: string } | null
  ) => {
    setSelectedPriceRange(range);
  };

  // Extract unique countries from the data
  const uniqueCountries: string[] = Array.from(
    new Set(data.map((item: Product) => item.country))
  );

  return (
    <div>
      <Navigation toggleSidebar={toggleSidebar} />

      {/* Sidebar */}
      <div
        className={`fixed top-0 left-0 h-full w-80 bg-white shadow-lg transform 
                              ${isOpen ? "translate-x-0" : "-translate-x-full"} 
                              transition-transform duration-300 ease-in-out z-50 rounded-r-lg `}
      >
        {/* Header with close button */}
        <div className="flex justify-between items-center p-4 border-b border-[#E5E7EB] bg-[#4A4A4A] text-white">
          <h2 className="text-lg font-semibold">Filters</h2>
          <button onClick={toggleSidebar} className="text-xl">
            <FiX />
          </button>
        </div>

        {/* Filters */}
        <div className="p-4 space-y-6 text-[#4A4A4A]">
          {/* Country Filter */}
          <div>
            <button
              className="flex justify-between items-center w-full text-left font-medium bg-gray-200 hover:bg-gray-300 p-3 rounded-lg"
              onClick={toggleCountryDropdown}
            >
              <span>Country</span>
              <FiChevronDown
                className={`transform ${countryDropdown ? "rotate-180" : ""}`}
              />
            </button>
            {countryDropdown && (
              <div className="mt-2 space-y-2">
                {uniqueCountries.map((country, index) => (
                  <div
                    key={index}
                    className="flex items-center space-x-2 cursor-pointer p-2 ml-2 rounded-md  hover:bg-[#FACC15] transition bg-gray-100"
                    onClick={() => handleCountrySelection(country)}
                  >
                    <input
                      type="checkbox"
                      checked={selectedCountries.includes(country)}
                      onChange={() => handleCountrySelection(country)}
                      className="accent-[#FACC15] w-5 h-5 cursor-pointer"
                    />
                    <span className="text-[#4A4A4A] font-medium">{country}</span>
                  </div>
                ))}
              </div>
            )}
          </div>

          {/* Color Filter */}
          <div>
            <button
              className="flex justify-between items-center w-full text-left font-medium bg-gray-200 hover:bg-gray-300 p-4 rounded-lg"
              onClick={toggleColorDropdown}
            >
              <span>Color</span>
              <FiChevronDown
                className={`transform ${colorDropdown ? "rotate-180" : ""}`}
              />
            </button>
            {colorDropdown && (
              <div className="mt-2 space-y-2">
                {["black", "brown", "red", "white", "golden"].map((color) => (
                  <div
                    key={color}
                    className="flex items-center space-x-2 cursor-pointer p-2 ml-2 rounded-md hover:bg-[#FACC15] transition bg-gray-100"
                    onClick={() => handleColorSelection(color)}
                  >
                    <input
                      type="checkbox"
                      checked={selectedColors.includes(color)}
                      onChange={() => handleColorSelection(color)}
                      className="accent-[#FACC15] w-5 h-5 cursor-pointer"
                    />
                    <span className="text-[#4A4A4A] font-medium">{color}</span>
                  </div>
                ))}
              </div>
            )}
          </div>

          {/* Price Filter */}
          <div>
            <button
              className="flex justify-between items-center  w-full text-left font-medium bg-gray-200 hover:bg-gray-300 p-4 rounded-lg"
              onClick={togglePriceDropdown}
            >
              <span>Price</span>
              <FiChevronDown
                className={`transform ${priceDropdown ? "rotate-180" : ""}`}
              />
            </button>
            {priceDropdown && (
              <div className="mt-2 space-y-2">
                {[{ label: "Below $300", min: 0, max: 300 },
                { label: "$300 - $600", min: 300, max: 600 },
                { label: "Above $600", min: 600, max: Infinity }].map((range) => (
                  <div
                    key={range.label}
                    className="flex items-center space-x-2 cursor-pointer p-2 ml-2 rounded-md hover:bg-[#FACC15] transition bg-gray-100"
                    onClick={() => handlePriceRangeSelection(range)}
                  >
                    <input
                      type="radio"
                      checked={selectedPriceRange?.label === range.label}
                      onChange={() => handlePriceRangeSelection(range)}
                      className="accent-[#FACC15] w-5 h-5 cursor-pointer"
                    />
                    <span className="text-[#4A4A4A] font-medium">{range.label}</span>
                  </div>
                ))}
              </div>
            )}
          </div>
        </div>

        {/* Footer */}
        <div className="p-4 border-t border-[#E5E7EB] bg-[#F9FAFB] absolute bottom-0 w-full flex justify-center">
          <button
            onClick={clearFilters}
            className="bg-[#4A4A4A] text-white text-lg px-6 py-3 w-[90%] rounded-lg hover:bg-[#D97706] hover:text-black transition"
          >
            Clear all
          </button>
        </div>
      </div>

      {/* Background overlay */}
      {isOpen && (
        <div
          className="fixed inset-0 bg-black opacity-50 z-40 cursor-pointer"
          onClick={toggleSidebar}
        ></div>
      )}
    </div>
  );


};

export default Sidebar;

```

```TSX

//============ components/Navigation.tsx ============== 

import { IoBagOutline, IoFilterOutline } from "react-icons/io5";

interface NavigationProps {
  toggleSidebar: () => void;
}

const Navigation = ({ toggleSidebar }: NavigationProps) => {

  return (
    <div className="mt-8 container w-[90%] ml-[5rem] flex justify-between items-center bg-[#4A4A4A] p-4 rounded-lg shadow-md">
      <h1 className="logo">
        <IoFilterOutline
          onClick={toggleSidebar}
          size={27}
          className="ml-16 cursor-pointer text-[#FACC15]"
        />
      </h1>

      <nav>
        <ul className="flex items-center mr-8 space-x-6 text-white font-semibold">
          <li className="hover:text-[#FACC15] cursor-pointer">Search</li>
          <li className="hover:text-[#FACC15] cursor-pointer">Help</li>
          <li className="hover:text-[#FACC15] cursor-pointer">My Account</li>
        </ul>
      </nav>

      <IoBagOutline size={24} className="text-[#FACC15]" />
    </div>
  );

};

export default Navigation;

```

```TSX

//============ components/ProductCard.tsx ============== 

import { useEffect } from "react";
import { useProductStore } from "../store";
import { FaChevronLeft, FaChevronRight } from "react-icons/fa";

interface Product {
  id: string;
  title: string;
  price: number;
  img: {
    black: string;
    [key: string]: string;
  };
}

interface ProductCardProps {
  product: Product;
}

const ProductCard = ({ product }: ProductCardProps) => {
  const { productStates, setProductImage, setProductHover, initializeProduct } =
    useProductStore((state) => state);

  const productState = productStates[product.id] || {};
  const currentImage = productState.currentImage || product.img.black;
  const hover = productState.hover || false;
  const images = Object.values(product.img);

  useEffect(() => {
    initializeProduct(product.id, product.img.black);
  }, [product.id, product.img.black, initializeProduct]);

  const handlePrev = () => {
    const currentIndex = images.indexOf(currentImage);
    const prevIndex = (currentIndex - 1 + images.length) % images.length;
    setProductImage(product.id, images[prevIndex]);
  };

  const handleNext = () => {
    const currentIndex = images.indexOf(currentImage);
    const nextIndex = (currentIndex + 1) % images.length;
    setProductImage(product.id, images[nextIndex]);
  };

  return (
    <div
      className="relative w-[20rem] m-4 border border-[#E5E7EB] bg-white shadow-lg rounded-lg p-4"
      onMouseEnter={() => setProductHover(product.id, true)}
      onMouseLeave={() => setProductHover(product.id, false)}
    >
      <div className="relative bg-[#E5E7EB] p-4 rounded-md">
        <img
          src={currentImage}
          alt={product.title}
          className="object-cover w-[12rem] h-[20rem] rounded-md ml-8"
        />
        {hover && (
          <div className="absolute inset-0 flex items-center justify-between px-4">
            <button onClick={handlePrev} className="carousel-button">
              <FaChevronLeft size={24} className="bg-[#FACC15] text-black p-2 rounded-full" />
            </button>
            <button onClick={handleNext} className="carousel-button">
              <FaChevronRight size={24} className="bg-[#FACC15] text-black p-2 rounded-full" />
            </button>
          </div>
        )}
      </div>
      <div className="mt-4 text-[#4A4A4A]">
        <h2 className="font-bold">{product.title}</h2>
        <p className="text-[#D97706] font-semibold">${product.price}</p>
      </div>
    </div>
  );
};

export default ProductCard;

```

```TS

//============ db/data.ts ============== 

import Image1 from "../assets/image1.png";
import Image2 from "../assets/image2.png";
import Image3 from "../assets/image3.png";
import Image4 from "../assets/image4.png";
import Image6 from "../assets/image6.png";
import Image7 from "../assets/image7.png";
import Image8 from "../assets/image8.png";
import Image9 from "../assets/image9.png";
import Image10 from "../assets/image10.png";
import Image11 from "../assets/image11.png";
import Image12 from "../assets/image12.png";
import Image13 from "../assets/image13.png";
import Image14 from "../assets/image14.png";
import Image15 from "../assets/image15.png";
import Image16 from "../assets/image16.png";
import Image17 from "../assets/image17.png";
import Image18 from "../assets/image18.png";
import Image19 from "../assets/image19.png";
import Image20 from "../assets/image20.png";
import Image21 from "../assets/image21.png";
import Image22 from "../assets/image22.png";
import Image23 from "../assets/image23.png";
import Image24 from "../assets/image24.png";
import Image25 from "../assets/image25.png";
import Image26 from "../assets/image26.png";
import Image27 from "../assets/image27.png";
import Image28 from "../assets/image28.png";
import Image29 from "../assets/image29.png";
import Image30 from "../assets/image30.png";
import Image31 from "../assets/image31.png";
import Image32 from "../assets/image32.png";
import Image33 from "../assets/image33.png";
import Image34 from "../assets/image34.png";
import Image35 from "../assets/image35.png";
import Image36 from "../assets/image36.png";
import Image37 from "../assets/image37.png";
import Image38 from "../assets/image38.png";
import Image39 from "../assets/image39.png";

export const data = [
  {
    id: "1",
    img: {
      black: Image1,
      brown: Image2,
      red: Image3,
      white: Image4,
    },
    title: "Some Random Watch",
    price: 445,
    company: "Nike",
    country: "Japan",
  },
  {
    id: "2",
    img: {
      black: Image6,
      brown: Image7,
      red: Image8,
      white: Image9,
    },
    title: "Some Random Watch",
    price: 340,
    company: "Nike",
    country: "USA",
  },
  {
    id: "3",
    img: {
      black: Image10,
      brown: Image11,
      red: Image12,
      white: Image13,
      golden: Image14,
    },
    title: "Some Random Watch",
    price: 225,
    company: "Nike",
    country: "China",
  },
  {
    id: "4",
    img: {
      black: Image15,
      brown: Image16,
      red: Image17,
      white: Image18,
      golden: Image19,
    },
    title: "Some Random Watch",
    price: 622,
    company: "Nike",
    country: "Japan",
  },
  {
    id: "5",
    img: {
      black: Image20,
      brown: Image21,
      red: Image22,
      golden: Image23,
    },
    title: "Some Random Watch",
    price: 126,
    company: "Nike",
    country: "China",
  },
  {
    id: "6",
    img: {
      black: Image24,
      brown: Image25,
      golden: Image26,
    },
    title: "Some Random Watch",
    price: 722,
    company: "Nike",
    country: "USA",
  },
  {
    id: "7",
    img: {
      black: Image27,
      white: Image28,
      golden: Image29,
    },
    title: "Some Random Watch",
    price: 532,
    company: "Nike",
    country: "Japan",
  },
  {
    id: "8",
    img: {
      black: Image30,
      brown: Image31,
      red: Image32,
      white: Image33,
      golden: Image34,
    },
    title: "Some Random Watch",
    price: 521,
    company: "Nike",
    country: "Japan",
  },
  {
    id: "9",
    img: {
      black: Image35,
      brown: Image36,
    },
    title: "Some Random Watch",
    price: 752,
    company: "Nike",
    country: "India",
  },
  {
    id: "10",
    img: {
      black: Image37,
      red: Image38,
      white: Image39,
    },
    title: "Some Random Watch",
    price: 241,
    company: "Nike",
    country: "Japan",
  },
];

```