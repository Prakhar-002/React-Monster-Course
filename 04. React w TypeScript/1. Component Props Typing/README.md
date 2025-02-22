
<h1  align="center" > 🍄 𝐂ⱺꭑρⱺ𐓣𝖾𐓣𝗍 𝐏𝗋ⱺρ𝗌 𝐓𝗒ρ𝗂𐓣𝗀 🥠</h1>

```TSX

//============ App.tsx ============== 

import User from "@/live coding/components/User";

export default function Home() {
  return (
    <section>
      {/* <User name="alex" age={20} isStudent={true} /> */}
      <User>
        <p>Hello</p>
      </User>
    </section>
  );
}

```

```TSX

//============ components/User.tsx ============== 

// -------------------------------------
// 1. Passing Types

// const User = (props: { name: string; age: number; isStudent: boolean }) => {
//   return (
//     <main>
//       <h2>{props.name}</h2>
//       <p>{props.age}</p>
//       <p>{props.isStudent}</p>
//     </main>
//   );
// };

// export default User;

// -------------------------------------
// 2. Destructuring Props Values

// const User = ({
//   name,
//   age,
//   isStudent,
// }: {
//   name: string;
//   age: number;
//   isStudent: boolean;
// }) => {
//   return (
//     <main>
//       <h2>{name}</h2>
//       <p>{age}</p>
//       <p>{isStudent}</p>
//     </main>
//   );
// };

// export default User;

// -------------------------------------
// 3. Creating Custom Types (type alias & Interfaces)

// type UserShape = {
//   name: string;
//   age: number;
//   isStudent: boolean;
// };

// interface UserShape {
//     name: string;
//     age: number;
//     isStudent: boolean;
// }

// const User = ({ name, age, isStudent }: UserShape) => {
//   return (
//     <main>
//       <h2>{name}</h2>
//       <p>{age}</p>
//       <p>{isStudent}</p>
//     </main>
//   );
// };

//  export default User;

// -------------------------------------
// 4. Children

import { type ReactNode } from "react";

type Shape = {
  children: ReactNode;
};

const User = ({ children }: Shape) => {
  return <main>{children}</main>;
};

export default User;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

# Component Props Typing

## Objective

In this exercise, you'll practice typing props for a React component using TypeScript. You will create a simple `Button` component with typed props and then use it within a parent component.

## Instructions

### Step 1: Create the `Button` Component

1. Create a new file named `Button.tsx` in the `src` directory.

2. Define a `Button` component that accepts the following props:

   - `label`: A string to display as the button's text.
   - `onClick`: A function that gets called when the button is clicked.
   - `disabled`: A boolean to indicate if the button is disabled.

### Step 2: Use the `Button` Component

1. Open `App.tsx` (or create a new component if you prefer).

2. Import and use the `Button` component, passing the appropriate props.

### Step 3: Verify Your Types

1. Make sure your TypeScript compiler is not showing any type errors.

2. Test the buttons in the browser to ensure they work as expected:
   - The first button should display "Click Me" and show an alert when clicked.
   - The second button should be disabled and should not trigger the alert.

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```TSX

//============ App.tsx ============== 

import Button from "./components/Button";

const App = () => {
  return (
    <div>
      <Button
        label="Click"
        onClick={() => console.log("clicked")}
        disabled={false}
      />
    </div>
  );
};

export default App;

```

```TSX

//============ components/Button.tsx ============== 

// const Button = (props: {
//   label: string;
//   onClick: () => void;
//   disabled: boolean;
// }) => {
//   return (
//     <div>
//       <button onClick={props.onClick} disabled={props.disabled}>
//         {props.label}
//       </button>
//     </div>
//   );
// };

// export default Button;

// Destructuring
const Button = ({
  label,
  onClick,
  disabled,
}: {
  label: string;
  onClick: () => void;
  disabled: boolean;
}) => {
  return (
    <div>
      <button onClick={onClick} disabled={disabled}>
        {label}
      </button>
    </div>
  );
};

export default Button;

```