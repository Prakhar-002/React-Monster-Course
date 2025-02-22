
<h1  align="center" > 🍄 𝐀ᥣ𝗍𝖾𝗋𐓣α𝗍𝗂𝗏𝖾 𝐖α𝗒 🥠</h1>

```TSX

//============ App.jsx ============== 

import User from "@/components/User";

export default function Home() {
  return (
    <section>
      <User name="alex" age={20} isStudent={false} />
    </section>
  );
}

```

```TSX

//============ components/User.jsx ============== 

import { FC } from "react";

interface Shape {
  name: string;
  age: number;
  isStudent: boolean;
}

const User: FC<Shape> = ({ name, age, isStudent }) => {
  return (
    <article>
      <h1>{name}</h1>
      <h1>{age}</h1>
      <h1>{isStudent}</h1>
    </article>
  );
};

export default User;

```
