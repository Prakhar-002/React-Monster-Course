
<h2  align="center" > 🕍 𝐓α𝗌𝗄 𝐋𝗂𝗌𝗍 𝐀ρρ 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/70598d81-dae8-4e3b-b4a5-00dbd24b76c6" width="" height=""/>

</h1>

</br>

```TS

//============ store.ts ============== 

import { create } from "zustand";

interface List {
  name: string;
  emoji: string;
}

interface Workspace {
  name: string;
  emoji: string;
}

interface Todo {
  text: string;
  list: string;
  workspace: string;
}

interface AppState {
  lists: List[];
  workspaces: Workspace[];
  todos: Todo[];
  editIndex: number | null;
  editText: string;
  dropdownIndex: number | null;
  isListModalOpen: boolean;
  isWorkspaceModalOpen: boolean;
  selectedList: string;
  selectedWorkspace: string;
  todoText: string;
  modalName: string;
  modalEmoji: string;
  modalType: "List" | "Workspace" | null;
  addList: (name: string, emoji: string) => void;
  addWorkspace: (name: string, emoji: string) => void;
  addTodo: (todo: Todo) => void;
  updateTodo: (index: number, updatedTodo: Todo) => void;
  deleteTodo: (index: number) => void;
  handleEdit: (index: number) => void;
  handleUpdate: (index: number) => void;
  handleDropdownClick: (index: number) => void;
  setEditText: (text: string) => void;
  setEditIndex: (index: number | null) => void;
  openListModal: () => void;
  closeListModal: () => void;
  openWorkspaceModal: () => void;
  closeWorkspaceModal: () => void;
  setSelectedList: (list: string) => void;
  setSelectedWorkspace: (workspace: string) => void;
  setTodoText: (text: string) => void;
  handleAddTodo: () => void;
  setModalName: (name: string) => void;
  setModalEmoji: (emoji: string) => void;
  setModalType: (type: "List" | "Workspace") => void;
  handleSaveModal: () => void;
}

export const useStore = create<AppState>((set) => ({
  lists: [],
  workspaces: [],
  todos: [],
  editIndex: null,
  editText: "",
  dropdownIndex: null,
  isListModalOpen: false,
  isWorkspaceModalOpen: false,
  selectedList: "",
  selectedWorkspace: "",
  todoText: "",
  modalName: "",
  modalEmoji: "",
  modalType: null,
  addList: (name, emoji) =>
    set((state) => ({
      lists: [...state.lists, { name, emoji }],
    })),
  addWorkspace: (name, emoji) =>
    set((state) => ({
      workspaces: [...state.workspaces, { name, emoji }],
    })),
  addTodo: (todo) =>
    set((state) => ({
      todos: [...state.todos, todo],
    })),
  updateTodo: (index, updatedTodo) =>
    set((state) => {
      const newTodos = [...state.todos];
      newTodos[index] = updatedTodo;
      return {
        todos: newTodos,
        editIndex: null,
        editText: "",
      };
    }),
  deleteTodo: (index) =>
    set((state) => ({
      todos: state.todos.filter((_, i) => i !== index),
      dropdownIndex: null,
    })),
  handleEdit: (index) =>
    set((state) => ({
      editIndex: index,
      editText: state.todos[index].text,
      dropdownIndex: null,
    })),
  handleUpdate: (index) =>
    set((state) => {
      const updatedTodo = {
        ...state.todos[index],
        text: state.editText,
      };
      const newTodos = [...state.todos];
      newTodos[index] = updatedTodo;
      return {
        todos: newTodos,
        editIndex: null,
        editText: "",
      };
    }),
  handleDropdownClick: (index) =>
    set((state) => ({
      dropdownIndex: index === state.dropdownIndex ? null : index,
    })),
  setEditText: (text) => set({ editText: text }),
  setEditIndex: (index) => set({ editIndex: index }),
  openListModal: () => set({ isListModalOpen: true, modalType: "List" }),
  closeListModal: () =>
    set({ isListModalOpen: false, modalName: "", modalEmoji: "" }),
  openWorkspaceModal: () =>
    set({ isWorkspaceModalOpen: true, modalType: "Workspace" }),
  closeWorkspaceModal: () =>
    set({ isWorkspaceModalOpen: false, modalName: "", modalEmoji: "" }),
  setSelectedList: (list) => set({ selectedList: list }),
  setSelectedWorkspace: (workspace) => set({ selectedWorkspace: workspace }),
  setTodoText: (text) => set({ todoText: text }),
  handleAddTodo: () =>
    set((state) => {
      const { todoText, selectedList, selectedWorkspace } = state;
      if (todoText.trim() === "") {
        alert("Todo cannot be empty");
        return state;
      }
      const newTodo = {
        text: todoText,
        list: selectedList,
        workspace: selectedWorkspace,
      };
      return {
        todos: [...state.todos, newTodo],
        todoText: "",
        selectedList: "",
        selectedWorkspace: "",
      };
    }),
  setModalName: (name) => set({ modalName: name }),
  setModalEmoji: (emoji) => set({ modalEmoji: emoji }),
  setModalType: (type) => set({ modalType: type }),
  handleSaveModal: () =>
    set((state) => {
      const { modalName, modalEmoji, modalType } = state;
      if (modalName.trim() === "") return state;

      if (modalType === "List") {
        state.addList(modalName, modalEmoji);
      } else if (modalType === "Workspace") {
        state.addWorkspace(modalName, modalEmoji);
      }

      return {
        modalName: "",
        modalEmoji: "",
        modalType: null,
        isListModalOpen: false,
        isWorkspaceModalOpen: false,
      };
    }),
}));

```

```TSX

//============ App.tsx ============== 

import Sidebar from "./components/Sidebar";
import MainArea from "./components/MainArea";
import Modal from "./components/Modal";
import { useStore } from "./store";
import { MdMoreVert } from "react-icons/md";

function App() {
  const {
    todos,
    editIndex,
    editText,
    dropdownIndex,
    handleEdit,
    handleUpdate,
    handleDropdownClick,
    deleteTodo,
    setEditText,
    setEditIndex,
  } = useStore();

  return (
    <div className="flex h-screen bg-gray-100">
      {/* Sidebar */}
      <Sidebar />

      {/* Main Content */}
      <div className="flex-1 p-6">
        <MainArea />

        {/* Todo List Section */}
        <div className="mt-6 bg-white shadow-md rounded-lg p-6">
          <h2 className="text-2xl font-semibold mb-4 text-gray-800">Todo List</h2>
          <ul className="space-y-3">
            {todos.map((todo, index) => (
              <li key={index} className="bg-gray-50 shadow-sm rounded-lg p-4 flex justify-between items-center hover:bg-gray-100 transition">
                {editIndex === index ? (
                  <div className="flex items-center w-full">
                    <input
                      type="text"
                      value={editText}
                      onChange={(e) => setEditText(e.target.value)}
                      className="flex-1 border border-gray-300 p-2 rounded-lg focus:ring-2 focus:ring-blue-400"
                    />
                    <button
                      onClick={() => handleUpdate(index)}
                      className="ml-2 bg-green-500 text-white px-4 py-2 rounded-lg hover:bg-green-600 transition"
                    >
                      Update
                    </button>
                    <button
                      onClick={() => setEditIndex(null)}
                      className="ml-2 bg-gray-500 text-white px-4 py-2 rounded-lg hover:bg-gray-600 transition"
                    >
                      Cancel
                    </button>
                  </div>
                ) : (
                  <div className="flex justify-between items-center w-full">
                    <div>
                      <strong className="text-gray-800">{todo.text}</strong>
                        <span className="text-gray-500 ml-2">(<b>List</b> : {todo.list}), <b>Workspace</b>: {todo.workspace}</span>
                    </div>
                    <MdMoreVert
                      className="cursor-pointer text-gray-700 hover:text-gray-900 transition"
                      size={24}
                      onClick={() => handleDropdownClick(index)}
                    />
                    {dropdownIndex === index && (
                      <div className="absolute right-0 mt-2 bg-white border rounded-lg shadow-lg w-32">
                        <button
                          onClick={() => handleEdit(index)}
                          className="block px-4 py-2 text-gray-700 hover:bg-gray-100 w-full text-left"
                        >
                          Edit
                        </button>
                        <button
                          onClick={() => deleteTodo(index)}
                          className="block px-4 py-2 text-red-600 hover:bg-red-100 w-full text-left"
                        >
                          Delete
                        </button>
                      </div>
                    )}
                  </div>
                )}
              </li>
            ))}
          </ul>
        </div>
      </div>

      {/* Modal */}
      <Model />
    </div>
  );


}

export default App;

```

```TSX

//============ components/Sidebar.tsx ============== 

import { FaPlus } from "react-icons/fa";
import { useStore } from "../store";

const Sidebar = () => {
  const { lists, workspaces, openListModal, openWorkspaceModal } = useStore();



  return (
    <div className="min-w-72 bg-gray-100 shadow-md flex flex-col p-4">
      <div className="flex-1  overflow-y-auto">
        {/* Lists Section */}
        <h3 className="text-lg font-semibold text-gray-800">Lists</h3>
        <ul className="space-y-2 mt-2">
          {lists.map((list, index) => (
            <li key={index} className="flex items-center p-2 rounded-lg hover:bg-gray-300 bg-gray-200 transition cursor-pointer">
              <span className="mr-2 text-lg">{list.emoji}</span>
              {list.name}
            </li>
          ))}
        </ul>

        <button
          onClick={openListModal}
          className="flex items-center justify-center mt-4 bg-blue-500 text-white py-2 px-4 rounded-lg hover:bg-blue-600 transition"
        >
          <FaPlus className="mr-2" /> New List
        </button>

        {/* Workspaces Section */}
        <h3 className="text-lg font-semibold mt-6 text-gray-800">Workspaces</h3>
        <ul className="space-y-2 mt-2">
          {workspaces.map((workspace, index) => (
            <li key={index} className="flex items-center p-2 rounded-lg hover:bg-gray-300 bg-gray-200 transition cursor-pointer">
              <span className="mr-2 text-lg">{workspace.emoji}</span>
              {workspace.name}
            </li>
          ))}
        </ul>

        <button
          onClick={openWorkspaceModal}
          className="flex items-center justify-center mt-4 bg-green-500 text-white py-2 px-4 rounded-lg hover:bg-green-600 transition"
        >
          <FaPlus className="mr-2" /> New Workspace
        </button>
      </div>
    </div>
  );


};

export default Sidebar;

```

```TSX

//============ components/MainArea.tsx ============== 

import { FaPlus } from "react-icons/fa";
import { useStore } from "../store";

const MainArea = () => {
  const {
    lists,
    workspaces,
    selectedList,
    selectedWorkspace,
    todoText,
    setSelectedList,
    setSelectedWorkspace,
    setTodoText,
    handleAddTodo,
  } = useStore();


  return (
    <div className="flex-1 p-6">
      <div className=" mb-4">
        <input type="text"
          value={todoText}
          onChange={(e) => setTodoText(e.target.value)}
          placeholder="Add A New Todo"
          className=" border border-gray-300 p-2 rounded-lg w-full"
        />


        <div className=" mt-2 flex items-center">
          <select
            value={selectedList}
            onChange={(e) => setSelectedList(e.target.value)}
            className="border border-gray-300 p-2 rounded-lg mr-2 "
          >
            <option value="" disabled>Select List</option>

            {lists.map((list, index) => (
              <option value={list.name} key={index} >
                {list.emoji} {list.name}
              </option>
            ))}
          </select>

          <select
            value={selectedWorkspace}
            onChange={(e) => setSelectedWorkspace(e.target.value)}
            className="border border-gray-300 p-2 rounded-lg"
          >
            <option value="" disabled>Select Workspace</option>

            {workspaces.map((workspace, index) => (
              <option value={workspace.name} key={index}>
                {workspace.emoji} {workspace.name}
              </option>
            ))}
          </select>

          <button
            onClick={handleAddTodo}
            className=" bg-black text-white px-4 py-2 rounded-lg ml-4 flex items-center"
          >
            <FaPlus className="mr-2" /> Add Todo
          </button>

        </div>
      </div>
    </div>
  )

};

export default MainArea;

```

```TSX

//============ components/Modal.tsx ============== 

import { FaTimes } from "react-icons/fa";
import { useStore } from "../store";

const Modal = () => {
  const {
    isListModalOpen,
    isWorkspaceModalOpen,
    modalName,
    modalEmoji,
    modalType,
    setModalName,
    setModalEmoji,
    handleSaveModal,
    closeListModal,
    closeWorkspaceModal,
  } = useStore();

  const handleClose = () => {
    if (modalType === "List") {
      closeListModal();
    } else if (modalType === "Workspace") {
      closeWorkspaceModal();
    }
  };

  const handleSave = () => {
    handleSaveModal();
  };

  if (!isListModalOpen && !isWorkspaceModalOpen) return null;

  return (
    <div className="fixed inset-0 flex items-center justify-center bg-gray-900 bg-opacity-50 z-50">
      <div className="bg-white rounded-lg shadow-lg p-6 w-96">
        <div className="flex justify-between items-center mb-4">
          <h2 className="text-xl font-bold text-gray-800">{`Create New ${modalType}`}</h2>
          <button onClick={handleClose} className="text-gray-500 hover:text-gray-700 transition">
            <FaTimes />
          </button>
        </div>

        <input
          type="text"
          value={modalName}
          onChange={(e) => setModalName(e.target.value)}
          placeholder={`Enter ${modalType} name`}
          className="w-full border border-gray-300 p-2 rounded-lg mb-4 focus:ring-2 focus:ring-blue-400"
        />

        <input
          type="text"
          value={modalEmoji}
          onChange={(e) => setModalEmoji(e.target.value)}
          placeholder="Enter emoji (optional)"
          className="w-full border border-gray-300 p-2 rounded-lg mb-4"
        />

        <button onClick={handleSave} className="w-full bg-blue-500 text-white py-2 rounded-lg hover:bg-blue-600 transition">
          Save
        </button>
      </div>
    </div>
  );

};

export default Modal;

```