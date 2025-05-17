<h1  align="center" > 🍄 𝐂ⱺ𐓣𝗍𝗋ⱺᥣᥣ𝖾ᑯ 𝗏𝗌 𝐔𐓣𝖼ⱺ𐓣𝗍𝗋ⱺᥣᥣ𝖾ᑯ 𝐂ⱺꭑρⱺ𐓣𝖾𐓣𝗍𝗌 🥠</h1>

<h3  align="center" > 🍄 𝐔𐓣𝖼ⱺ𐓣𝗍𝗋ⱺᥣᥣ𝖾ᑯ 𝐅ⱺ𝗋ꭑ 🥠</h3>

```JSX
//============ ⚛️App.tsx ==============

import UncontrolledForm from "./components/UncontrolledForm";

const App = () => {
  return (
    <div>
      <UncontrolledForm />
    </div>
  );
};

export default App;

```

</br>

```JSX
//======== 🗂️components/⚛️UncontrolledForm.tsx ========

import { useRef, FormEvent } from "react";

const UncontrolledForm = () => {
  const nameInput = useRef<HTMLInputElement>(null);
  const ageInput = useRef<HTMLInputElement>(null);
  const hairColorInput = useRef<HTMLInputElement>(null);

  const handleSubmit = (e: FormEvent<HTMLFormElement>): void => {
    e.preventDefault();
    if (nameInput.current && ageInput.current && hairColorInput.current) {
      console.log(nameInput.current.value);
      console.log(ageInput.current.value);
      console.log(hairColorInput.current.value);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        className="border"
        type="text"
        name="name"
        placeholder="Name"
        ref={nameInput}
      />
      <input
        className="border"
        type="number"
        name="age"
        placeholder="Age"
        ref={ageInput}
      />
      <input
        className="border"
        type="text"
        name="hairColor"
        placeholder="Hair Color"
        ref={hairColorInput}
      />
      <input type="submit" name="submit" placeholder="Submit" />
    </form>
  );
};

export default UncontrolledForm;

```

</br>

<h3  align="center" > 🍄 𝐂ⱺ𐓣𝗍𝗋ⱺᥣᥣ𝖾ᑯ 𝐅ⱺ𝗋ꭑ 🥠</h3>

```JSX
//============ ⚛️App.tsx ==============

import ControlledForm from "./components/ControlledForm";

const App = () => {
  return (
    <div>
      <ControlledForm />
    </div>
  );
};

export default App;

```

</br>

```JSX
//======== 🗂️components/⚛️ControlledForm.tsx ========

import { useState, useEffect } from "react";

const ControlledForm = () => {
  const [name, setName] = useState("");
  const [age, setAge] = useState<number | string>("");
  const [hairColor, setHairColor] = useState("");
  const [nameInputError, setNameInputError] = useState("");

  useEffect(() => {
    if (name.length < 2) {
      setNameInputError("Name must be at least 2 characters or long");
    } else {
      setNameInputError("");
    }
  }, [name]);

  return (
    <form>
      {nameInputError && <p className="text-red-500">{nameInputError}</p>}
      <input
        type="text"
        name="name"
        placeholder="Name"
        value={name}
        onChange={(e) => setName(e.target.value)}
        className="border m-2"
      />
      <input
        type="number"
        name="age"
        placeholder="Age"
        value={age}
        onChange={(e) => setAge(Number(e.target.value))}
        className="border m-2"
      />
      <input
        type="text"
        name="hairColor"
        placeholder="Hair Color"
        value={hairColor}
        onChange={(e) => setHairColor(e.target.value)}
        className="border m-2"
      />

      <button>Submit</button>
    </form>
  );
};

export default ControlledForm;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Challenge: Build a Form with Controlled and Uncontrolled Components

#### **Task:**

Create a simple form with the following fields:

- **First Name** (Text input)
- **Last Name** (Text input)
- **Email** (Email input)
- **Subscribe to newsletter** (Checkbox)
- **Message** (Textarea)

You are required to create two versions of the form:

1. **Controlled Components**: Where the form fields are managed by React state.
2. **Uncontrolled Components**: Where the form fields are managed by the DOM, and React doesn’t directly track the value of each input.

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

</br>

```JSX
//============ ⚛️App.tsx ==============

import ControlledForm from "./components/ControlledForm";
import UncontrolledForm from "./components/UnControlledForm";

const App = () => {
  return (
    <div>
      <ControlledForm />
      <UncontrolledForm />
    </div>
  );
};
export default App;

```

</br>

```JSX
//============ 🗂️components/⚛️ControlledForm.tsx ==============

import { useState } from "react";

function ControlledForm() {
  const [formData, setFormData] = useState({
    firstName: "",
    lastName: "",
    email: "",
    subscribe: false,
    message: "",
  });

  const handleChange = (e: any) => {
    const { name, value, type, checked } = e.target;
    setFormData((prevData) => ({
      ...prevData,
      [name]: type === "checkbox" ? checked : value,
    }));
  };

  const handleSubmit = (e: any) => {
    e.preventDefault();
    console.log(formData);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        name="firstName"
        value={formData.firstName}
        onChange={handleChange}
        placeholder="First Name"
      />
      <input
        type="text"
        name="lastName"
        value={formData.lastName}
        onChange={handleChange}
        placeholder="Last Name"
      />
      <input
        type="email"
        name="email"
        value={formData.email}
        onChange={handleChange}
        placeholder="Email"
      />
      <label>
        <input
          type="checkbox"
          name="subscribe"
          checked={formData.subscribe}
          onChange={handleChange}
        />
        Subscribe to Newsletter
      </label>
      <textarea
        name="message"
        value={formData.message}
        onChange={handleChange}
        placeholder="Message"
      ></textarea>
      <button type="submit">Submit</button>
    </form>
  );
}

export default ControlledForm;

```

</br>

```JSX
//============ 🗂️components/⚛️UncontrolledForm.tsx ==============

import { useRef } from "react";

interface FormData {
  firstName: string;
  lastName: string;
  email: string;
  subscribe: boolean;
  message: string;
}

function UncontrolledForm() {
  const firstNameRef = useRef<HTMLInputElement>(null);
  const lastNameRef = useRef<HTMLInputElement>(null);
  const emailRef = useRef<HTMLInputElement>(null);
  const subscribeRef = useRef<HTMLInputElement>(null);
  const messageRef = useRef<HTMLTextAreaElement>(null);

  const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault();

    const formData: FormData = {
      firstName: firstNameRef.current?.value ?? "",
      lastName: lastNameRef.current?.value ?? "",
      email: emailRef.current?.value ?? "",
      subscribe: subscribeRef.current?.checked ?? false,
      message: messageRef.current?.value ?? "",
    };

    console.log(formData);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input ref={firstNameRef} type="text" placeholder="First Name" />
      <input ref={lastNameRef} type="text" placeholder="Last Name" />
      <input ref={emailRef} type="email" placeholder="Email" />
      <label>
        <input ref={subscribeRef} type="checkbox" />
        Subscribe to Newsletter
      </label>
      <textarea ref={messageRef} placeholder="Message"></textarea>
      <button type="submit">Submit</button>
    </form>
  );
}

export default UncontrolledForm;

```
