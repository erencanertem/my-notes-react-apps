Header.jsx

``` react
function Header() {
  return ( // A new Header Component--- Yeni bir Header Componenti
    <header>
      <div className="container">
        <h2>Feedback UI</h2>
      </div>
    </header>
  );
}

export default Header;

```



App.Js

``` react
import Header from "./components/Header";

function App() {
  return (
    <>
      <Header />
      <div className="container">
        <h1>My App</h1>
      </div>
    </>
  );
}

export default App;

```

![Screenshot_24](C:\Users\erenc\Desktop\React Notlarım\Feedback UI Notes\Screenshot_24.png)

---on above Feedback UI comes from Header Component, MyApp comes from App.JS

Header.Jsx

```react

function Header(props) { // We added props as param to our function
    // We can also use Header({text}) for add param to our function
  return (
    <header>
      <div className="container">
        <h2>{props.text}</h2> // We added text props for our page(Comes from App.JS)
          // Like above we can use just {text} like above.
          // But we have to use same syntax (props) and {props.text} or ({text}) and 			// {text} == 
      </div>
    </header>
  );
}

export default Header;


```



App.JS

```react
import Header from "./components/Header";

function App() {
  return (
    <>
      <Header text="Hello World" /> // That text is a props for Header Component. Used the code block above.
      <div className="container">
        <h1>My App</h1>
      </div>
    </>
  );
}

export default App;

```

After that change, here it is! our new page.

![Screenshot_7](C:\Users\erenc\Desktop\React Notlarım\Feedback UI Notes\Screenshot_7.png)



```react
Header.JSX
import PropTypes from "prop-types";

function Header({ text }) {
  return (
    <header>
      <div className="container">
        <h2>{text}</h2>
      </div>
    </header>
  );
}
// If we didn't pass a prop to our Header component at App.js we can set default text string with defaultProps

Header.defaultProps = { 
  text: "Feedback UI",
};

//We can set the propType like at below, we can set string, boolean, int,etc.
// also we can add isRequired method. 

Header.propTypes = {
  text : PropTypes.string
}

export default Header;

App.Js

import Header from "./components/Header";

function App() {
  return (
    <>
      <Header />
      <div className="container">
        <h1>My App</h1>
      </div>
    </>
  );
}

export default App;

```

![Screenshot_6](C:\Users\erenc\Desktop\React Notlarım\Feedback UI Notes\Screenshot_6.png)