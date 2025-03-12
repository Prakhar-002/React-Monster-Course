
<h2  align="center" > 🕍 𝐄𝗑ρ𝖾𐓣𝗌𝖾 𝐓𝗋α𝖼𝗄𝖾𝗋 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/f97c35b4-d945-4706-9b1b-d93bf9cdd488" width="700px" height="784px"/>

</h1>

</br>

```TS

//============ store.ts ============== 

import { create } from "zustand";

interface Expense {
  id: number;
  description: string;
  amount: number;
}

interface ExpenseStore {
  expenses: Expense[];
  addExpense: (expense: Expense) => void;
  removeExpense: (id: number) => void;
}

const useStore = create<ExpenseStore>((set) => ({
  expenses: [],
  addExpense: (expense) =>
    set((state) => ({
      expenses: [...state.expenses, expense],
    })),
  removeExpense: (id) =>
    set((state) => ({
      expenses: state.expenses.filter((expense) => expense.id !== id),
    })),
}));

export default useStore;

```

```TSX

//============ App.tsx ============== 

import ExpenseTracker from "./components/ExpenseTracker";

const App = () => {
  return (
    <div>
      <ExpenseTracker />
    </div>
  );
};

export default App;

```

```TSX

//============ components/ExpenseTracker.tsx ============== 

import { useState } from "react";
import useStore from "../store";

const ExpenseTracker = () => {
  const { expenses, addExpense, removeExpense } = useStore();
  const [description, setDescription] = useState<string>("");
  const [amount, setAmount] = useState<number | "">("");

  const handleAddExpense = () => {
    if (description.trim() === "" || amount === "") return;

    addExpense({
      id: Date.now(),
      description,
      amount: Number(amount),
    });

    setDescription("");
    setAmount("");
  };

  return (
    <div className="min-h-screen flex items-center justify-center bg-blue-100">
      <div className="bg-white p-6 rounded-lg shadow-lg w-full max-w-lg">
        <h1 className="text-3xl font-bold mb-6 text-center text-blue-800">
          Expense Tracker
        </h1>
        <div className="space-y-4 mb-6">
          <input
            type="text"
            value={description}
            onChange={(e) => setDescription(e.target.value)}
            placeholder="Expense Description"
            className="w-full px-4 py-2 border rounded-lg border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500"
          />
          <input
            type="number"
            value={amount}
            onChange={(e) =>
              setAmount(e.target.value === "" ? "" : Number(e.target.value))
            }
            placeholder="Amount"
            className="w-full px-4 py-2 border rounded-lg border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500"
          />
          <button
            onClick={handleAddExpense}
            className="bg-blue-500 text-white w-full px-4 py-2 rounded-lg hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-blue-500"
          >
            Add Expense
          </button>
        </div>
        <ul className="space-y-4 mb-6">
          {expenses.map((expense) => (
            <li
              key={expense.id}
              className="flex justify-between items-center bg-blue-50 p-4 rounded-lg shadow-sm"
            >
              <span className="text-gray-700">
                {expense.description}: ${expense.amount.toFixed(2)}
              </span>
              <button
                onClick={() => removeExpense(expense.id)}
                className="bg-red-500 text-white px-3 py-1 rounded-lg hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-red-500"
              >
                Delete
              </button>
            </li>
          ))}
        </ul>
        <div className="text-center">
          <h2 className="text-2xl font-semibold text-blue-800">
            Total Expense: $
            {expenses
              .reduce((total, expense) => total + expense.amount, 0)
              .toFixed(2)}
          </h2>
        </div>
      </div>
    </div>
  );
};

export default ExpenseTracker;

```