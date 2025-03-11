
<h2  align="center" > 🕍 𝐍ⱺ𝗍𝖾𝗌 🏄‍♀️</h2>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

</br>

```TS

//============ store.ts ============== 

import { create } from "zustand";

interface Note {
  text: string;
  color: string;
}

interface NotesState {
  notes: Note[];
  search: string;
  editorContent: string;
  noteColor: string;
  currentNoteIndex: number | null;
  setNotes: (updatedNotes: Note[]) => void;
  setSearch: (searchValue: string) => void;
  setEditorContent: (content: string) => void;
  setNoteColor: (color: string) => void;
  setCurrentNoteIndex: (index: number | null) => void;
  addOrUpdateNote: () => void;
  selectNote: (index: number) => void;
}

const useNotesStore = create<NotesState>((set) => ({
  notes: [],
  search: "",
  editorContent: "",
  noteColor: "#ffffff",
  currentNoteIndex: null,

  setNotes: (updatedNotes) => set(() => ({ notes: updatedNotes })),
  setSearch: (searchValue) => set(() => ({ search: searchValue })),
  setEditorContent: (content) => set(() => ({ editorContent: content })),
  setNoteColor: (color) => set(() => ({ noteColor: color })),
  setCurrentNoteIndex: (index) => set(() => ({ currentNoteIndex: index })),

  addOrUpdateNote: () =>
    set((state) => {
      const { editorContent, noteColor, currentNoteIndex, notes } = state;
      if (editorContent.trim()) {
        if (currentNoteIndex !== null) {
          // Update existing note
          const updatedNotes = [...notes];
          updatedNotes[currentNoteIndex] = {
            text: editorContent,
            color: noteColor,
          };
          return {
            notes: updatedNotes,
            editorContent: "",
            noteColor: "#ffffff",
            currentNoteIndex: null,
          };
        } else {
          return {
            notes: [...notes, { text: editorContent, color: noteColor }],
            editorContent: "",
            noteColor: "#ffffff",
            currentNoteIndex: null,
          };
        }
      }
    }),

  selectNote: (index) =>
    set((state) => ({
      currentNoteIndex: index,
      editorContent: state.notes[index].text,
      noteColor: state.notes[index].color,
    })),
}));

export default useNotesStore;

```

```TSX

//============ App.tsx ============== 

import { AiOutlinePlus } from "react-icons/ai";
import ReactQuill from "react-quill";
import "react-quill/dist/quill.snow.css";
import useNotesStore from "./store";
import Sidebar from "./components/Sidebar";

const App = () => {
  const {
    editorContent,
    noteColor,
    currentNoteIndex,
    setEditorContent,
    setNoteColor,
    addOrUpdateNote,
  } = useNotesStore();

  return (
    <div className="h-screen flex">
      <Sidebar />
      {/* Main Area */}
      <div className="w-2/3 p-8">
        {/* Text Editor (React Quill) */}
        <div className="p-4 rounded-lg">
          <ReactQuill
            value={editorContent}
            onChange={setEditorContent}
            placeholder="Write your note here..."
            theme="snow"
            className="h-96 bg-white mb-[2rem]"
          />
        </div>

        {/* Color Selector */}
        <div className="flex ml-[1rem] items-center mt-4 space-x-4">
          <input
            type="color"
            value={noteColor}
            onChange={(e) => setNoteColor(e.target.value)}
            className="w-10 h-10 p-1 border rounded-full"
          />
          <p>Choose a note color</p>
        </div>

        {/* Save Button */}
        <button
          className="bg-blue-500 ml-[1rem] text-white py-2 px-4 mt-4 rounded-lg shadow-lg hover:bg-blue-600 flex items-center"
          onClick={addOrUpdateNote}
        >
          <AiOutlinePlus className="mr-2" />{" "}
          {currentNoteIndex !== null ? "Update Note" : "Save Note"}
        </button>
      </div>
    </div>
  );
};

export default App;

```

```TSX

//============ components/Sidebar.tsx ============== 

import { FiSearch } from "react-icons/fi";
import useNotesStore from "../store";

const Sidebar = () => {
  const { notes, search, selectNote, setSearch } = useNotesStore();

  const filteredNotes = notes.filter((note) =>
    note.text.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <>
      {/* Sidebar */}
      <div className="w-1/3 bg-white p-4 shadow-lg">
        {/* Search Bar */}
        <div className="flex items-center mb-4">
          <FiSearch className="text-xl mr-2" />
          <input
            type="text"
            className="w-full border-b focus:outline-none"
            placeholder="Search notes..."
            value={search}
            onChange={(e) => setSearch(e.target.value)}
          />
        </div>

        {/* Notes List */}
        <div>
          {filteredNotes.length > 0 ? (
            filteredNotes.map((note, index) => (
              <div
                key={index}
                className="flex items-center p-4 mb-2 rounded-lg shadow-md cursor-pointer border hover:bg-gray-300"
                onClick={() => selectNote(index)}
              >
                {/* Color Circle */}
                <div
                  className="w-4 h-4 rounded-full mr-2"
                  style={{
                    backgroundColor: note.color,
                    border: "1px solid #000",
                  }}
                ></div>

                {/* Note Content */}
                <div
                  className="truncate"
                  dangerouslySetInnerHTML={{ __html: note.text }}
                />
              </div>
            ))
          ) : (
            <p>No new notes</p>
          )}
        </div>
      </div>
    </>
  );
};

export default Sidebar;

```