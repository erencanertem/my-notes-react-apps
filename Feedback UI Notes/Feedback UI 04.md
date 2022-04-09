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

![Screenshot_24](https://user-images.githubusercontent.com/66770659/162552433-81ab0fd1-c345-4a24-ade3-bacd70af3161.png)


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


![Screenshot_7](https://user-images.githubusercontent.com/66770659/162552438-63661a04-ec66-42ef-97d2-efe8aa928b6b.png)



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

![Screenshot_6](https://user-images.githubusercontent.com/66770659/162552444-886ff32f-88c6-4847-9bcd-967f803ee40a.png)
