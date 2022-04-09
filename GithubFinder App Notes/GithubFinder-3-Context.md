````react
GithubContext.js


import { createContext, useState } from "react"; / We import createContext

const GithubContext = createContext();

const GITHUB_URL = process.env.REACT_APP_GITHUB_URL; / We set our url and token to variables
const GITHUB_TOKEN = process.env.REACT_APP_GITHUB_TOKEN;

export const GithubProvider = ({ children }) => { / Children means we sent as prop everything in the function
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);

  const fetchUsers = async () => {
    const response = await fetch(`${GITHUB_URL}/users`, {
      headers: { 
        Authorization: `token ${GITHUB_TOKEN}`,
      },
    });
    const data = await response.json();

    setUsers(data);
    setLoading(false);
  }

  return <GithubContext.Provider value={{ / Here we return what we done in function          !!!Double Curly Brakets!!!
    users,
    loading,
    fetchUsers
  }}>
    {children}
  </GithubContext.Provider>
}


export default GithubContext


````





````react

import { useEffect, useContext } from "react"; / We import useContext and don't need useState
import Spinner from "../layout/Spinner";
import UserItem from "../users/UserItem";
import GithubContext from "../../context/github/GithubContext"; 
function UserResults() { / We catch our values comes from returns at GithubContext
  const { users, loading, fetchUsers } = useContext(GithubContext);

  useEffect(() => {
    fetchUsers();
  }, []);

  if (!loading) {
    return (
      <div className="grid grid-cols-1 gap-8 xl:grid-col-4 lg:grid-cols-3 md:grid-cols-2">
        {users.map((user) => (
          <UserItem key={user.id} user={user} />
        ))}
      </div>
    );
  } else {
    return <Spinner />;
  }
}

export default UserResults;


````



````react

import { BrowserRouter as Router, Route, Routes } from "react-router-dom";
import Home from "./pages/Home";
import NotFound from "./pages/NotFound";
import About from "./pages/About";
import Navbar from "./components/layout/Navbar";
import Footer from "./components/layout/Footer";
import { GithubProvider } from "./context/github/GithubContext"; / We import GithubProvider*

function App() {
  return (
    <GithubProvider> {/ Wrap all of contents with GithubProvider
      <Router>
        <div className="flex flex-col justify-between h-screen">
          <Navbar />
          <main className="container mx-auto px-3 pb-12">
            <Routes>
              <Route path="/" element={<Home />} />
              <Route path="/about" element={<About />} />
              <Route path="/notfound" element={<NotFound />} />
              <Route path="/*" element={<NotFound />} />
            </Routes>
          </main>
          <Footer />
        </div>
      </Router>
    </GithubProvider>
  );
}

export default App;


````

![Screenshot_2](https://user-images.githubusercontent.com/66770659/162552908-c9e4ceae-3787-4ee6-a13a-0e8609034054.png)

And finally we got our states(objects) at GithubProvider

