

![Screenshot_8](https://user-images.githubusercontent.com/66770659/162552456-c1b68216-5e07-4173-a703-c8238da08b97.png)


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

![Screenshot_9](https://user-images.githubusercontent.com/66770659/162552461-3539bdbe-df50-4842-963e-3ce08a1dbb75.png)

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


![Screenshot_10](https://user-images.githubusercontent.com/66770659/162552463-15b767b8-2fee-4ac1-bfd8-1f33544e0893.png)

