<h1  align="center" > 🍄 𝐇𝐎𝐂 🥠</h1>

<h3  align="center" > 🍄 𝐇𝐎𝐂 🥠</h3>

```JSX
//============ ⚛️App.tsx ==============

import { printProps } from "./utils/printProps";
import TodoList from "./components/TodoList";

const TodoListWrapped = printProps(TodoList);

const App = () => {
  return (
    <div>
      <TodoListWrapped a={1} b="hello" c={{ name: "huxn" }} />
    </div>
  );
};

export default App;

```

</br>

```JSX
//======== 🗂️components/⚛️TodoList.tsx ========

interface Todo {
  id: number;
  title: string;
  body: string;
}

interface TodoListProps {
  todo: Todo | null;
}

const TodoList = ({ todo }: TodoListProps) => {
  const { id, title } = todo || {};

  return todo ? (
    <div>
      <p>
        <strong>Todo ID:</strong> {id}
      </p>
      <h1>
        <strong>Todo Title:</strong> {title}
      </h1>
    </div>
  ) : (
    <p>Loading...</p>
  );
};

export default TodoList;

```

</br>

```JSX
//======== 🗂️utils/⚛️printProps.tsx ========

export const printProps = (Component: any) => {
  return (props: any) => {
    console.log(props);
    return <Component {...props} />;
  };
};

```

</br>


<h3  align="center" > 🍄 With Loading 🥠</h3>

```JSX
//============ ⚛️App.tsx ==============

import { useEffect, useState } from "react";
import withLoading from "./utils/withLoading";
import MyComponent from "./components/MyComponent";

const MyComponentWithLoading = withLoading(MyComponent);

function App() {
  const [isLoading, setIsLoading] = useState(true);
  const [data, setData] = useState("");

  useEffect(() => {
    setTimeout(() => {
      setData("Data fetched!");
      setIsLoading(false);
    }, 2000);
  }, []);

  return <MyComponentWithLoading isLoading={isLoading} data={data} />;
}

export default App;

```

</br>

```JSX
//======== 🗂️components/⚛️MyComponent.tsx ========

const MyComponent = ({ data }: any) => {
  return <div>{data}</div>;
};

export default MyComponent;

```

</br>

```JSX
//======== 🗂️utils/⚛️withLoading.tsx ========

import React from "react";

interface WithLoadingProps {
  isLoading: boolean;
  [key: string]: any;
}

const withLoading = <P extends object>(
  WrappedComponent: React.ComponentType<P>
) => {
  return function WithLoading({ isLoading, ...props }: WithLoadingProps & P) {
    if (isLoading) {
      return <div>Loading...</div>;
    }
    return <WrappedComponent {...(props as P)} />;
  };
};

export default withLoading;

```

</br>

<h3  align="center" > 🍄 Fetching Data With HOC 🥠</h3>

```JSX
//============ ⚛️App.tsx ==============

import TodoList from "./components/TodoList";
import { withTodo } from "./utils/withTodo";

const TodoListWrapper = withTodo(TodoList, "2");

const App = () => {
  return (
    <div>
      <TodoListWrapper />
    </div>
  );
};

export default App;

```

</br>

```JSX
//======== 🗂️components/⚛️TodoList.tsx ========

interface Todo {
  id: number;
  title: string;
  body: string;
}

interface TodoListProps {
  todo: Todo | null;
}

const TodoList = ({ todo }: TodoListProps) => {
  const { id, title } = todo || {};

  return todo ? (
    <div>
      <p>
        <strong>Todo ID:</strong> {id}
      </p>
      <h1>
        <strong>Todo Title:</strong> {title}
      </h1>
    </div>
  ) : (
    <p>Loading...</p>
  );
};

export default TodoList;

```

</br>

```JSX
//======== 🗂️utils/⚛️withTodo.tsx ========

import axios from "axios";
import { useEffect, useState } from "react";

export const withTodo = (Component: any, todoId: string) => {
  return (props: any) => {
    const [todo, setTodo] = useState(null);

    useEffect(() => {
      (async () => {
        const response = await axios.get(
          `https://jsonplaceholder.typicode.com/todos/${todoId}`
        );
        setTodo(response.data);
      })();
    }, []);

    return <Component {...props} todo={todo} />;
  };
};

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### Challenge: **Create a HOC for Access Control and Dynamic Prop Injection**

You need to implement an HOC that does two things:

1. **Access Control**: The HOC should accept a `roles` prop, which is an array of allowed roles. The HOC should check if the user has the required roles, and if not, it should display a fallback component (like a "Not Authorized" message or redirect to a different page).
2. **Dynamic Prop Injection**: The HOC should also be able to inject dynamic props into the wrapped component based on conditions. For example, based on the user's role, the HOC should inject additional props into the wrapped component (e.g., special content or features based on role).

#### Requirements:

- You need to define the types for the component's props and the HOC in TypeScript.
- The HOC should be flexible to handle any type of component, with the ability to inject custom props.
- Handle default props and dynamic prop injection based on roles.
- Make sure that TypeScript ensures proper type safety throughout the code.
- Implement the `roles` prop properly, ensuring that the injected component only renders for users with the correct roles.

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

</br>

```JSX
//============ ⚛️App.tsx ==============

import { withAccessControl } from "./utils/withAccessControl";
import NotAuthorized from "./components/NotAuthorized";
import MyComponent from "./components/MyComponent";

const MyComponentWithAccessControl = withAccessControl(MyComponent);

const App = () => {
  return (
    <div>
      <MyComponentWithAccessControl
        roles={["admin", "manager"]}
        // roles={["user", "guest"]}
        fallbackComponent={NotAuthorized}
        message="Hello, Admin!"
        injectedProps={{
          userName: "John Doe",
          userPermissions: ["view_dashboard", "edit_settings"],
        }}
      />
    </div>
  );
};

export default App;

```

</br>

```JSX
//============ 🗂️components/⚛️MyComponent.tsx ==============

import { WrappedComponentProps } from "../types/access-control.types";

const MyComponent = ({
  message,
  userName,
  userPermissions,
}: WrappedComponentProps) => {
  return (
    <div>
      <h1>{message}</h1>
      <p>Welcome, {userName}</p>
      <p>Your permissions: {userPermissions?.join(", ")}</p>
    </div>
  );
};

export default MyComponent;

```

</br>

```JSX
//============ 🗂️components/⚛️NotAuthorized.tsx ==============

const NotAuthorized = () => (
  <div>You are not authorized to view this content.</div>
);

export default NotAuthorized;

```

</br>

```JSX
//============ 🗂️utils/⚛️withAccessControl.tsx ==============

import { ComponentType } from "react";
import {
  AccessControlProps,
  InjectedProps,
} from "../types/access-control.types";

const currentUserRole = "admin";

export const withAccessControl = <P extends object>(
  WrappedComponent: ComponentType<P & InjectedProps>
) => {
  return (props: P & AccessControlProps) => {
    const {
      roles,
      fallbackComponent: Fallback,
      injectedProps = {},
      ...restProps
    } = props;

    const hasAccess = roles.includes(currentUserRole);

    if (!hasAccess) {
      return <Fallback />;
    }

    const mergedProps = {
      ...restProps,
      ...injectedProps,
    };

    return <WrappedComponent {...(mergedProps as P & InjectedProps)} />;
  };
};

```

</br>

```JSX
//============ 🗂️types/⚛️ access-control.types.ts ==============

import React from "react";

export interface AccessControlProps {
  roles: string[];
  fallbackComponent: React.ComponentType;
  injectedProps?: { [key: string]: any };
}

export interface InjectedProps {
  userName?: string;
  userPermissions?: string[];
}

export interface WrappedComponentProps extends InjectedProps {
  message: string;
}

```
