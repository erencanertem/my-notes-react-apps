When we create this app we used tailwindCSS and daisyUI. First of all, install those npm to our project folder

https://tailwindcss.com/docs/installation

https://daisyui.com/

After that, 

````react
App.js

import { BrowserRouter as Router, Route, Routes } from "react-router-dom"; / we install react-router-dom
import Home from "./pages/Home";
import NotFound from "./pages/NotFound";
import About from "./pages/About";
import Navbar from "./components/layout/Navbar";
import Footer from "./components/layout/Footer";

/ We create Component like above.

function App() {
  return (
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
  );
}

export default App;


````



````react

import { FaGithub } from "react-icons/fa";
import { Link } from "react-router-dom";
import { PropTypes } from "prop-types";

function Navbar({ title }) {
  return ( / All classes comes from tailwindCSS and DaisyUI
    <nav className="navbar mb-12 shadow-lg bg-neutral text-neutral-content">
      <div className="container mx-auto">
        <div className="flex-none px-2 mx-2">
          <FaGithub className="inline pr-2 text-3xl" />
          <Link to="/" className="text-lg font-bold align-middle">
            {title}
          </Link>
        </div>
        <div className="flex-1 px-2 mx-2">
          <div className="flex justify-end">
            <Link to="/" className="btn btn-ghost btn-sm rounded-btn">
              Home
            </Link>
            <Link to="/about" className="btn btn-ghost btn-sm rounded-btn">
              About
            </Link>
          </div>
        </div>
      </div>
    </nav>
  );
}

Navbar.defaultProps = {
  title: "Github Finder", / We set title as GithubFinder default.
};

Navbar.propTypes = {
  title: PropTypes.string,
};

export default Navbar;


````



````react
Footer.jsx

function Footer() {
  const footerYear = new Date().getFullYear(); / We took present year and push it our p tag
  return (
    <footer className="footer p-10 bg-gray-500 text-primary-content footer-center">
      <div>
        <p>Copyright &copy; {footerYear} All Rights Reserved</p>
      </div>
    </footer>
  );
}

export default Footer;



````





````react
Components

Home.Jsx

function Home() {
  return (
    <div>
      <h1 className="text-6xl">Welcome</h1>
    </div>
  );
}

export default Home;

About.Jsx

function About() {
  return (
    <div>
      <h1 className="text-6xl mb-4">Github Finder</h1>
    </div>
  );
}

export default About;


NotFound.jsx

import { FaHome } from "react-icons/fa"; / We installed react-icons(fa comes from "Font Awesome")
import { Link } from "react-router-dom";

function NotFound() {
  return (
    <div className="hero">
      <div className="text-center hero-content">
        <div className="max-w-lg">
          <h1 className="text-8xl font-bold mb-8">Oops!</h1>
          <p className="text-5xl mb-8">404 - Page Not Found!</p>
          <Link to="/" className="btn btn-primary btn-lg">
            <FaHome className="mr-2" />
            Back To Home
          </Link>
        </div>
      </div>
    </div>
  );
}

export default NotFound;




````



````react
/ tailwind.config.js

module.exports = {
  content: [
    "./src/**/*.{js,jsx,ts,tsx}",
  ],
  theme: {
    extend: {},
  }, / In below we add daisyUI for use it with tailwind.
  plugins: [require("daisyui")],
}


````

