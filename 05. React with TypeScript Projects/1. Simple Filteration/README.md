<h1  align="center" > 🍄 𝐒𝗂ꭑρᥣ𝖾 𝐅𝗂ᥣ𝗍𝖾𝗋α𝗍𝗂ⱺ𐓣 🥠</h1>

<h1  align="center" > 

<img src="" width="" height=""/>

</h1>

```TSX

//============ App.tsx ============== 

import Dashboard from "./components/Dashboard";

const App = () => {
  return (
    <div>
      <Dashboard />
    </div>
  );
};

export default App;

```

```TSX

//============ Components/Dashboard.tsx ============== 

import Sidebar from "./Sidebar";
import ProjectTable from "./Table";

const Dashboard = () => {
  return (
    <div className="flex h-screen">
      <Sidebar />
      <div className="flex-1 bg-gray-900">
        <ProjectTable />
      </div>
    </div>
  );
};

export default Dashboard;

```

```TSX

//============ Components/Sidebar.tsx ============== 

const Sidebar = () => {
  return (
    <div className="w-16 fixed h-screen border border-[#242424] p-4 flex flex-col items-center space-y-8">
      <div className="text-white">Logo</div>
      <div className="text-gray-400">📁</div>
      <div className="text-gray-400">👤</div>
      <div className="text-gray-400">⚙️</div>
    </div>
  );
};

export default Sidebar;

```

```TSX

//============ Components/ProjectTable.tsx ============== 

import { useState } from "react";
import { BsThreeDots } from "react-icons/bs";
import { BiSort } from "react-icons/bi";
import { MdSort } from "react-icons/md";
import { AiOutlineDown } from "react-icons/ai";
import { data } from "../utils/data";

const ProjectTable = () => {
  const [projects, setProjects] = useState(data);

  const [sortConfig, setSortConfig] = useState<{
    key: string;
    direction: string;
  } | null>(null);

  const [dropdownVisible, setDropdownVisible] = useState(false);
  const [filtersVisible, setFiltersVisible] = useState(false);
  const [searchQuery, setSearchQuery] = useState("");
  const [filters, setFilters] = useState({
    name: "",
    country: "",
    email: "",
    project: "",
    status: "",
  });
  const [statusDropdownVisible, setStatusDropdownVisible] = useState<
    number | null
  >(null);

  const sortProjects = (key: string) => {
    let sortedProjects = [...projects];

    if (
      sortConfig &&
      sortConfig.key === key &&
      sortConfig.direction === "ascending"
    ) {
      sortedProjects.sort((a, b) => (a[key] > b[key] ? -1 : 1));
      setSortConfig({ key, direction: "descending" });
    } else {
      sortedProjects.sort((a, b) => (a[key] > b[key] ? 1 : -1));
      setSortConfig({ key, direction: "ascending" });
    }
    setProjects(sortedProjects);
  };

  const handleSortOptionClick = (key: string) => {
    sortProjects(key);
    setDropdownVisible(false);
  };

  const handleFilterChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    setFilters({
      ...filters,
      [e.target.name]: e.target.value,
    });
  };

  const handleStatusChange = (index: number, newStatus: string) => {
    const updatedProjects = projects.map((project, i) =>
      i === index
        ? {
            ...project,
            status: newStatus,
            progress: newStatus === "Completed" ? "100%" : project.progress,
          }
        : project
    );
    setProjects(updatedProjects);
    setStatusDropdownVisible(null);
  };

  const filteredProjects = projects.filter(
    (project) =>
      (searchQuery === "" ||
        Object.values(project).some((value) =>
          value.toLowerCase().includes(searchQuery.toLowerCase())
        )) &&
      (filters.name === "" ||
        project.client.toLowerCase().includes(filters.name.toLowerCase())) &&
      (filters.country === "" ||
        project.country
          .toLowerCase()
          .includes(filters.country.toLowerCase())) &&
      (filters.email === "" ||
        project.email.toLowerCase().includes(filters.email.toLowerCase())) &&
      (filters.project === "" ||
        project.project
          .toLowerCase()
          .includes(filters.project.toLowerCase())) &&
      (filters.status === "" ||
        project.status.toLowerCase().includes(filters.status.toLowerCase()))
  );

  // Calculate paginated data
  const [currentPage, setCurrentPage] = useState(1);
  const itemsPerPage = 5;
  const startIndex = (currentPage - 1) * itemsPerPage;
  const currentProjects = filteredProjects.slice(
    startIndex,
    startIndex + itemsPerPage
  );
  const totalPages = Math.ceil(filteredProjects.length / itemsPerPage);
  const handlePageChange = (pageNumber: number) => setCurrentPage(pageNumber);

  return (
    <div className="p-4 w-[93%] ml-[5rem]">
      {/* Sorting */}
      <div className="flex items-center mb-5">
        <div className="relative">
          <button
            onClick={() => setDropdownVisible(!dropdownVisible)}
            className="border border-gray-700 flex items-center justify-center text-white p-2 rounded"
          >
            <BiSort className="mr-[0.3rem]" />
            Sort
            <AiOutlineDown className="ml-2" />
          </button>
          {dropdownVisible && (
            <div className="absolute top-full left-0 mt-2 bg-gray-800 border border-gray-700 rounded shadow-lg">
              <button
                onClick={() => handleSortOptionClick("client")}
                className="block px-4 py-2 text-white w-full hover:bg-gray-700"
              >
                Name
              </button>
              <button
                onClick={() => handleSortOptionClick("country")}
                className="block px-4 py-2 text-white hover:bg-gray-700"
              >
                Country
              </button>
              <button
                onClick={() => handleSortOptionClick("date")}
                className="block px-4 py-2 text-white  w-full hover:bg-gray-700"
              >
                Date
              </button>
            </div>
          )}
        </div>

        {/* Filters */}
        <div className="relative ml-4 w-full">
          <button
            onClick={() => setFiltersVisible(!filtersVisible)}
            className="border border-gray-700 flex items-center justify-center text-white p-2 rounded"
          >
            <MdSort className="mr-[0.3rem]" />
            Filters
            <AiOutlineDown className="ml-2" />
          </button>
          {filtersVisible && (
            <div className="absolute top-full left-0 mt-2 bg-gray-800 border border-gray-700 rounded shadow-lg p-4">
              <div className="mb-2">
                <label className="block text-white">Filter by Name:</label>
                <input
                  type="text"
                  name="name"
                  value={filters.name}
                  onChange={handleFilterChange}
                  className="bg-gray-900 text-white rounded p-2 w-full"
                />
              </div>
              <div className="mb-2">
                <label className="block text-white">Filter by Country:</label>
                <input
                  type="text"
                  name="country"
                  value={filters.country}
                  onChange={handleFilterChange}
                  className="bg-gray-900 text-white rounded p-2 w-full"
                />
              </div>
              <div className="mb-2">
                <label className="block text-white">Filter by Email:</label>
                <input
                  type="text"
                  name="email"
                  value={filters.email}
                  onChange={handleFilterChange}
                  className="bg-gray-900 text-white rounded p-2 w-full"
                />
              </div>
              <div className="mb-2">
                <label className="block text-white">Filter by Project:</label>
                <input
                  type="text"
                  name="project"
                  value={filters.project}
                  onChange={handleFilterChange}
                  className="bg-gray-900 text-white rounded p-2 w-full"
                />
              </div>
              <div className="mb-2">
                <label className="block text-white">Filter by Status:</label>
                <input
                  type="text"
                  name="status"
                  value={filters.status}
                  onChange={handleFilterChange}
                  className="bg-gray-900 text-white rounded p-2 w-full"
                />
              </div>
            </div>
          )}
        </div>
      </div>

      {/* Main Table */}
      <table className="min-w-full table-auto rounded border border-gray-700 text-white">
        <thead>
          <tr>
            <th className="px-5 py-3 text-left">Image</th>
            <th className="px-5 py-3 text-left">Name</th>
            <th className="px-5 py-3 text-left">Country</th>
            <th className="px-5 py-3 text-left">Email</th>
            <th className="px-5 py-3 text-left">Project Name</th>
            <th className="px-5 py-3 text-left">Task Progress</th>
            <th className="px-5 py-3 text-left">Status</th>
            <th className="px-5 py-3 text-left">Date</th>
            <th className="px-5 py-3 text-left">Actions</th>
          </tr>
        </thead>
        <tbody>
          {currentProjects.map((project, index) => (
            <tr key={index} className="border border-gray-700">
              <td className="px-4 py-2">
                <img
                  src={project.image}
                  alt={project.client}
                  className="w-[3rem] h-[3rem] object-cover rounded-full"
                />
              </td>
              <td className="px-4 py-2">{project.client}</td>
              <td className="px-4 py-2">{project.country}</td>
              <td className="px-4 py-2">{project.email}</td>
              <td className="px-4 py-2">{project.project}</td>

              <td className="px-4 py-2">
                <div className="w-24 h-2 bg-gray-700 rounded">
                  <div
                    className={`w-[${project.progress}] h-2 bg-green-500 rounded`}
                  ></div>
                </div>
              </td>
              <td className="px-4 py-2 w-[10rem]">
                <span
                  className={`bg-${
                    project.status === "Completed" ? "green" : "yellow"
                  }-500 p-1 rounded`}
                >
                  {project.status}
                </span>
              </td>
              <td className="px-4 py-2">{project.date}</td>

              <td className="px-4 py-2">
                <div className="relative">
                  <BsThreeDots
                    className="cursor-pointer"
                    onClick={() => setStatusDropdownVisible(index)}
                  />
                  {statusDropdownVisible === index && (
                    <div className="absolute top-full right-0 mt-2 bg-gray-800 border border-gray-700 rounded shadow-lg">
                      <button
                        onClick={() => handleStatusChange(index, "In Progress")}
                        className="block px-4 py-2 text-white hover:bg-gray-700 w-full text-left"
                      >
                        In Progress
                      </button>
                      <button
                        onClick={() => handleStatusChange(index, "Completed")}
                        className="block px-4 py-2 text-white hover:bg-gray-700 w-full text-left"
                      >
                        Completed
                      </button>
                    </div>
                  )}
                </div>
              </td>
            </tr>
          ))}
        </tbody>
      </table>

      {/* Pagination */}
      <div className="flex justify-end mt-4">
        <button
          disabled={currentPage === 1}
          onClick={() => handlePageChange(currentPage - 1)}
          className="px-4 py-2 bg-gray-700 text-white rounded mr-2 disabled:opacity-50"
        >
          Previous
        </button>
        <span className="px-4 py-2 text-white">
          Page {currentPage} of {totalPages}
        </span>
        <button
          disabled={currentPage === totalPages}
          onClick={() => handlePageChange(currentPage + 1)}
          className="px-4 py-2 bg-gray-700 text-white rounded ml-2 disabled:opacity-50"
        >
          Next
        </button>
      </div>
    </div>
  );
};

export default ProjectTable;

```

```TSX

//============ utils/data.ts ============== 

export const data = [
  {
    client: "Alice Johnson",
    country: "Canada",
    email: "alice.johnson@gmail.com",
    project: "AI Research Platform",
    progress: "10%",
    status: "Completed",
    date: "10/06/2023",
    image:
      "https://images.unsplash.com/photo-1526413232644-8a40f03cc03b?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    client: "Michael Thompson",
    country: "Germany",
    email: "michael.thompson@gmail.com",
    project: "Blockchain Development",
    progress: "20%",
    status: "In Progress",
    date: "22/07/2023",
    image:
      "https://images.unsplash.com/photo-1534528741775-53994a69daeb?q=80&w=1964&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    client: "Sophia Lee",
    country: "Australia",
    email: "sophia.lee@gmail.com",
    project: "E-Learning System",
    progress: "100%",
    status: "In Progress",
    date: "30/08/2023",
    image:
      "https://images.unsplash.com/photo-1524504388940-b1c1722653e1?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    client: "Lucas Perez",
    country: "Mexico",
    email: "lucas.perez@gmail.com",
    project: "Mobile Payment App",
    progress: "50%",
    status: "In Progress",
    date: "15/09/2023",
    image:
      "https://images.unsplash.com/photo-1539571696357-5a69c17a67c6?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    client: "Ava Kim",
    country: "South Korea",
    email: "ava.kim@gmail.com",
    project: "Smart Home Automation",
    progress: "30%",
    status: "In Progress",
    date: "05/07/2023",
    image:
      "https://images.unsplash.com/photo-1517841905240-472988babdf9?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    client: "Ethan Davis",
    country: "New Zealand",
    email: "ethan.davis@gmail.com",
    project: "Virtual Reality Game",
    progress: "8%",
    status: "In Progress",
    date: "23/06/2023",
    image:
      "https://images.unsplash.com/photo-1487222477894-8943e31ef7b2?q=80&w=1995&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    client: "Isabella Rossi",
    country: "Italy",
    email: "isabella.rossi@gmail.com",
    project: "E-Commerce Platform",
    progress: "60%",
    status: "In Progress",
    date: "18/05/2023",
    image:
      "https://images.unsplash.com/photo-1526510747491-58f928ec870f?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    client: "Noah Garcia",
    country: "Spain",
    email: "noah.garcia@gmail.com",
    project: "Tourism Website",
    progress: "80%",
    status: "Completed",
    date: "12/08/2023",
    image: "https://example.com/images/noah.jpg",
  },
  {
    client: "Emma Martinez",
    country: "Argentina",
    email: "emma.martinez@gmail.com",
    project: "Healthcare App",
    progress: "90%",
    status: "In Progress",
    date: "27/09/2023",
    image:
      "https://images.unsplash.com/photo-1519058082700-08a0b56da9b4?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    client: "Liam Patel",
    country: "India",
    email: "liam.patel@gmail.com",
    project: "Agritech Platform",
    progress: "100%",
    status: "In Progress",
    date: "09/09/2023",
    image:
      "https://images.unsplash.com/photo-1632765854612-9b02b6ec2b15?q=80&w=1886&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    client: "Olivia Chen",
    country: "China",
    email: "olivia.chen@gmail.com",
    project: "AI Assistant",
    progress: "20%",
    status: "In Progress",
    date: "01/08/2023",
    image:
      "https://images.unsplash.com/photo-1632765854612-9b02b6ec2b15?q=80&w=1886&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    client: "Mia Williams",
    country: "USA",
    email: "mia.williams@gmail.com",
    project: "Cloud Storage Solution",
    progress: "10%",
    status: "In Progress",
    date: "20/07/2023",
    image:
      "https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    client: "William Tanaka",
    country: "Japan",
    email: "william.tanaka@gmail.com",
    project: "IoT Device Integration",
    progress: "70%",
    status: "Completed",
    date: "29/06/2023",
    image:
      "https://images.unsplash.com/photo-1509783236416-c9ad59bae472?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
  {
    client: "Charlotte Wilson",
    country: "UK",
    email: "charlotte.wilson@gmail.com",
    project: "Financial Analytics Tool",
    progress: "90%",
    status: "In Progress",
    date: "13/09/2023",
    image:
      "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  },
];

```
