``` react
we created a new component named Card.jsx

function Card({ children }) { // is a props comes from react.
  return <div className="card">{children}</div>;
}

// With this way we can use Card anywhere we want

export default Card;

```

``` react

FeedbackItem.jsx

import Card from "./shared/Card";

function FeedbackItem({ item }) {
  return (	// We changed div as Card and we used children prop for move HTML to Card.jsx
    <Card> // we set class at Card component
      <div className="num-display">{item.rating}</div>
      <div className="text-display">{item.text}</div>
    </Card>
  );
}

export default FeedbackItem;
```

![Screenshot_14](C:\Users\erenc\Desktop\React Notlarım\Feedback UI Notes\Screenshot_14.png)



``` react

import Card from "./shared/Card";

// Conditinal Class 

function FeedbackItem({ item }) {
  return (
    <Card reverse={true}> // We Set reverse prop as true-- We add these class at index.css

      <div className="num-display">{item.rating}</div>
      <div className="text-display">{item.text}</div>

​    </Card>
  );
}

export default FeedbackItem;

```



````react

function Card({ children, reverse }) { // in here, it depends to reverse(true or false), if its true, then it will be added as class
  return <div className={`card ${reverse && "reverse"}`}>{children}</div>;
}

export default Card;


````

![Screenshot_15](C:\Users\erenc\Desktop\React Notlarım\Feedback UI Notes\Screenshot_15.png)

``` react
function Card({ children, reverse }) {
    
    // Conditional Styling, it depends again reverse(True or false)
    
  return (
    <div
      className="card"
      style={{
        backgroundColor: reverse ? "rgba(0,0,0,0.4)" : "#fff",
        color: reverse ? "#fff" : "rgba(0,0,0,0.4)",
      }}
    >
      {children}
    </div>
  );
}

export default Card;

```



