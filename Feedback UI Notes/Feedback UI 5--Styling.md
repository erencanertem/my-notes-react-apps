

![Screenshot_8](C:\Users\erenc\Desktop\React Notlarım\Feedback UI Notes\Screenshot_8.png)

We add a css and our webpage like above.

```react
import PropTypes from "prop-types";

function Header({ text }) {
  return (
    <header style={{ backgroundColor: "blue", color: "red" }}> // we changed the value like this.
      <div className="container">
        <h2>{text}</h2>
      </div>
    </header>
  );
}

Header.defaultProps = {
  text: "Feedback UI",
};

Header.propTypes = {
  text: PropTypes.string,
};

export default Header;

```

![Screenshot_9](C:\Users\erenc\Desktop\React Notlarım\Feedback UI Notes\Screenshot_9.png)

```react
import PropTypes from "prop-types";

function Header({ text }) {
  const headerStyle = { // Also we can do same thing different way. We send that var to our style attribute.
    backgroundColor: "blue",
    color: "red",
  };
  return (
    <header style={headerStyle}> // { } not {{}}
      <div className="container">
        <h2>{text}</h2>
      </div>
    </header>
  );
}

Header.defaultProps = {
  text: "Feedback UI",
};

Header.propTypes = {
  text: PropTypes.string,
};

export default Header;

```



```react
// There is a different way too
Header.jsx

import PropTypes from "prop-types";

function Header({ text, bgColor, textColor }) { // 3 props for Header Function
  const headerStyle = {
    backgroundColor: bgColor, // These props are came from App.js <Header/> component
    color: textColor,
  };
  return (
    <header style={headerStyle}>
      <div className="container">
        <h2>{text}</h2>
      </div>
    </header>
  );
}

Header.defaultProps = {
  text: "Feedback UI",
};

Header.propTypes = {
  text: PropTypes.string,
};

export default Header;

// App.js

import Header from "./components/Header";

function App() {
  return (
    <>
      <Header bgColor="red" textColor="blue" /> // We set these to value as props.
      <div className="container">
        <h1>My App</h1>
      </div>
    </>
  );
}

export default App;


```



``` react
import PropTypes from "prop-types";

function Header({ text, bgColor, textColor }) {
  const headerStyle = {
    backgroundColor: bgColor,
    color: textColor,
  };
  return (
    <header style={headerStyle}>
      <div className="container">
        <h2>{text}</h2>
      </div>
    </header>
  );
}

Header.defaultProps = { // And we can set default values for that (We Deleted setted value at App.js)
  text: "Feedback UI", 
  bgColor: "rgba(0,0,0,0.4)",
  textColor: "#ff6a95",
};

Header.propTypes = {  
  text: PropTypes.string,
  bgColor : PropTypes.string,
  textColor : PropTypes.string
};

export default Header;

```



![Screenshot_10](C:\Users\erenc\Desktop\React Notlarım\Feedback UI Notes\Screenshot_10.png)