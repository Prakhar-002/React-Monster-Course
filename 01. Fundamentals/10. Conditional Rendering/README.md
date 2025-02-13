
<h3  align="center" >𝐂ⱺ𐓣ᑯ𝗂𝗍𝗂ⱺ𐓣αᥣ 𝐑𝖾𐓣ᑯ𝖾𝗋𝗂𐓣𝗀</h3>

``` JSX

// In this video I'm gonna give you the practice of functional component
// BUT you're totally free to work with class based components as well 🥂

// ------------------  Example 1 (IF) ------------------

// const ValidPassword = () => <h1>Valid Password</h1>;
// const InvalidPassword = () => <h1>Invalid Password</h1>;

// const Password = ({ isValid }) => {
//   if (isValid) {
//     return <ValidPassword />;
//   }
//   return <InvalidPassword />;
// };

// const App = () => {
//   return (
//     <section>
//       <Password isValid={true} />
//     </section>
//   );
// };

// ------------------  Example 2 (&&) ------------------

// function Cart() {
//   const items = ["Wireless Earbuds", "Power Bank", "New SSD", "Hoddie"];

//   return (
//     <>
//       <h1>Cart 🛒</h1>
//       {items.length > 0 && <h2>You have {items.length} items in your Cart.</h2>}

//       <ul>
//         <h4> 👇Products </h4>
//         {items.map((item) => (
//           <li key={Math.random()}>{item}</li>
//         ))}
//       </ul>
//     </>
//   );
// }

// const App = () => <Cart />;

// ------------------ Example 3 (Ternary Operator) ------------------
// condition ? true : false

const ValidPassword = () => <h1>Valid Password</h1>;
const InvalidPassword = () => <h1>Invalid Password</h1>;

const Password = ({ isValid }) =>
  isValid ? <ValidPassword /> : <InvalidPassword />;

const App = () => {
  return (
    <section>
      <Password isValid={true} />
    </section>
  );
};

export default App;

```

</br>

<h3  align="center" >𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌</h3>

### Exercise: Conditional Rendering in React

In this exercise, you will practice different ways to render JSX conditionally in React components.

#### Step 1: Create a `Weather` Component with `if`, `else if`, and `else`

1. Create a new file called `Weather.jsx`.
2. Inside this file, create a functional component called `Weather`.
3. The component should:
   - Take a `temperature` prop.
   - Use `if`, `else if`, and `else` statements to conditionally render different messages based on the temperature value:
     - If the temperature is below 15, display: "It's cold outside!"
     - If the temperature is between 15 and 25, display: "It's nice outside!"
     - If the temperature is above 25, display: "It's hot outside!"

#### Step 2: Create a `UserStatus` Component with the `&&` Operator

1. Create a new file called `UserStatus.jsx`.
2. Inside this file, create a functional component called `UserStatus`.
3. The component should:
   - Take two boolean props `loggedIn`, `isAdmin`
   - Use the `&&` operator to display a message for Admin & Normal User:
     - If `loggedIn` is `true` and `isAdmin` display: "Welcome Admin!"
     - If it's just `loggedIn` and not admin then display "Welcome User".

#### Step 3: Create a `Greeting` Component with a Ternary Operator

1. Create a new file called `Greeting.jsx`.
2. Inside this file, create a functional component called `Greeting`.
3. The component should:
   - Take a `timeOfDay` prop (e.g., `"morning"`, `"afternoon"`, or `"evening"`).
   - Use the ternary operator to conditionally display different greetings based on the time of day:
     - If `timeOfDay` is `"morning"`, display: "Good morning!"
     - If `timeOfDay` is `"afternoon"`, display: "Good afternoon!"

#### Step 4: Render the Components in `App.jsx`

1. In your `App.jsx` file, import the `Weather`, `UserStatus`, and `Greeting` components:

   ```jsx
   import Weather from "./Weather";
   import UserStatus from "./UserStatus";
   import Greeting from "./Greeting";
   ```

2. Inside the `App` component, render each component with different props to test the conditional rendering logic.

Example:

```jsx
function App() {
  return (
    <div>
      <h1>Conditional Rendering in React</h1>

      {/* Weather component */}
      <Weather temperature={10} />
      <Weather temperature={20} />
      <Weather temperature={30} />

      {/* UserStatus component */}
      <UserStatus loggedIn={true} />
      <UserStatus loggedIn={false} />

      {/* Greeting component */}
      <Greeting timeOfDay="morning" />
      <Greeting timeOfDay="afternoon" />
      <Greeting />
    </div>
  );
}

export default App;
```

</br>

<h3  align="center" >𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣</h3>

```JSX

//============ App.jsx ============== 

import Greeting from "./components/Greeting";
import UserStatus from "./components/UserStatus";
import Weather from "./components/Weather";

function App() {
  return (
    <>
      <Weather />
      <UserStatus loggedIn={true} isAdmin={false} />
      <Greeting timeOfDay="morning" />
    </>
  );
}

export default App;

```

```JSX

//============ Weather.jsx ============== 

const Weather = () => {
  let temp = 26;

  // If the temperature is below 15, display: "It's cold outside!"
  // If the temperature is between 15 and 25, display: "It's nice outside!"
  // If the temperature is above 25, display: "It's hot outside!"

  if (temp < 15) {
    return <div>It's cold outside!</div>;
  } else if (temp >= 15 && temp <= 25) {
    return <div>It's nice outside!</div>;
  } else if (temp > 25) {
    return <div>It's hot outside!</div>;
  }
};

export default Weather;

```

```JSX

//============ UserStatus.jsx ============== 

const UserStatus = (props) => {
  // Use the && operator to display a message if the user is logged in:
  // If loggedIn is true, display: "Welcome back!"
  // If loggedIn is false, display nothing.

  if (props.loggedIn && props.isAdmin) {
    return <div>Welcome admin</div>;
  } else {
    return <div>Welcome user</div>;
  }
};

export default UserStatus;

```

```JSX

//============ Greeting.jsx ============== 

const Greeting = (props) => {
  // Take a timeOfDay prop (e.g., "morning", "afternoon", or "evening").
  // Use the ternary operator to conditionally display different greetings based on the time of day:
  // If timeOfDay is "morning", display: "Good morning!"
  // If timeOfDay is "afternoon", display: "Good afternoon!"
  // If timeOfDay is not provided, display: "Hello!"

  return props.timeOfDay === "morning" ? (
    <div>Good morning!</div>
  ) : (
    <div>Good afternoon!</div>
  );
};
export default Greeting;

```