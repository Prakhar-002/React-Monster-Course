
<h1  align="center" > 🍄 𝐑𝖾α𝖼𝗍 𝐇ⱺⱺ𝗄 𝐅ⱺ𝗋ꭑ 🥠</h1>

```TSX

//============ Main.tsx ============== 

import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

ReactDOM.createRoot(document.getElementById("root") as HTMLElement).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

```

```TSX

//============ App.tsx ============== 

import SimpleForm from "./components/SimpleForm";
import "./style.css";

function App() {
  return (
    <div>
      <SimpleForm />
    </div>
  );
}

export default App;

```

```TSX

//============ components/SimpleForm.tsx ============== 

import { useForm, SubmitHandler } from "react-hook-form";

interface FormData {
  name: string;
  email: string;
  password: string;
}

const SimpleForm = () => {
  // register:  is used to connect input fields to the form.
  // handleSubmit:  is a function to handle form submission.
  // errors:  contains validation errors for the form.

  const {
    register,
    handleSubmit,
    formState: { errors, isSubmitting },
  } = useForm<FormData>();

  // console.log(errors);

  const onSubmit: SubmitHandler<FormData> = (data) => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <div>
        <label htmlFor="name">Name:</label>
        <input
          id="name"
          type="text"
          {...register("name", { required: "Name is required" })}
        />
        {errors.name && <p style={{ color: "red" }}>{errors.name.message}</p>}
      </div>

      <div>
        <label htmlFor="email">Email:</label>
        <input
          {...register("email", {
            required: "Email is required",
            pattern: {
              value: /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i,
              message: "Invalid email address",
            },
          })}
          type="email"
          id="email"
          placeholder="Email"
        />

        {errors.email && (
          <div style={{ color: "red" }}>{errors.email.message}</div>
        )}
      </div>

      <input
        {...register("password", {
          minLength: {
            value: 8,
            message: "Password must be at least 8 characters",
          },
        })}
        type="password"
        placeholder="Password"
      />

      {errors.password && (
        <div style={{ color: "red" }}>{errors.password.message}</div>
      )}

      <button disabled={isSubmitting}>
        {isSubmitting ? "Loading..." : "Submit"}
      </button>
    </form>
  );
};

export default SimpleForm;

```


```CSS

body {
  background: #000;
  color: #fff;
}

```

</br>

<h1  align="center" >🌽 𝐏𝗋ⱺ𝗃𝖾𝖼𝗍 🪻</h1>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/b57a9c0a-5ca7-466a-b175-9a0ce84adaa0" width="410px" height="600px"/>

</h1>

```TSX

//============ App.tsx ============== 

import MyForm from "./components/MyForm";

const App = () => {
  return (
    <div>
      <MyForm />
    </div>
  );
};

export default App;

```

```TSX

//============ components/MyForm.tsx ============== 

import { useForm, SubmitHandler } from "react-hook-form";
import "../style.css";

interface FormData {
  firstName: string;
  lastName: string;
  email: string;
  city: string;
  state: string;
  zip: string;
  country: string;
  completeLocation: string;
}

const MyForm: React.FC = () => {
  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm<FormData>();

  // Define the submit handler with the proper type
  const onSubmit: SubmitHandler<FormData> = (data) => {
    console.log(data);
  };

  return (
    <div className="form-container">
      <h2>Registration Form</h2>
      <form onSubmit={handleSubmit(onSubmit)}>
        <div>
          <label htmlFor="firstName">First Name</label>
          <input
            id="firstName"
            type="text"
            {...register("firstName", { required: "First Name is required" })}
          />
          {errors.firstName && <p>{errors.firstName.message}</p>}
        </div>

        <div>
          <label htmlFor="lastName">Last Name</label>
          <input
            id="lastName"
            type="text"
            {...register("lastName", { required: "Last Name is required" })}
          />
          {errors.lastName && <p>{errors.lastName.message}</p>}
        </div>

        <div>
          <label htmlFor="email">Email Address</label>
          <input
            id="email"
            type="email"
            {...register("email", {
              required: "Email Address is required",
              pattern: {
                value: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
                message: "Invalid email address",
              },
            })}
          />
          {errors.email && <p>{errors.email.message}</p>}
        </div>

        <div>
          <label htmlFor="city">City</label>
          <input
            id="city"
            type="text"
            {...register("city", { required: "City is required" })}
          />
          {errors.city && <p>{errors.city.message}</p>}
        </div>

        <div>
          <label htmlFor="state">State</label>
          <input
            id="state"
            type="text"
            {...register("state", { required: "State is required" })}
          />
          {errors.state && <p>{errors.state.message}</p>}
        </div>

        <div>
          <label htmlFor="zip">ZIP</label>
          <input
            id="zip"
            type="text"
            {...register("zip", { required: "ZIP is required" })}
          />
          {errors.zip && <p>{errors.zip.message}</p>}
        </div>

        <div>
          <label htmlFor="country">Country</label>
          <input
            id="country"
            type="text"
            {...register("country", { required: "Country is required" })}
          />
          {errors.country && <p>{errors.country.message}</p>}
        </div>

        <div>
          <label htmlFor="completeLocation">Complete Location</label>
          <textarea
            id="completeLocation"
            {...register("completeLocation", {
              required: "Complete Location is required",
            })}
          />
          {errors.completeLocation && <p>{errors.completeLocation.message}</p>}
        </div>

        <button type="submit">Submit</button>
      </form>
    </div>
  );
};

export default MyForm;

```

```CSS

body {
  font-family: sans-serif;
}

.form-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
}

form div {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

input,
textarea {
  width: 100%;
  padding: 8px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  padding: 10px 15px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

p {
  color: red;
  margin: 5px 0;
}

```
