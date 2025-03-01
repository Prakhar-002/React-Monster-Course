<h1  align="center" > 🍄 𝐓𝐀𝐁𝐒 🥠</h1>

<h1  align="center" > 

<img src="https://github.com/user-attachments/assets/d42b4cc9-25c6-462c-a24c-61cc94c16926" width="" height=""/>

</h1>

```TSX

//============ App.tsx ============== 

import Profile from "./components/Profile";
import Sidebar from "./components/Sidebar";

const App = () => {
  return (
    <div>
      <Sidebar />
      <Profile />
    </div>
  );
};

export default App;

```

```TSX

//============ Components/Sidebar.tsx ============== 

import { FaHome, FaUser, FaSearch } from "react-icons/fa";
import { IoMdSettings } from "react-icons/io";

const Sidebar = () => {
  return (
    <aside className="sidebar fixed top-0 left-0 h-screen w-20 bg-[#1A1C1E] text-white">
      <ul className="p-4 flex flex-col justify-between items-center h-full">
        <div className="top">
          <li className="mb-2">
            <div className="flex items-center">
              <FaHome className="mr-2 mb-3" size={18} />
            </div>
          </li>
          <li className="mb-2">
            <div className="flex items-center">
              <FaUser className="mr-2 mb-3" size={18} />
            </div>
          </li>
          <li className="mb-2">
            <div className="flex items-center">
              <FaSearch className="mr-2 mb-3" size={18} />
            </div>
          </li>
        </div>

        <div className="bottom">
          <li>
            <IoMdSettings size={18} />
            <FaUser className="mt-5" size={18} />
          </li>
        </div>
      </ul>
    </aside>
  );
};

export default Sidebar;

```

```TSX

//============ Components/Profile.tsx ============== 

import { useState } from "react";
import { FaCamera } from "react-icons/fa";
import Tabs from "./Tabs";

const Profile = () => {
  const [bannerUrl, setBannerUrl] = useState(
    "https://via.placeholder.com/1500x400"
  );
  const [profileUrl, setProfileUrl] = useState(
    "https://via.placeholder.com/100"
  );

  // Handlers for image changes
  const handleBannerChange = (event) => {
    const file = event.target.files[0];
    if (file) {
      // The line of code is used in JavaScript to create a temporary URL that points to a Blob or File object.
      setBannerUrl(URL.createObjectURL(file));
    }
  };

  const handleProfileChange = (event) => {
    const file = event.target.files[0];
    if (file) {
      setProfileUrl(URL.createObjectURL(file));
    }
  };

  return (
    <div className="relative w-[94%] ml-[5rem]">
      <div className="relative">
        <img
          src={bannerUrl}
          alt="Background"
          className="w-full h-60 object-cover"
        />
        <button className="absolute top-2 right-2 bg-gray-800 text-white p-2 rounded-full hover:bg-gray-600">
          <label htmlFor="banner-upload" className="cursor-pointer">
            <FaCamera size={24} />
          </label>
          <input
            id="banner-upload"
            type="file"
            accept="image/*"
            className="hidden"
            onChange={handleBannerChange}
          />
        </button>
      </div>

      {/* Channel Logo */}
      <div className="flex items-center ml-4 mt-[2rem] ">
        <img
          src={profileUrl}
          alt="Channel Logo"
          className="w-40 h-40  object-cover rounded-full border-4 border-white relative"
        />

        <button className="absolute  ml-[3.6rem] mt-[10rem] bg-gray-800 text-white p-2 rounded-full hover:bg-gray-600">
          <label htmlFor="profile-upload" className="cursor-pointer">
            <FaCamera size={24} />
          </label>
          <input
            id="profile-upload"
            type="file"
            accept="image/*"
            className="hidden"
            onChange={handleProfileChange}
          />
        </button>

        {/* Channel Details */}
        <div className="ml-4 mt-4">
          <h1 className="text-2xl font-bold">HuXn WebDev</h1>
          <p>1M views</p>
          <p className="mt-2">
            This is a short description of the YouTube channel. It gives an
            overview of the content and what viewers can expect.
          </p>
          <button className="mt-4 bg-red-600 text-white py-2 px-4 rounded hover:bg-red-500">
            Subscribe
          </button>
        </div>
      </div>

      <Tabs />
    </div>
  );
};

export default Profile;

```

```TSX

//============ Components/Tabs.tsx ============== 

import { useState } from "react";
import { FaHome, FaInfoCircle, FaPhone } from "react-icons/fa";
import { GoProjectSymlink } from "react-icons/go";
import { SiCoursera } from "react-icons/si";
import Card from "./Card";
import About from "./About";
import Contact from "./Contact";

const tabs = [
  {
    id: "home",
    icon: <FaHome />,
    label: "Home",
    content: (
      <div className="flex flex-wrap">
        {Array.from({ length: 6 }).map((_, index) => (
          <Card
            key={index}
            title="Amazing Card"
            description="This is a cool-looking card component using React and Tailwind CSS."
            image="https://via.placeholder.com/400x300"
          />
        ))}
      </div>
    ),
  },
  {
    id: "about",
    icon: <FaInfoCircle />,
    label: "About",
    content: <About />,
  },
  {
    id: "projects",
    icon: <GoProjectSymlink />,
    label: "Projects",
    content: (
      <div className="flex flex-wrap">
        {Array.from({ length: 6 }).map((_, index) => (
          <Card
            key={index}
            title="Amazing Card"
            description="This is a cool-looking card component using React and Tailwind CSS."
            image="https://via.placeholder.com/400x300"
          />
        ))}
      </div>
    ),
  },
  {
    id: "courses",
    icon: <SiCoursera />,
    label: "Courses",
    content: (
      <div className="flex flex-wrap">
        {Array.from({ length: 6 }).map((_, index) => (
          <Card
            key={index}
            title="Amazing Card"
            description="This is a cool-looking card component using React and Tailwind CSS."
            image="https://via.placeholder.com/400x300"
          />
        ))}
      </div>
    ),
  },
  {
    id: "contact",
    icon: <FaPhone />,
    label: "Contact",
    content: <Contact />,
  },
];

const Tabs = () => {
  const [activeTab, setActiveTab] = useState(tabs[0].id);

  return (
    <div className="p-4 mt-[3rem]">
      <div className="flex border-b border-gray-200">
        {tabs.map((tab) => (
          <button
            key={tab.id}
            className={`flex-1 text-center py-2 px-4 font-medium text-sm ${
              activeTab === tab.id ? "border-b-2 " : "text-gray-600"
            }`}
            onClick={() => setActiveTab(tab.id)}
          >
            <div className="flex items-center justify-center space-x-2">
              {tab.icon}
              <span>{tab.label}</span>
            </div>
          </button>
        ))}
      </div>
      <div className="mt-4 p-4 rounded-lg">
        {tabs.find((tab) => tab.id === activeTab)?.content}
      </div>
    </div>
  );
};

export default Tabs;

```

```TSX

//============ Components/Card.tsx ============== 

interface CardProps {
  title: string;
  description: string;
  image: string;
  link: string;
}

const Card = ({ title, description, image, link }: CardProps) => {
  return (
    <div className="max-w-sm mx-auto m-[1rem] bg-[#1A1C1E] rounded-lg shadow-md overflow-hidden">
      <img className="w-full h-48 object-cover" src={image} alt={title} />
      <div className="p-6">
        <h2 className="text-2xl font-bold  mb-2">{title}</h2>
        <p className="text-gray-700 mb-4">{description}</p>
        <a
          href={link}
          className="inline-block px-4 py-2 bg-white text-black font-semibold rounded-lg shadow hover:bg-gray-600 hover:text-white transition duration-200"
        >
          Learn More
        </a>
      </div>
    </div>
  );
};

export default Card;

```

```TSX

//============ Components/About.tsx ============== 

const About = () => {
  return (
    <section className="bg-gray-100 py-12 px-4 sm:px-6 lg:px-8">
      <div className="max-w-4xl mx-auto">
        <h2 className="text-3xl font-extrabold text-gray-900 mb-6">
          About HuXn
        </h2>
        <p className="text-lg text-gray-700">
          HuXn is a talented software engineer with a passion for creating
          stunning user experiences. Having worked with an extensive range of
          technologies, frameworks, and programming languages - from React and
          Angular to Python, Golang, and more - his expertise in the field is
          unparalleled. HuXn's diverse skill set has enabled him to build
          countless projects for clients around the world, showcasing his
          ability to adapt and excel in any given environment.
        </p>
        <p className="mt-4 text-lg text-gray-700">
          However, it was his love for User Interface Design that truly set him
          apart. HuXn's dedication to honing his skills in this area led him
          down a path of self-discovery, taking advantage of every resource
          available to him - from online tutorials to workshops and beyond. With
          his tireless efforts, HuXn has earned his badge as a truly talented
          UI/UX Designer.
        </p>
      </div>
    </section>
  );
};

export default About;

```

```TSX

//============ Components/Contact.tsx ============== 

import { FaTwitter, FaYoutube, FaGithub, FaInstagram } from "react-icons/fa";

const Contact = () => {
  const links = [
    {
      href: "https://twitter.com/@huxnwebdev",
      label: "Twitter",
      icon: <FaTwitter className="h-6 w-6 text-blue-500" />,
    },
    {
      href: "https://youtube.com/@huxnwebdev",
      label: "YouTube",
      icon: <FaYoutube className="h-6 w-6 text-red-600" />,
    },
    {
      href: "https://github.com/HuXn-WebDev",
      label: "GitHub",
      icon: <FaGithub className="h-6 w-6 text-gray-900" />,
    },
    {
      href: "https://instagram.com/huxnshorts",
      label: "Instagram",
      icon: <FaInstagram className="h-6 w-6 text-pink-500" />,
    },
  ];

  return (
    <section className="bg-gray-100 py-12 px-4 sm:px-6 lg:px-8">
      <h2 className="text-3xl font-extrabold text-gray-900 mb-6">Contact Me</h2>
      <div className="flex items-center ">
        {links.map((link) => (
          <a
            key={link.label}
            href={link.href}
            target="_blank"
            rel="noopener noreferrer"
            className="flex items-center space-x-2 text-gray-900 hover:text-gray-600 mr-[2rem]"
          >
            {link.icon}
            <span className="text-lg">{link.label}</span>
          </a>
        ))}
      </div>
    </section>
  );
};

export default Contact;

```
