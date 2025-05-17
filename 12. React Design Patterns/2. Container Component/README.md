
<h1  align="center" > 🍄 𝐂ⱺ𐓣𝗍α𝗂𐓣𝖾𝗋 𝐂ⱺꭑρⱺ𐓣𝖾𐓣𝗍 🥠</h1>

<h3  align="center" > 🍄 𝐍ⱺ𝗍 𝐒ⱺ 𝐆ⱺⱺᑯ 𝐂ⱺᑯ𝖾 🥠</h3>

``` JSX
//============ ⚛️App.tsx ============== 

import TodoList from "./components/Details/TodoList";
import SingleTodoLoader from "./components/shared/SingleTodoLoader";

const App = () => {
  return (
    <div>
      <SingleTodoLoader>
        <TodoList />
      </SingleTodoLoader>
    </div>
  );
};

export default App;

```

</br>

``` JSX
//======== 🗂️components/🗂️shared/⚛️SingleTodoLoader.tsx ========

import React, { useEffect, useState, ReactNode } from "react";
import axios from "axios";

interface Todo {
  id: number;
  title: string;
  completed: string;
}

interface SingleTodoLoaderProps {
  children: ReactNode;
}

interface ChildComponentProps {
  todos: Todo | null;
}

const SingleTodoLoader = ({ children }: SingleTodoLoaderProps) => {
  const [todos, setTodos] = useState<Todo | null>(null);

  useEffect(() => {
    (async () => {
      const response = await axios.get<Todo>(
        "https://jsonplaceholder.typicode.com/todos/1"
      );
      setTodos(response.data);
    })();
  }, []);

  return (
    <>
      {React.Children.map(children, (child) => {
        if (React.isValidElement<ChildComponentProps>(child)) {
          return React.cloneElement(child, {
            todos,
          });
        }
        return child;
      })}
    </>
  );
};

export default SingleTodoLoader;

```

</br>

``` JSX
//======== 🗂️components/🗂️details/⚛️TodoList.tsx ========

interface Todo {
  id: number;
  title: string;
  completed: string;
}

interface TodoListProps {
  todos: Todo | null;
}

const TodoList = ({ todos }: TodoListProps) => {
  const { id, title } = todos || {};

  return todos ? (
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

<h3  align="center" > 🍄 𝐑𝖾𝖿α𝖼𝗍ⱺ𝗋 1 🥠</h3>

``` JSX
//============ ⚛️App.tsx ============== 

import TodoList from "./components/Details/TodoList";
import SingleTodoLoader from "./components/shared/SingleTodoLoader";

const App = () => {
  return (
    <div>
      <SingleTodoLoader todoId="1">
        <TodoList />
      </SingleTodoLoader>
      <br />

      <SingleTodoLoader todoId="2">
        <TodoList />
      </SingleTodoLoader>
      <br />

      <SingleTodoLoader todoId="3">
        <TodoList />
      </SingleTodoLoader>
      <br />
    </div>
  );
};

export default App;

```

</br>

``` JSX
//======== 🗂️components/🗂️shared/⚛️SingleTodoLoader.tsx ========

import React, { useEffect, useState, ReactNode } from "react";
import axios from "axios";

interface Todo {
  id: number;
  title: string;
  completed: boolean;
}

interface SingleTodoLoaderProps {
  children: ReactNode;
  todoId: string;
}

interface ChildComponentProps {
  todos: Todo | null;
}

const SingleTodoLoader = ({ todoId, children }: SingleTodoLoaderProps) => {
  const [todo, setTodo] = useState<Todo | null>(null);

  useEffect(() => {
    (async () => {
      const response = await axios.get(
        `https://jsonplaceholder.typicode.com/todos/${todoId}`
      );
      setTodo(response.data);
    })();
  }, [todoId]);

  return (
    <>
      {React.Children.map(children, (child) => {
        if (React.isValidElement<ChildComponentProps>(child)) {
          return React.cloneElement(child, {
            todo,
          });
        }
        return child;
      })}
    </>
  );
};

export default SingleTodoLoader;

```

</br>

``` JSX
//======== 🗂️components/🗂️details/⚛️TodoList.tsx ========

interface Todo {
  id: number;
  title: string;
  completed: string;
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

<h3  align="center" > 🍄 𝐑𝖾𝖿α𝖼𝗍ⱺ𝗋 2 🥠</h3>

``` JSX
//============ ⚛️App.tsx ============== 

import CommentsList from "./components/Details/CommentsList";
import TodoList from "./components/Details/TodoList";
import ResourceLoader from "./components/shared/ResourceLoader";

const App = () => {
  return (
    <div>
      <ResourceLoader resourceUrl="/todos/1" resourceName="todo">
        <TodoList />
      </ResourceLoader>

      <hr />
      <br />

      <ResourceLoader resourceUrl="/comments/1" resourceName="comments">
        <CommentsList />
      </ResourceLoader>
    </div>
  );
};

export default App;

```

</br>

``` JSX
//======== 🗂️components/🗂️shared/⚛️ResourceLoader.tsx ========

import React, { useEffect, useState, ReactNode } from "react";
import axios from "axios";

interface ResourceLoaderProps {
  resourceUrl: string;
  resourceName: string;
  children: ReactNode;
}

const ResourceLoader = ({
  resourceUrl,
  resourceName,
  children,
}: ResourceLoaderProps) => {
  const [state, setState] = useState<any>(null);

  useEffect(() => {
    (async () => {
      const response = await axios.get(
        `https://jsonplaceholder.typicode.com/${resourceUrl}`
      );
      setState(response.data);
    })();
  }, [resourceUrl]);

  return (
    <>
      {React.Children.map(children, (child) => {
        if (React.isValidElement(child)) {
          return React.cloneElement(child, {
            [resourceName]: state,
          });
        }
        return child;
      })}
    </>
  );
};

export default ResourceLoader;

```

</br>

``` JSX
//======== 🗂️components/🗂️Details/⚛️TodoList.tsx ========

interface Todo {
  id: number;
  title: string;
  completed: string;
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

``` JSX
//======== 🗂️components/🗂️details/⚛️SingleTodoLoader.tsx ========

interface Comment {
  id: number;
  name: string;
  email: string;
  body: string;
}

interface CommentsListProps {
  comments: Comment | null;
}

const CommentsList = ({ comments }: CommentsListProps) => {
  const { id, name, email, body } = comments || {};

  return comments ? (
    <div>
      <p>
        <strong>Comment ID:</strong> {id}
      </p>
      <h1>
        <strong>Comment Name:</strong> {name}
      </h1>
      <p>
        <strong>Comment Email:</strong> {email}
      </p>
      <p>
        <strong>Comment Body:</strong> {body}
      </p>
    </div>
  ) : (
    <p>Loading...</p>
  );
};

export default CommentsList;

```

</br>

<h3  align="center" > 🍄 𝐑𝖾𝖿α𝖼𝗍ⱺ𝗋 3 🥠</h3>

``` JSX
//============ ⚛️App.tsx ============== 

import axios from "axios";
import DataSource from "./components/shared/DataSource";
import CommentsList from "./components/CommentsList";
import TodoList from "./components/TodoList";

const getServerData = (url: string) => async () => {
  const response = await axios.get(url);
  return response.data;
};

const App = () => {
  return (
    <div>
      <DataSource
        getDataFunc={getServerData(
          "https://jsonplaceholder.typicode.com/todos/1"
        )}
        resourceName="todo"
      >
        <TodoList />
      </DataSource>

      <br />

      <DataSource
        getDataFunc={getServerData(
          "https://jsonplaceholder.typicode.com/comments/1"
        )}
        resourceName="comments"
      >
        <CommentsList />
      </DataSource>
    </div>
  );
};

export default App;

```

</br>

``` JSX
//======== 🗂️components/🗂️shared/⚛️DataSource.tsx ========

import React, { useEffect, useState, ReactNode } from "react";

interface DataSourceProps {
  getDataFunc?: () => void;
  resourceName: string;
  children: ReactNode;
}

const DataSource = ({
  getDataFunc = () => {},
  resourceName,
  children,
}: DataSourceProps) => {
  const [state, setState] = useState<any>(null);

  useEffect(() => {
    (async () => {
      const data = await getDataFunc();
      setState(data);
    })();
  }, [getDataFunc]);

  return (
    <>
      {React.Children.map(children, (child) => {
        if (React.isValidElement(child)) {
          return React.cloneElement(child, {
            [resourceName]: state,
          });
        }
        return child;
      })}
    </>
  );
};

export default DataSource;

```

</br>

``` JSX
//======== 🗂️components/⚛️CommentsList.tsx ========

interface Comment {
  id: number;
  name: string;
  email: string;
  body: string;
}

interface CommentsListProps {
  comments: Comment | null;
}

const CommentsList = ({ comments }: CommentsListProps) => {
  const { id, name, email, body } = comments || {};

  return comments ? (
    <div>
      <p>
        <strong>Comment ID:</strong> {id}
      </p>
      <h1>
        <strong>Comment Name:</strong> {name}
      </h1>
      <p>
        <strong>Comment Email:</strong> {email}
      </p>
      <p>
        <strong>Comment Body:</strong> {body}
      </p>
    </div>
  ) : (
    <p>Loading...</p>
  );
};

export default CommentsList;

```

</br>

``` JSX
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
        <strong>Post ID:</strong> {id}
      </p>
      <h1>
        <strong>Post Title:</strong> {title}
      </h1>
    </div>
  ) : (
    <p>Loading...</p>
  );
};

export default TodoList;

```

</br>

<h1  align="center" >📚 𝐀𝗌𝗌𝗂𝗀𐓣ꭑ𝖾𐓣𝗍 🎧 𝚰𐓣𝗌𝗍𝗋υ𝖼𝗍𝗂ⱺ𐓣𝗌 🧋</h1>

### **Container Component Challenge**

Your goal is to implement a reusable data-fetching component in React that can fetch data from an external API and provide it to its child components. This should be done with proper error handling, conditional rendering, and flexibility in how data is passed down to child components.

1. **Create a `DataSource` Component**:  
   This component should take a `getDataFunc` prop that will be used to fetch data. The `getDataFunc` function can be asynchronous and will return the data. The `DataSource` component should manage the state for:

   - The fetched data.
   - An error message in case the data fetch fails.

   The component should:

   - Call `getDataFunc` when it mounts and store the fetched data in the state.
   - Display an error message if the data fetch fails.
   - Pass the fetched data down to its children as a prop.
   - The `resourceName` prop should determine the key for the data passed to the child components.

2. **Create a `ProductList` Component**:  
   This component should accept a `products` prop (an array of products) and render a list of product items. Each product should display:

   - Title
   - Description
   - Price
   - Image

   If the `products` prop is `null` or `undefined`, the component should display a loading message.

3. **Inside the `App` Component**:  
   The `App` component should use the `DataSource` component to fetch data from the external API. Use a function that returns the data-fetching promise (for example, using `axios`) and pass this function to the `DataSource` component.

4. **Use the `DataSource` Component with `ProductList`**:  
   Inside `App`, use the `DataSource` component to fetch data from an API endpoint like `https://fakestoreapi.com/products`. Pass the `products` data to the `ProductList` component as a prop.

</br>

<h1  align="center" >🌽 𝐒ⱺᥣυ𝗍𝗂ⱺ𐓣 🪻</h1>

</br>

``` JSX
//============ ⚛️App.tsx ============== 

import axios from "axios";
import DataSource from "./components/shared/DataSource";
import ProductList from "./components/ProductList";

const getServerData = (url: string) => async () => {
  const response = await axios.get(url);
  return response.data;
};

const App = () => {
  return (
    <div style={{ padding: "20px" }}>
      <h1>Welcome to the Fake Store</h1>

      <DataSource
        getDataFunc={getServerData("https://fakestoreapi.com/products")}
        resourceName="products"
      >
        <ProductList />
      </DataSource>
    </div>
  );
};

export default App;

```

</br>

``` JSX
//============ 🗂️components/🗂️shared/⚛️DataSource.tsx ============== 

import React, { useEffect, useState, ReactNode } from "react";

interface DataSourceProps {
  getDataFunc?: () => void;
  resourceName: string;
  children: ReactNode;
}

const DataSource = ({
  getDataFunc = () => {},
  resourceName,
  children,
}: DataSourceProps) => {
  const [state, setState] = useState<any>(null);
  const [error, setError] = useState<string | null>(null);

  useEffect(() => {
    (async () => {
      try {
        const data = await getDataFunc();
        setState(data);
      } catch (err) {
        setError("Failed to fetch data.");
      }
    })();
  }, [getDataFunc]);

  return (
    <>
      {error ? (
        <p style={{ color: "red" }}>{error}</p>
      ) : (
        React.Children.map(children, (child) => {
          if (React.isValidElement(child)) {
            return React.cloneElement(child, {
              [resourceName]: state,
            });
          }
          return child;
        })
      )}
    </>
  );
};

export default DataSource;

```

</br>

``` JSX
//============ 🗂️components/⚛️ProductList.tsx ============== 

interface Product {
  id: number;
  title: string;
  description: string;
  price: number;
  image: string;
}

interface ProductListProps {
  products: Product[] | null;
}

const ProductList = ({ products }: ProductListProps) => {
  return products ? (
    <div className="product-list-container">
      <ul>
        {products.map((product) => (
          <li key={product.id} className="product-card">
            <h2>{product.title}</h2>
            <p>{product.description}</p>
            <p className="price">${product.price}</p>
            <img src={product.image} alt={product.title} />
          </li>
        ))}
      </ul>
    </div>
  ) : (
    <p className="loading-message">Loading products...</p>
  );
};

export default ProductList;

```
