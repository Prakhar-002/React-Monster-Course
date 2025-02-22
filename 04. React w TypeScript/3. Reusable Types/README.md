
<h1  align="center" > 🍄 𝐑𝖾υ𝗌αᑲᥣ𝖾 𝐓𝗒ρ𝖾𝗌 🥠</h1>

<h2  align="center" > 🍄 1. 𝐖𝗂𝗍ɦⱺυ𝗍 𝐑𝖾υ𝗌αᑲᥣ𝖾 𝐓𝗒ρ𝖾𝗌 🥠</h2>

```TSX

//============ App.tsx ============== 

import AdminInfo from "@/components/AdminInfo";
import UsersInfo from "@/components/UserInfo";

export default function Home() {
  return (
    <>
      <h1>Users Info 👇</h1>
      <UsersInfo
        username="Alex"
        email="alex@gmail.com"
        age={20}
        location={["Earth", "USA"]}
      />

      <h1>Admin Info 👇</h1>
      <AdminInfo
        username="Alex"
        email="alex@gmail.com"
        age={20}
        location={["Mars", "Unknown"]}
        admin="yes"
      />
    </>
  );
}

```

```TSX

//============ components/AdminInfo.tsx ============== 

type AInfo = {
  username: string;
  email: string;
  age: number;
  location: string[];
  // We just wanna add this extra type
  admin: string;
};

const AdminInfo = ({ username, email, age, location, admin }: AInfo) => {
  return (
    <ul>
      <li>{username}</li>
      <li>{email}</li>
      <li>{age}</li>
      <li>{JSON.stringify(location)}</li>
      <li>{admin}</li>
    </ul>
  );
};

export default AdminInfo;

```

```TSX

//============ components/UsersInfo.tsx ============== 

type Info = {
  username: string;
  email: string;
  age: number;
  location: string[];
};

const UsersInfo = ({ username, email, age, location }: Info) => {
  return (
    <ul>
      <li>{username}</li>
      <li>{email}</li>
      <li>{age}</li>
      <li>{JSON.stringify(location)}</li>
    </ul>
  );
};

export default UsersInfo;

```

<h2  align="center" > 🍄 2. 𝐖𝗂𝗍ɦ 𝐑𝖾υ𝗌αᑲᥣ𝖾 𝐓𝗒ρ𝖾𝗌 🥠</h2>

```TSX

//============ App.tsx ============== 

import AdminInfo from "@/components/AdminInfo";
import UsersInfo from "@/components/UserInfo";

export default function Home() {
  return (
    <>
      <h1>Users Info 👇</h1>
      <UsersInfo
        username="Alex"
        email="alex@gmail.com"
        age={20}
        location={["Earth", "USA"]}
      />

      <h1>Admin Info 👇</h1>
      <AdminInfo
        username="Alex"
        email="alex@gmail.com"
        age={20}
        location={["Mars", "Unknown"]}
        admin="yes"
      />
    </>
  );
}

```

```TSX

//============ components/AdminInfo.tsx ============== 

import { type Info } from "./UserInfo";

type AdminInfoList = Info & {
  admin: string;
};

const AdminInfo = ({
  username,
  email,
  age,
  location,
  admin,
}: AdminInfoList) => {
  return (
    <ul>
      <li>{username}</li>
      <li>{email}</li>
      <li>{age}</li>
      <li>{JSON.stringify(location)}</li>
      <li>{admin}</li>
    </ul>
  );
};

export default AdminInfo;

```

```TSX

//============ components/UsersInfo.tsx ============== 

export type Info = {
  username: string;
  email: string;
  age: number;
  location: string[];
};

const UsersInfo = ({ username, email, age, location }: Info) => {
  return (
    <ul>
      <li>{username}</li>
      <li>{email}</li>
      <li>{age}</li>
      <li>{JSON.stringify(location)}</li>
    </ul>
  );
};

export default UsersInfo;

```


</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

# Reusable Props Typing

## Objective

In this exercise, you'll practice creating reusable prop types in TypeScript. You will define a set of reusable props for different types of user information and then apply them to multiple React components.

### Step 1: Define Reusable Types

1. **Create a file named `types.ts` in the `src` directory.**

2. **Define a base `Info` type and an extended `AdminInfoList` type in `types.ts`:**

   - **`Info` Type**: This type represents the base information shared by all users. It includes essential properties that any user will have like (id, name, email).

### Step 2: Create `UserInfo` Component

1. **Create a new file named `UserInfo.tsx` in the `src` directory.**

2. **Create a `UserInfo` component that displays user information based on the `Info` type:**

### Step 3: Create `AdminInfo` Component

1. **Create a new file named `AdminInfo.tsx` in the `src` directory.**

2. **Create an `AdminInfo` component that displays user information and additional admin details based on the `AdminInfoList` type:**

### Step 5: Use the Components in `App`

1. **Open `App.tsx` (or create a new component if you prefer).**

2. **Import and use the `UserInfo` and `AdminInfo` components, passing the appropriate props**

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

```TSX

//============ App.tsx ============== 

import UserInfo from "./components/UserInfo";
import AdminInfo from "./components/AdminInfo";
import { Info, AdminInfoList } from "./types";

const App = () => {
  const user: Info = {
    id: 1,
    name: "John Doe",
    email: "john@example.com",
  };

  const admin: AdminInfoList = {
    id: 2,
    name: "Jane Smith",
    email: "jane@example.com",
    role: "admin",
    lastLogin: new Date(),
  };

  return (
    <div>
      <UserInfo user={user} />
      <AdminInfo admin={admin} />
    </div>
  );
}

export default App;

```

```TS

//============ Info.ts ============== 

type Info = {
  id: number;
  name: string;
  email: string;
};

type AdminInfoList = Info & {
  role: string;
  lastLogin: Date;
};

export { type Info, type AdminInfoList };

```

```TSX

//============ components/AdminInfoProps.tsx ============== 

import React from "react";
import { AdminInfoList } from "../types";

type AdminInfoProps = {
  admin: AdminInfoList;
};

const AdminInfo: React.FC<AdminInfoProps> = ({ admin }) => {
  return (
    <div>
      <h2>Admin Information</h2>
      <p>ID: {admin.id}</p>
      <p>Name: {admin.name}</p>
      <p>Email: {admin.email}</p>
      <p>Role: {admin.role}</p>
      <p>Last Login: {admin.lastLogin.toLocaleString()}</p>
    </div>
  );
};

export default AdminInfo;

```

```TSX

//============ components/UserInfoProps.tsx ============== 

import React from "react";
import { Info } from "../types";

type UserInfoProps = {
  user: Info;
};

const UserInfo: React.FC<UserInfoProps> = ({ user }) => {
  return (
    <div>
      <h2>User Information</h2>
      <p>ID: {user.id}</p>
      <p>Name: {user.name}</p>
      <p>Email: {user.email}</p>
    </div>
  );
};

export default UserInfo;

```