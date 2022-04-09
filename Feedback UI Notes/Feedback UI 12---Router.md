````react

// Using Router with npm

import { v4 as uuidv4 } from "uuid"
import { BrowserRouter as Router, Routes, Route } from "react-router-dom"  // at V6, we need to import Routes also
import { useState } from "react"; 
import Header from "./components/Header";
import FeedbackList from "./components/FeedbackList";
import FeedbackData from "./data/FeedbackData";
import FeedbackStats from "./components/FeedbackStats";
import FeedbackForm from "./components/FeedbackForm";
import AboutPage from "./pages/AboutPage"

function App() {
  const [feedback, setFeedback] = useState(FeedbackData);

  const deleteFeedback = (id) => {
    if (window.confirm("Are you sure you want to delete?")) {
      setFeedback(feedback.filter((item) => item.id !== id));
    }

  }

  const addFeedback = (newFeedback) => {
    newFeedback.id = uuidv4()
    setFeedback([newFeedback, ...feedback])
  }

  return (
    <Router>
      <Header />
      <div className="container">
        <Routes> { // With V6 we need wrap our Route with Routes
                // We have to change as element and like syntax below}
          <Route exact path="/" element={
            <>
              <FeedbackForm handleAdd={addFeedback} />
              <FeedbackStats feedback={feedback} />
              <FeedbackList feedback={feedback} handleDelete={deleteFeedback} />

            </>
          }>
          </Route>

          <Route path="/about" element={<AboutPage />} />
        </Routes>
      </div>
    </Router>
  );
}

export default App;

````





````react

import { FaQuestion } from "react-icons/fa";
import { Link } from "react-router-dom";

function AboutIconLink() {
  return (
    <div className="about-link">
      <Link to="/about">
        <FaQuestion size={30} />
      </Link>
    </div>
      
      also
      {// We can do it this way.}
      // We can also use a tag instead Link but, if we use a tag,then our browser refresh all the time when we click to Question Mark or Back to Home Button.
     <div className="about-link">
      <Link
        to={{
          pathname: "/about",
          search: "?sort=name",
          hash: "#hello",
        }}
      >
        <FaQuestion size={30} />
      </Link>
    </div>
      
  );
}

export default AboutIconLink;


````

![Screenshot_18](C:\Users\erenc\Desktop\React Notlarım\Feedback UI Notes\Screenshot_18.png)

We can see our changes at search bar.

