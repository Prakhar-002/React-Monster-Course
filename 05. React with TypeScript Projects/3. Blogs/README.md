<h1  align="center" > 🍄 𝐁𝐋𝐎𝐆𝐒 🥠</h1>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/5369c8a0-3816-48d9-affe-cc519f7c0067" width="" height=""/>

</h1>

```TSX

//============ App.tsx ============== 

import { useState } from "react";
import ArticleList from "./components/ArticleList";
import BlogForm from "./components/BlogForm";
import Modal from "./components/Modal";
import Navigation from "./components/Navigation";
import PeopleToFollow from "./components/PeopleToFollow";
import TopicsList from "./components/TopTopics";
import TrendsList from "./components/TrendList";
import { BlogProvider } from "./shared/BlogContext";
import { Blog } from "./types";
import { IoMdAddCircle } from "react-icons/io";

const App = () => {
  const [isModalOpen, setModalOpen] = useState(false);
  const [editingBlog, setEditingBlog] = useState<Blog | null>(null);

  const openModalForNewBlog = () => {
    setEditingBlog(null);
    setModalOpen(true);
  };

  const openModalForEdit = (blog: Blog) => {
    setEditingBlog(blog);
    setModalOpen(true);
  };

  return (
    <div>
      <BlogProvider>
        <Navigation />

        <div className="flex justify-center">
          <div className="mx-auto p-6">
            <div>
              <button
                onClick={openModalForNewBlog}
                className="ml-[7rem] bg-black flex justify-center items-center text-white px-4 py-2 rounded mb-4"
              >
                Add New Blog <IoMdAddCircle className="ml-[.5rem]" />
              </button>

              <ArticleList onEdit={openModalForEdit} />
              {isModalOpen && (
                <Modal onClose={() => setModalOpen(false)}>
                  <BlogForm
                    existingBlog={editingBlog}
                    onClose={() => setModalOpen(false)}
                  />
                </Modal>
              )}
            </div>
          </div>

          <div className="w-[30%]">
            <PeopleToFollow />
            <TrendsList />
            <TopicsList />
          </div>
        </div>
      </BlogProvider>
    </div>
  );
};

export default App;

```

```TSX

//============ Components/Navigation.tsx ============== 

import { FaSearch, FaUserCircle } from "react-icons/fa";

const Navigation = () => {
  return (
    <nav className="border-2 text-black border-gray-200 p-4 flex justify-between items-center">
      {/* Center: Search Bar */}
      <div className="flex items-center border-2  rounded-full px-4 py-2 max-w-md ml-[5rem]">
        <FaSearch className="mr-2 text-xl" />
        <input
          type="text"
          placeholder="Search..."
          className="bg-transparent outline-none w-full"
        />
      </div>

      {/* Right: User Profile */}
      <div className="flex items-center mr-[5rem]">
        <FaUserCircle className="text-3xl mr-2" />
      </div>
    </nav>
  );
};

export default Navigation;

```


```TSX

//============ Components/PeopleToFollow.tsx ============== 

import UserCard from "./UserCard";

const peopleToFollow = [
  { name: "Alena Gouse", following: false },
  { name: "Ruben Bator", following: true },
  { name: "Aspen Stanton", following: false },
  { name: "Madelyn George", following: false },
];

function PeopleToFollow() {
  return (
    <div className="bg-white p-4 rounded-lg shadow">
      <h3 className="font-semibold text-lg mb-4">👥 People who to follow</h3>
      <div className="space-y-4">
        {peopleToFollow.map((person, index) => (
          <UserCard key={index} person={person} />
        ))}
      </div>
    </div>
  );
}

export default PeopleToFollow;

```


```TSX

//============ Components/UserCard.tsx ============== 

import { FaUserCircle } from "react-icons/fa";

function UserCard({ person }) {
  return (
    <div className="flex items-center justify-between">
      <div className="flex items-center">
        <FaUserCircle className="text-3xl mr-3 text-gray-500" />
        <span>{person.name}</span>
      </div>
      <button
        className={`px-4 py-1 text-sm rounded-full ${
          person.following ? "bg-black text-white" : "bg-gray-200 text-gray-700"
        }`}
      >
        {person.following ? "Following" : "Follow"}
      </button>
    </div>
  );
}

export default UserCard;

```


```TSX

//============ Components/TrendsList.tsx ============== 

const trends = [
  {
    title: "Be the Person You Are on Vacation",
    author: "Maren Torff",
  },
  {
    title: "Hate NFTs? I have some bad news...",
    author: "Zain Levin",
  },
  {
    title: "The real impact of dark UX patterns",
    author: "Lindsey Curtis",
  },
];

function TrendsList() {
  return (
    <div className="bg-white p-4 rounded-lg shadow mt-8">
      <h3 className="font-semibold text-lg mb-4">📈 Today's top trends</h3>
      <ul className="space-y-4">
        {trends.map((trend, index) => (
          <li key={index} className="flex flex-col">
            <span className="font-medium">{trend.title}</span>
            <span className="text-sm text-gray-500">By {trend.author}</span>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default TrendsList;

```


```TSX

//============ Components/TopicsList.tsx ============== 

const topics = [
  "Technology",
  "Design Thinking",
  "Crypto",
  "NFT",
  "Personal Growth",
  "Reading",
];

function TopicsList() {
  return (
    <div className="bg-white p-4 rounded-lg shadow mt-8">
      <h3 className="font-semibold text-lg mb-4">🏷️ Topics for you</h3>
      <div className="flex flex-wrap gap-2">
        {topics.map((topic, index) => (
          <span
            key={index}
            className="px-3 py-1 bg-gray-200 text-gray-700 text-sm rounded-full cursor-pointer hover:bg-gray-300"
          >
            {topic}
          </span>
        ))}
      </div>
    </div>
  );
}

export default TopicsList;

```


```TSX

//============ Components/Modal.tsx ============== 

const Modal: React.FC<{ children: React.ReactNode; onClose: () => void }> = ({
  children,
  onClose,
}) => {
  return (
    <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center">
      <div className="bg-white p-4 rounded-lg shadow relative">
        {children}
        <button
          onClick={onClose}
          className="absolute top-2 right-2 text-gray-500"
        >
          ✕
        </button>
      </div>
    </div>
  );
};

export default Modal;

```

```TS

//============ types.ts ============== 

export interface Blog {
  id: number;
  title: string;
  description: string;
  image: string;
  time: string;
}

```

```TSX

//============ shared/BlogContext.tsx ============== 

import { createContext, useState, useContext } from "react";
import { Blog } from "../types";

interface BlogContextType {
  blogs: Blog[];
  addBlog: (blog: Blog) => void;
  updateBlog: (blog: Blog) => void;
  deleteBlog: (id: number) => void;
}

const BlogContext = createContext<BlogContextType | undefined>(undefined);

export const BlogProvider: React.FC<{ children: React.ReactNode }> = ({
  children,
}) => {
  const [blogs, setBlogs] = useState<Blog[]>([]);

  const addBlog = (blog: Blog) => {
    setBlogs([...blogs, blog]);
  };

  const updateBlog = (updatedBlog: Blog) => {
    setBlogs(
      blogs.map((blog) => (blog.id === updatedBlog.id ? updatedBlog : blog))
    );
  };

  const deleteBlog = (id: number) =>
    setBlogs(blogs.filter((blog) => blog.id !== id));

  return (
    <BlogContext.Provider value={{ blogs, addBlog, updateBlog, deleteBlog }}>
      {children}
    </BlogContext.Provider>
  );
};

export const useBlogs = () => {
  const context = useContext(BlogContext);
  if (!context) {
    throw new Error("useBlogs must be used within a BlogProvider");
  }
  return context;
};

```

```TSX

//============ Components/BlogForm.tsx ============== 

import { useState, useEffect } from "react";
import { useBlogs } from "../shared/BlogContext";
import { Blog } from "../types";

interface BlogFormProps {
  existingBlog?: Blog;
  onClose: () => void;
}

const BlogForm: React.FC<BlogFormProps> = ({ existingBlog, onClose }) => {
  const { addBlog, updateBlog } = useBlogs();
  const [title, setTitle] = useState(existingBlog?.title || "");
  const [description, setDescription] = useState(
    existingBlog?.description || ""
  );
  const [image, setImage] = useState(existingBlog?.image || "");
  const [time, setTime] = useState(existingBlog?.time || "");

  useEffect(() => {
    if (existingBlog) {
      setTitle(existingBlog.title);
      setDescription(existingBlog.description);
      setImage(existingBlog.image);
      setTime(existingBlog.time);
    }
  }, [existingBlog]);

  const handleSubmit = () => {
    const blog: Blog = {
      id: existingBlog ? existingBlog.id : Date.now(),
      title,
      description,
      image,
      time,
    };

    if (existingBlog) {
      updateBlog(blog);
    } else {
      addBlog(blog);
    }

    onClose();
  };

  return (
    <div className="bg-white p-6 rounded-lg  w-[30rem] mx-auto">
      <h3 className="font-semibold text-xl mb-2 text-gray-800">
        {existingBlog ? "Edit Blog" : "Add Blog"}
      </h3>
      <div className="space-y-4">
        <input
          type="text"
          placeholder="Title"
          value={title}
          onChange={(e) => setTitle(e.target.value)}
          className="block w-full px-4 py-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-black"
        />
        <textarea
          placeholder="Description"
          value={description}
          onChange={(e) => setDescription(e.target.value)}
          className="block w-full px-4 py-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-black resize-none h-32"
        />
        <input
          type="text"
          placeholder="Image URL"
          value={image}
          onChange={(e) => setImage(e.target.value)}
          className="block w-full px-4 py-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-black"
        />
        <input
          type="date"
          placeholder="Time"
          value={time}
          onChange={(e) => setTime(e.target.value)}
          className="block w-full px-4 py-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-black"
        />
      </div>
      <div className="flex justify-end mt-6 space-x-4">
        <button
          onClick={handleSubmit}
          className="bg-blue-600 text-white px-6 py-2 rounded-lg font-semibold shadow-sm hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-black"
        >
          {existingBlog ? "Update" : "Add"}
        </button>
        <button
          onClick={onClose}
          className="bg-gray-500 text-white px-6 py-2 rounded-lg font-semibold shadow-sm hover:bg-gray-600 focus:outline-none focus:ring-2 focus:ring-gray-500"
        >
          Cancel
        </button>
      </div>
    </div>
  );
};

export default BlogForm;

```


```TSX

//============ Components/ArticleList.tsx ============== 

import { useBlogs } from "../shared/BlogContext";
import ArticleCard from "./ArticleCard";
import { Blog } from "../types";

interface ArticleListProps {
  onEdit: (blog: Blog) => void;
}

const ArticleList: React.FC<ArticleListProps> = ({ onEdit }) => {
  const { blogs, deleteBlog } = useBlogs();

  return (
    <div className="ml-[5rem]">
      {blogs.map((blog) => (
        <ArticleCard
          key={blog.id}
          article={blog}
          onDelete={() => deleteBlog(blog.id)}
          onEdit={() => onEdit(blog)}
        />
      ))}
    </div>
  );
};

export default ArticleList;

```

```TSX

//============ Components/Counter.tsx ============== 

import { FaBookmark, FaTrash, FaEdit } from "react-icons/fa";
import { Blog } from "../types";

interface ArticleCardProps {
  article: Blog;
  onDelete: () => void;
  onEdit: () => void;
}

const ArticleCard: React.FC<ArticleCardProps> = ({
  article,
  onDelete,
  onEdit,
}) => {
  return (
    <div className="flex p-4 bg-white w-[40rem] mb-6 ml-[2rem] shadow-lg rounded-lg hover:shadow-xl transition-shadow duration-300 ease-in-out">
      <img
        src={article.image}
        alt={article.title}
        className="w-36 h-24 object-cover rounded-lg shadow-md"
      />
      <div className="ml-6 flex-1 flex flex-col">
        <h3 className="text-xl font-semibold text-gray-800 mb-2">
          {article.title}
        </h3>
        <p className="text-sm text-gray-700 flex-1">{article.description}</p>
        <div className="flex items-center justify-between mt-4 text-gray-600">
          <span className="text-xs">{article.time}</span>
          <div className="flex space-x-3">
            <FaBookmark className="text-gray-500 hover:text-gray-700 transition-colors duration-200 cursor-pointer" />
            <FaEdit
              onClick={onEdit}
              className="text-blue-500 hover:text-blue-600 transition-colors duration-200 cursor-pointer"
            />
            <FaTrash
              onClick={onDelete}
              className="text-red-500 hover:text-red-600 transition-colors duration-200 cursor-pointer"
            />
          </div>
        </div>
      </div>
    </div>
  );
};

export default ArticleCard;

```
