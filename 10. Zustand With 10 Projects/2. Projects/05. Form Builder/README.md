
<h2  align="center" > 🕍 𝐅ⱺ𝗋ꭑ 𝐁υ𝗂ᥣᑯ𝖾𝗋 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/917c4e4b-9b56-4e8d-9066-91cf40b5939c" width="700px" height="445px"/>

</h1>

</br>

```TS

//============ store.ts ============== 

import { create } from "zustand";

// Define the type for form fields
interface FormField {
  label: string;
  type: "text" | "number" | "password" | "textarea" | "date" | "file";
  value: string;
}

// Define the shape of the store state
interface FormStoreState {
  formFields: FormField[];
  addField: (field: FormField) => void;
  removeField: (index: number) => void;
  updateField: (index: number, updatedField: FormField) => void;
  resetForm: () => void;
}

// Create the Zustand store with TypeScript
const useFormStore = create<FormStoreState>((set) => ({
  formFields: [],

  addField: (field) =>
    set((state) => ({
      formFields: [...state.formFields, field],
    })),

  removeField: (index) =>
    set((state) => ({
      formFields: state.formFields.filter((_, i) => i !== index),
    })),

  updateField: (index, updatedField) =>
    set((state) => ({
      formFields: state.formFields.map((field, i) =>
        i === index ? updatedField : field
      ),
    })),

  resetForm: () => set({ formFields: [] }),
}));

export default useFormStore;

```

```TSX

//============ App.tsx ============== 

import FormBuilder from "./components/FormBuilder";

const App = () => {
  return (
    <div>
      <FormBuilder />
    </div>
  );
};

export default App;

```

```TSX

//============ components/FormBuilder.tsx ============== 

import { useState, ChangeEvent } from "react";
import useFormStore from "../store";
import FormField from "./FormField";

interface NewField {
  label: string;
  type: "text" | "number" | "password" | "textarea" | "date" | "file";
  value: string;
}

const FormBuilder = () => {
  const { formFields, addField, removeField, updateField, resetForm } =
    useFormStore();
  const [newField, setNewField] = useState<NewField>({
    label: "",
    type: "text",
    value: "",
  });

  const handleAddField = () => {
    addField(newField);
    setNewField({ label: "", type: "text", value: "" });
  };

  const handleFieldChange = (
    e: ChangeEvent<HTMLInputElement | HTMLSelectElement | HTMLTextAreaElement>
  ) => {
    const { name, value } = e.target;
    setNewField((prev) => ({ ...prev, [name]: value }));
  };

  const handleFieldUpdate = (index: number, updatedField: NewField) => {
    updateField(index, updatedField);
  };

  const handleFieldRemove = (index: number) => {
    removeField(index);
  };

  return (
    <div className=" bg-gray-300 min-h-screen">
      <div className="max-w-3xl bg-gray-400 mx-auto p-6 shadow-lg rounded-lg">
        <h1 className="text-2xl  font-semibold mb-4 text-center">Form Builder</h1>

        {/* New Field Input Section */}
        <div className="flex flex-col md:flex-row gap-4 mb-6">
          <input
            type="text"
            name="label"
            placeholder="Field Label"
            value={newField.label}
            onChange={handleFieldChange}
            className="w-full p-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-blue-400"
          />
          <select
            name="type"
            value={newField.type}
            onChange={handleFieldChange}
            className="w-full p-2 border rounded-md bg-white focus:outline-none focus:ring-2 focus:ring-blue-400"
          >
            <option value="text">Text</option>
            <option value="number">Number</option>
            <option value="password">Password</option>
            <option value="textarea">Textarea</option>
            <option value="date">Date</option>
            <option value="file">File</option>
          </select>
          <div className="flex justify-between space-x-2">
            <button
              type="button"
              onClick={handleAddField}
              className="bg-blue-600 text-white px-4 py-2 rounded-md hover:bg-blue-700 transition"
            >
              Add Field
            </button>
            <button
              type="button"
              onClick={resetForm}
              className="bg-red-500 text-white px-4 py-2 rounded-md hover:bg-red-600 transition"
            >
              Reset Form
            </button>
          </div>
        </div>

        {/* Form Fields Display */}
        <form className="space-y-4">
          {formFields.map((field, index) => (
            <FormField
              key={index}
              field={field}
              index={index}
              onUpdate={handleFieldUpdate}
              onRemove={handleFieldRemove}
            />
          ))}
        </form>
      </div>
    </div>
  );
};

export default FormBuilder;

```

```TSX

//============ components/FormField.tsx ============== 

interface FormFieldProps {
  field: {
    label: string;
    type: "text" | "number" | "password" | "textarea" | "date" | "file";
    value: string;
  };
  index: number;
  onUpdate: (
    index: number,
    updatedField: {
      label: string;
      type: "text" | "number" | "password" | "textarea" | "date" | "file";
      value: string;
    }
  ) => void;
  onRemove: (index: number) => void;
}

const FormField: React.FC<FormFieldProps> = ({
  field,
  index,
  onUpdate,
  onRemove,
}) => {
  const handleChange = (
    e: React.ChangeEvent<HTMLInputElement | HTMLTextAreaElement>
  ) => {
    onUpdate(index, { ...field, value: e.target.value });
  };

  if (field.type === "textarea") {
    return (
      <div>
        <label>
          {field.label}
          <textarea value={field.value} onChange={handleChange} />
        </label>
        <button type="button" onClick={() => onRemove(index)}>
          Remove
        </button>
      </div>
    );
  }

  if (field.type === "file") {
    return (
      <div>
        <label>
          {field.label}
          <input
            type="file"
            onChange={(e) =>
              onUpdate(index, {
                ...field,
                value: e.target.files
                  ? Array.from(e.target.files)
                      .map((file) => file.name)
                      .join(", ")
                  : "",
              })
            }
          />
        </label>
        <button type="button" onClick={() => onRemove(index)}>
          Remove
        </button>
      </div>
    );
  }

  return (
    <div className="flex flex-col gap-2 p-4 bg-gray-100 rounded-lg shadow-md">
      <label className="text-sm font-semibold">{field.label}</label>

      {field.type === "textarea" ? (
        <textarea
          value={field.value}
          onChange={handleChange}
          className="w-full p-2 border rounded-md focus:ring-2 focus:ring-blue-400"
        />
      ) : field.type === "file" ? (
        <div className="flex flex-col gap-2">
          <input
            type="file"
            onChange={(e) =>
              onUpdate(index, {
                ...field,
                value: e.target.files
                  ? Array.from(e.target.files)
                    .map((file) => file.name)
                    .join(", ")
                  : "",
              })
            }
            className="p-2 border rounded-md focus:ring-2 focus:ring-blue-400"
          />
          {field.value && (
            <p className="text-sm text-gray-600">Selected: {field.value}</p>
          )}
        </div>
      ) : (
        <input
          type={field.type}
          value={field.type === "file" ? undefined : field.value} // Use 'undefined' instead of an empty string
          onChange={handleChange}
          className="w-full p-2 border rounded-md focus:ring-2 focus:ring-blue-400"
        />
      )}

      <button
        type="button"
        onClick={() => onRemove(index)}
        className="self-start px-3 py-1 text-white bg-red-500 rounded-md hover:bg-red-600 transition"
      >
        Remove
      </button>
    </div>
  );

};

export default FormField;

```