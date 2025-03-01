
<h1  align="center" > 🍄 𝐀𝖼𝗍𝗂ⱺ𐓣𝗌 🥠</h1>

React 19 introduces Actions, which are asynchronous
functions designed to simplify form submissions. Actions
can be utilized on both the client and server sides.

```JSX

//============ App.jsx ============== 

import Form from "./component/Form";

const App = () => {
  return (
    <div>
      <Form />
    </div>
  );
};

export default App;

```

```JSX

//============ Components/Form.jsx ============== 

const Form = () => {
  const formAction = (formData) => {
    const userData = {
      name: formData.get("name"),
      email: formData.get("email"),
      password: formData.get("password"),
    };

    console.log(userData);
  };

  return (
    <form action={formAction}>
      <label htmlFor="name">Name:</label>
      <input
        className="border-2 border-black rounded"
        type="text"
        id="name"
        name="name"
      />{" "}
      <br />
      <label htmlFor="email">Email:</label>
      <input
        className="border-2 border-black rounded"
        type="email"
        id="email"
        name="email"
      />{" "}
      <br />
      <label htmlFor="password">Password:</label>
      <input
        className="border-2 border-black rounded"
        type="password"
        id="password"
        name="password"
      />
      <br />
      <button type="submit" className="bg-black text-white px-4 py-2 mt-3">
        Submit
      </button>
    </form>
  );
};

export default Form;

```