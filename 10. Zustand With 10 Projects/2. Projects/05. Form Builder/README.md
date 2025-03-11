
<h2  align="center" > 🕍 𝐅ⱺ𝗋ꭑ 𝐁υ𝗂ᥣᑯ𝖾𝗋 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

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
    <div>
      <h1>Form Builder</h1>
      <div>
        <input
          type="text"
          name="label"
          placeholder="Field Label"
          value={newField.label}
          onChange={handleFieldChange}
        />
        <select name="type" value={newField.type} onChange={handleFieldChange}>
          <option value="text">Text</option>
          <option value="number">Number</option>
          <option value="password">Password</option>
          <option value="textarea">Textarea</option>
          <option value="date">Date</option>
          <option value="file">File</option>
        </select>
        <button type="button" onClick={handleAddField}>
          Add Field
        </button>
        <button type="button" onClick={resetForm}>
          Reset Form
        </button>
      </div>
      <form>
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
    <div>
      <label>
        {field.label}
        <input
          type={field.type}
          value={field.type === "file" ? "" : field.value}
          onChange={handleChange}
        />
      </label>
      <button type="button" onClick={() => onRemove(index)}>
        Remove
      </button>
    </div>
  );
};

export default FormField;

```