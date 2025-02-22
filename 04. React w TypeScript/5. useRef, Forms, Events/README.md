
<h1  align="center" > 🍄 υ𝗌𝖾𝐑𝖾𝖿, 𝐅ⱺ𝗋ꭑ𝗌, 𝐄𝗏𝖾𐓣𝗍𝗌 🥠</h1>

```TSX

//============ App.tsx ============== 

import Form from "@/components/Form";

export default function Home() {
  return (
    <>
      <Form />
    </>
  );
}

```

```TSX

//============ components/Form.tsx ============== 

"use client";

import { useRef, type FormEvent, useState } from "react";

type formData = {
  name: string;
  email: string;
  password: string;
};

const Form = () => {
  const [submittedData, setSubmittedData] = useState<formData>({
    name: "",
    email: "",
    password: "",
  });

  const name = useRef<HTMLInputElement>(null);
  const email = useRef<HTMLInputElement>(null);
  const password = useRef<HTMLInputElement>(null);

  const handleSubmit = (event: FormEvent<HTMLFormElement>) => {
    event.preventDefault();

    const nameVal = name.current!.value;
    const emailVal = email.current!.value;
    const passwordVal = password.current!.value;

    setSubmittedData({
      name: nameVal,
      email: emailVal,
      password: passwordVal,
    });

    console.log(nameVal);
    console.log(emailVal);
    console.log(passwordVal);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" placeholder="Enter your name" ref={name} />
      <input type="email" placeholder="Enter your email" ref={email} />
      <input type="password" placeholder="Enter your password" ref={password} />
      <button type="submit">Submit</button>

      <section>
        <h1>Name: {submittedData.name}</h1>
        <h1>Email: {submittedData.email}</h1>
        <h1>Password: {submittedData.password}</h1>
      </section>
    </form>
  );
};

export default Form;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

# Typing `useRef`, Forms, and Events

## Objective

In this exercise, you'll practice typing React hooks such as `useRef`, handling forms, and typing events in TypeScript. You will create components that utilize these concepts with proper type annotations.

## Instructions

### Step 1: Typing `useRef`

1. Create a file named `FocusInput.tsx` in the `src` directory.

2. Define a component that uses `useRef` to focus an input field when a button is clicked. Type the ref appropriately.

### Step 2: Typing Forms

1. Create a file named `ContactForm.tsx` in the `src` directory.

2. Define a form component with typed state and form handlers.

### Step 3: Typing Events

1. Create a file named `EventHandling.tsx` in the `src` directory.

2. Define a component that demonstrates typing different event handlers.

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```TSX

//============ App.tsx ============== 

import ContactForm from "./components/ContactForm";
import EventHandling from "./components/EventHandling";
import FocusInput from "./components/FocusInput";

const App: React.FC = () => {
  return (
    <div>
      <FocusInput />
      <ContactForm />
      <EventHandling />
    </div>
  );
};

export default App;

```

```TSX

//============ components/ContactForm.tsx ============== 

import { useState } from "react";

interface ContactFormState {
  name: string;
  email: string;
}

const ContactForm = () => {
  const [formData, setFormData] = useState<ContactFormState>({
    name: "",
    email: "",
  });

  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    const { name, value } = e.target;
    setFormData((prevState) => ({ ...prevState, [name]: value }));
  };

  const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    console.log("Form submitted:", formData);
    // Handle form submission (e.g., send data to an API)
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label>
          Name:
          <input
            type="text"
            name="name"
            value={formData.name}
            onChange={handleChange}
          />
        </label>
      </div>
      <div>
        <label>
          Email:
          <input
            type="email"
            name="email"
            value={formData.email}
            onChange={handleChange}
          />
        </label>
      </div>
      <button type="submit">Submit</button>
    </form>
  );
};

export default ContactForm;

```

```TSX

//============ components/EventHandling.tsx ============== 

const EventHandling = () => {
  const handleClick = (e: React.MouseEvent<HTMLButtonElement>) => {
    console.log("Button clicked!", e.currentTarget);
  };

  const handleMouseEnter = (e: React.MouseEvent<HTMLDivElement>) => {
    console.log("Mouse entered!", e.currentTarget);
  };

  return (
    <div onMouseEnter={handleMouseEnter}>
      <h2>Event Handling Example</h2>
      <button onClick={handleClick}>Click Me!</button>
    </div>
  );
};

export default EventHandling;

```

```TSX

//============ components/FocusInput.tsx ============== 

import { useRef } from "react";

const FocusInput = () => {
  const inputRef = useRef<HTMLInputElement>(null);

  const handleFocus = () => {
    inputRef.current?.focus();
  };

  return (
    <div>
      <input
        type="text"
        ref={inputRef}
        placeholder="Click the button to focus me"
      />
      <button onClick={handleFocus}>Focus Input</button>
    </div>
  );
};

export default FocusInput;

```