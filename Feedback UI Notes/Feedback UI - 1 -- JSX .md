``` react

// JSX kullanılmadan yapılan bir sayfa --- Not Using JSX

import React from "react";

function App() {
  return React.createElement(
    "div",
    { className: "container" },
    React.createElement("h1", {}, "My App")
  );
}

export default App;


// JSX kullanılarak yazılan bir syntax --- With JSX

function App() {
  return (
    <div className="container">
      <h1>My App</h1>
    </div>
  );
}

export default App;


```

 

