
<h1  align="center" > 🍄 𝐒ρᥣ𝗂𝗍 𝐒𝖼𝗋𝖾𝖾𐓣 🥠</h1>

``` JSX
//============ ⚛️App.tsx ============== 

import Left from "./components/Left";
import Right from "./components/Right";
import SplitScreen from "./components/SplitScreen";

const App = () => {
  return (
    // <SplitScreen leftWeight={50} rightWeight={30}>
    <SplitScreen leftWeight={15} rightWeight={80}>
      <Left />
      <Right />
    </SplitScreen>
  );
};

export default App;

```

</br>

``` JSX
//============ 🗂️components/⚛️SplitScreen.tsx ============== 

import { ReactNode } from "react";

interface SplitScreenProps {
  children: [ReactNode, ReactNode];
  leftWeight: number;
  rightWeight: number;
}

const SplitScreen = ({
  children,
  leftWeight = 1,
  rightWeight = 1,
}: SplitScreenProps) => {
  const [left, right] = children;

  const leftWidth = `${leftWeight}rem`;
  const rightWidth = `${rightWeight}rem`;

  return (
    <section className="flex w-screen">
      <div style={{ width: leftWidth }}>{left}</div>
      <div style={{ width: rightWidth }}>{right}</div>
    </section>
  );
};

export default SplitScreen;

```

</br>

``` JSX
//============ 🗂️components/⚛️Left.tsx ============== 

const Left = () => {
  // return <div className="bg-teal-400">Left</div>;
  return <div className="bg-teal-400 h-[46rem]">Left</div>;
};

export default Left;

```

</br>

``` JSX
//============ 🗂️components/⚛️Right.tsx ============== 

const Right = () => {
  return <div className="bg-red-400">Right</div>;
};

export default Right;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Challenge: Building a Dashboard Layout with Layout Component

1. **Create the `Header` Component**

   - The `Header` component will contain the dashboard's title and a profile/logout button.
   - Use Tailwind for styling to create a header with a background color and proper alignment.

   **Task:**

   - Create a `Header.tsx` file in the `src/components` folder.
   - Implement the following structure:
     - A header with a background color.
     - A title on the left side ("My Dashboard").
     - A profile button and a logout button aligned to the right.

2. **Create the `Footer` Component**

   - The `Footer` component will be a simple footer with a copyright message.
   - It should be styled to stick at the bottom of the page.

   **Task:**

   - Create a `Footer.tsx` file in the `src/components` folder.
   - Add the text: `&copy; 2025 My Dashboard App`.

3. **Create the `Sidebar` Component**

   - The `Sidebar` component will be a vertical sidebar on the left side.
   - Include a list of links for "Home", "Settings", and "Profile".

   **Task:**

   - Create a `Sidebar.tsx` file in the `src/components` folder.
   - Use Tailwind to style the sidebar with a background color, padding, and a simple list of links.
   - Add hover effects to the links.

4. **Create the `Content` Component**

   - The `Content` component will display the main dashboard content with some stats (e.g., Total Users and Revenue).
   - Use Tailwind CSS grid to layout the stats in two columns.

   **Task:**

   - Create a `Content.tsx` file in the `src/components` folder.
   - Display two stats cards: one for "Total Users" and one for "Revenue".
   - Make the cards visually distinct using Tailwind CSS classes.

5. **Create the `SplitScreen` Component**

   - The `SplitScreen` component will manage the layout between the sidebar and content area.
   - This component should accept two children: the left side (sidebar) and the right side (content). The widths of each side should be controlled through props.

   **Task:**

   - Create a `SplitScreen.tsx` file in the `src/components` folder.
   - The component should accept `children` (two elements), `leftWeight`, and `rightWeight` as props.
   - The widths of the left and right sections should be dynamically set based on the `leftWeight` and `rightWeight` props.

---

### Step 3: Assemble the Layout in `App.tsx`

1. **Import and Use the Components in `App.tsx`**

   - In the `App.tsx` file, import all the components you've created so far: `Header`, `Footer`, `Sidebar`, `Content`, and `SplitScreen`.

   **Task:**

   - Use the `Header` at the top of the page.
   - Use `SplitScreen` to structure the layout, passing the `Sidebar` as the left child and the `Content` as the right child.
   - Set the `leftWeight` to `3` and `rightWeight` to `60` (or adjust as necessary to get the desired layout).
   - Use the `Footer` component at the bottom of the page.

2. **Ensure Responsiveness**

   - Adjust the layout to be responsive. Ensure that the sidebar is properly aligned with the content and doesn't overlap.
   - Use Tailwind's responsive utilities to adjust the layout on different screen sizes.

   **Task:**

   - Ensure the app is responsive. On smaller screens (e.g., mobile), the sidebar should collapse or be hidden, and the content should take up the full width.


</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

</br>

``` JSX
//============ ⚛️App.tsx ============== 

import Header from "./components/Header";
import Footer from "./components/Footer";
import SplitScreen from "./components/SplitScreen";
import Sidebar from "./components/Sidebar";
import Content from "./components/Content";

const App = () => {
  return (
    <div className="flex flex-col h-screen">
      {/* Header */}
      <Header />

      {/* Main Content Layout */}
      <SplitScreen leftWeight={3} rightWeight={60}>
        <Sidebar />
        <Content />
      </SplitScreen>

      {/* Footer */}
      <Footer />
    </div>
  );
};

export default App;

```

</br>

``` JSX
//============ 🗂️components/⚛️SplitScreen.tsx ============== 

import { ReactNode } from "react";

interface SplitScreenProps {
  children: [ReactNode, ReactNode];
  leftWeight: number;
  rightWeight: number;
}

const SplitScreen = ({
  children,
  leftWeight = 1,
  rightWeight = 1,
}: SplitScreenProps) => {
  const [left, right] = children;

  const leftWidth = `${leftWeight}rem`;
  const rightWidth = `${rightWeight}rem`;

  return (
    <section className="flex flex-1">
      <div style={{ width: leftWidth }} className="p-4">
        {left}
      </div>
      <div style={{ width: rightWidth }} className="p-4">
        {right}
      </div>
    </section>
  );
};

export default SplitScreen;

```

</br>

``` JSX
//============ 🗂️components/⚛️ Header.tsx ============== 

const Header = () => {
  return (
    <header className="bg-teal-600  text-white p-4 flex justify-between items-center">
      <h1 className="text-xl">My Dashboard</h1>
      <div className="flex items-center space-x-4">
        <button className="bg-teal-800 p-2 rounded-full">Profile</button>
        <button className="bg-teal-800 p-2 rounded-full">Logout</button>
      </div>
    </header>
  );
};

export default Header;

```

</br>

``` JSX
//============ 🗂️components/⚛️ Sidebar.tsx ============== 

const Sidebar = () => {
  return (
    <div className="bg-teal-500 h-full w-[10rem] text-white p-4">
      <h2 className="text-xl">Dashboard</h2>
      <ul className="mt-6 space-y-4">
        <li>
          <a href="#home" className="hover:text-gray-200">
            Home
          </a>
        </li>
        <li>
          <a href="#settings" className="hover:text-gray-200">
            Settings
          </a>
        </li>
        <li>
          <a href="#profile" className="hover:text-gray-200">
            Profile
          </a>
        </li>
      </ul>
    </div>
  );
};

export default Sidebar;

```

</br>

</br>

``` JSX
//============ 🗂️components/⚛️ Content.tsx ============== 

const Content = () => {
  return (
    <div className="bg-white shadow-md rounded-lg p-6 ml-[10rem]">
      <h2 className="text-2xl font-bold">Welcome to the Dashboard!</h2>
      <p className="mt-4">Here are your stats for today:</p>
      <div className="mt-6 grid grid-cols-2 gap-4">
        <div className="bg-gray-100 p-4 rounded-md">
          <h3 className="text-lg">Total Users</h3>
          <p className="text-xl font-semibold">1,245</p>
        </div>
        <div className="bg-gray-100 p-4 rounded-md">
          <h3 className="text-lg">Revenue</h3>
          <p className="text-xl font-semibold">$4,850</p>
        </div>
      </div>
    </div>
  );
};

export default Content;

```

</br>

``` JSX
//============ 🗂️components/⚛️ Footer.tsx ============== 

const Footer = () => {
  return (
    <footer className="bg-teal-800 text-white p-4 text-center">
      <p>&copy; 2025 My Dashboard App</p>
    </footer>
  );
};

export default Footer;

```
