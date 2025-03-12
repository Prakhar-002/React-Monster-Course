
<h2  align="center" > 🕍 𝐓ⱺᑯⱺ 𝐋𝗂𝗌𝗍 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/2b698611-49bd-4229-b941-5b2b5b6a8689" width="700px" height="621px"/>

</h1>

</br>

```TS

//============ store.ts ============== 

import { create } from "zustand";

interface Todo {
  id: number;
  text: string;
  completed: boolean;
}

interface TodoStore {
  todos: Todo[];
  addTodo: (todo: Todo) => void;
  removeTodo: (id: number) => void;
  toggleTodo: (id: number) => void;
}

const useStore = create<TodoStore>((set) => ({
  todos: [],
  addTodo: (todo) =>
    set((state) => ({
      todos: [...state.todos, todo],
    })),

  removeTodo: (id) =>
    set((state) => ({
      todos: state.todos.filter((todo) => todo.id !== id),
    })),
  toggleTodo: (id) =>
    set((state) => ({
      todos: state.todos.map((todo) =>
        todo.id === id ? { ...todo, completed: !todo.completed } : todo
      ),
    })),
}));

export default useStore;

```

```TSX

//============ App.tsx ============== 

import TodoList from "./components/TodoList";

const App = () => {
  return (
    <div>
      <TodoList />
    </div>
  );
};

export default App;

```

```TSX

//============ components/TodoList.tsx ============== 

import { useState } from "react";
import useStore from "../store";

function TodoList() {
  const { todos, addTodo, removeTodo, toggleTodo } = useStore();
  const [inputValue, setInputValue] = useState("");

  const handleAddTodo = () => {
    if (inputValue.trim() === "") return;
    addTodo({
      id: Date.now(),
      text: inputValue,
      completed: false,
    });
    setInputValue("");
  };


  return (
    <div className="min-h-screen flex items-center justify-center bg-gradient-to-br from-orange-400 via-pink-500 to-purple-600">
      <div className="bg-white/90 backdrop-blur-lg p-6 rounded-2xl shadow-2xl w-full max-w-md">
        <h1 className="text-3xl font-extrabold text-center text-gray-800 mb-6">
          🌅 My To-Do List
        </h1>

        {/* Input & Add Button */}
        <div className="flex items-center mb-4">
          <input
            type="text"
            value={inputValue}
            onChange={(e) => setInputValue(e.target.value)}
            placeholder="What's next?"
            className="flex-grow px-4 py-3 rounded-l-xl border border-gray-300 focus:outline-none focus:ring-2 focus:ring-pink-500 shadow-sm text-gray-700"
          />

          <button
            onClick={handleAddTodo}
            className="bg-gradient-to-r from-pink-500 to-red-500 text-white px-4 py-3 rounded-r-xl hover:from-pink-600 hover:to-red-600 transition duration-300 focus:outline-none focus:ring-2 focus:ring-pink-500"
          >
            ➕ Add
          </button>
        </div>

        {/* To-Do List */}
        <ul className="space-y-4">
          {todos.map((todo) => (
            <li key={todo.id}
              className="flex items-center justify-between bg-white/80 p-4 rounded-xl shadow-md border-l-4 border-pink-500 transition-all"
            >
              <div className="flex items-center">
                <input
                  type="checkbox"
                  checked={todo.completed}
                  onChange={() => toggleTodo(todo.id)}
                  className="mr-3 h-5 w-5 accent-pink-500 focus:ring-pink-500 rounded-lg"
                />

                <span
                  className={`text-lg font-medium ${todo.completed ?
                    "line-through text-gray-400"
                    : "text-gray-900"
                    }`}
                >
                  {todo.text}
                </span>
              </div>

              <button
                onClick={() => removeTodo(todo.id)}
                className="text-red-500 hover:text-red-700 transition duration-300 focus:outline-none focus:ring-2 focus:ring-red-500"
              >
                🗑 Delete
              </button>
            </li>
          ))}
        </ul>
      </div>
    </div>
  );

}

export default TodoList;

```