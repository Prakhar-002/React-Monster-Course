
<h1  align="center" > 🍄 𝐅ⱺ𝗋ꭑ 𝐕αᥣ𝗂ᑯα𝗍𝗂ⱺ𐓣 🥠</h1>

<h1  align="center" > 

<img  src="https://github.com/user-attachments/assets/265cb34e-cda3-4021-859e-d9842e42ef05" width="500px" height="304px"/>

</h1>

```JSX

//============ App.jsx ============== 

import Form from "./Form";
import "./style.css";

const App = () => {
  return <Form />;
};

export default App;

```

```JSX

//============ Form.jsx ============== 

import { useState } from "react";

function Form() {
  const [username, setusername] = useState("");
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const [confirmPassword, setConfirmPassword] = useState("");

  const [errorUserName, setErrorUserName] = useState("");
  const [errorEmail, setErrorEmail] = useState("");
  const [errorPassword, setErrorPassword] = useState("");
  const [errorConfrimPassword, setErrorConfirmPassword] = useState("");

  const [userColor, setUserColor] = useState("");
  const [emailColor, setEmailColor] = useState("");
  const [passwordColor, setPasswordColor] = useState("");
  const [confirmPasswordColor, setConfirmPasswordColor] = useState("");

  function validate(e) {
    e.preventDefault();

    if (username.length > 8) {
      setErrorUserName("");
      setUserColor("green");
    } else {
      setErrorUserName("Username must be 8 letters long.");
      setUserColor("red");
    }

    if (email.includes("@gmail")) {
      setErrorEmail("");
      setEmailColor("green");
    } else {
      setEmailColor("red");
      setErrorEmail("Email should have @gmail");
    }

    if (password.length > 8) {
      setErrorPassword("");
      setPasswordColor("green");
    } else {
      setErrorPassword("Password should be 8 letters long ");
      setPasswordColor("red");
    }

    if (password != "" && password == confirmPassword) {
      setErrorConfirmPassword("");
      setConfirmPasswordColor("green");
    } else {
      setErrorConfirmPassword("Passwords didn't matched.");
      setConfirmPasswordColor("red");
    }
  }

  return (
    <>
      <div className="card">
        <div className="card-image"></div>

        <form>
          <input
            type="text"
            placeholder="Name"
            style={{ borderColor: userColor }}
            value={username}
            onChange={(e) => setusername(e.target.value)}
          />

          <p className="error">{errorUserName}</p>

          <input
            type="text"
            placeholder="Email"
            style={{ borderColor: emailColor }}
            value={email}
            onChange={(e) => setEmail(e.target.value)}
          />
          <p className="error">{errorEmail}</p>

          <input
            type="password"
            placeholder="Password"
            style={{ borderColor: passwordColor }}
            value={password}
            onChange={(e) => setPassword(e.target.value)}
          />
          <p className="error">{errorPassword}</p>

          <input
            type="password"
            placeholder="Confirm Password"
            style={{ borderColor: confirmPasswordColor }}
            value={confirmPassword}
            onChange={(e) => setConfirmPassword(e.target.value)}
          />
          <p className="error">{errorConfrimPassword}</p>

          <button className="submit-btn" onClick={validate}>
            Submit
          </button>
        </form>
      </div>
    </>
  );
}

export default Form;

```

<h1  align="center" >🌽 𝓬𝓼𝓼 🪻</h1>

```css

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  height: 100vh;
  background-image: linear-gradient(to right, #fff7c8 0%, #fa709a 100%);
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  background: #f3fffe;
  display: grid;
  grid-template-columns: 1fr 1fr;
  width: 50rem;
  height: 30rem;
  box-shadow: 0.5px 0.5px 1px 1px rgb(255, 255, 223);
}

.card-image {
  background: url("https://images.unsplash.com/photo-1540979388789-6cee28a1cdc9?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=387&q=80");
  background-position: center;
  background-size: cover;
}

form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

input {
  padding: 10px 10px;
  margin: 5px;
  width: 20rem;
  background: transparent;
  border: none;
  border-bottom: 1px solid #ccc;
  outline: none;
}

.error {
  font-family: sans-serif;
  color: red;
}

.submit-btn {
  width: 80%;
  margin-top: 20px;
  padding: 10px 20px;
  background: transparent;
  background: rgb(255, 90, 123);
  cursor: pointer;
  border: none;
  color: #fff;
  font-weight: bold;
}

```
