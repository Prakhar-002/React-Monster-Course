
<h2  align="center" > 🕍 𝐍ⱺ𝗍𝖾𝗌 🏄‍♀️</h2>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/c7fbf0b1-4f9d-4805-ba35-bd9680ff1224" width="" height=""/>

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
    <div className="h-screen flex bg-teal-200 text-gray-800">
      {/* Sidebar */}
      <Sidebar />

      {/* Main Content */}
      <div className="w-2/3 bg-teal-200 p-8">
        {/* Text Editor */}
        <div className="p-6 pb-16 bg-teal-50 shadow-lg rounded-2xl">
          <ReactQuill
            value={editorContent}
            onChange={setEditorContent}
            placeholder="Write your note here..."
            theme="snow"
            className="h-96 bg-transparent"
          />
        </div>

        {/* Color Selector */}
        <div className="flex items-center mt-6 space-x-4">
          <input
            type="color"
            value={noteColor}
            onChange={(e) => setNoteColor(e.target.value)}
            className="w-12 h-12 border-2 border-teal-500 rounded-full shadow-md cursor-pointer hover:scale-110 transition-transform"
          />
          <p className="text-lg font-semibold">Choose a note color</p>
        </div>

        {/* Save Button */}
        <button
          className="bg-teal-600 hover:bg-teal-700 text-white py-3 px-6 mt-6 rounded-lg shadow-md font-semibold transition-all duration-300 transform hover:scale-105 focus:ring-4 focus:ring-teal-300 flex items-center"
          onClick={addOrUpdateNote}
        >
          <AiOutlinePlus className="mr-2" />
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
      <div className="w-1/3 bg-teal-600 text-white p-6 shadow-xl rounded-r-2xl">
        {/* Search Bar */}
        <div className="flex items-center mb-6 bg-teal-500 px-3 py-2 rounded-lg shadow-md">
          <FiSearch className="text-white text-xl mr-2" />
          <input
            type="text"
            className="w-full bg-transparent outline-none text-white placeholder-gray-300"
            placeholder="Search notes..."
            value={search}
            onChange={(e) => setSearch(e.target.value)}
          />
        </div>

        {/* Notes List */}
        <div className="space-y-3">
          {filteredNotes.length > 0 ? (
            filteredNotes.map((note, index) => (
              <div
                key={index}
                className="flex items-center p-4 bg-white/20 shadow-lg rounded-lg border border-white/30 cursor-pointer transition-all hover:bg-teal-500"
                onClick={() => selectNote(index)}
              >
                {/* Color Indicator */}
                <div
                  className="w-5 h-5 rounded-full border border-white mr-3"
                  style={{ backgroundColor: note.color }}
                ></div>

                {/* Note Content */}
                <div
                  className="truncate font-medium text-white"
                  dangerouslySetInnerHTML={{ __html: note.text }}
                />
              </div>
            ))
          ) : (
            <p className="text-white text-center">No new notes</p>
          )}
        </div>
      </div>
    </>
  );

};

export default Sidebar;

```