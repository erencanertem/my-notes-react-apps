
![Screenshot_13](https://user-images.githubusercontent.com/66770659/162552510-bb7bb9f3-b4b5-44f6-9b3a-f35f594be06a.png)

```react

App.js

import { useState } from "react";
import Header from "./components/Header";
import FeedbackList from "./components/FeedbackList";
import FeedbackData from "./data/FeedbackData"; // FeedbackData.js file imported.
	// inside of it, id,text and rating
function App() {
  const [feedback, setFeedback] = useState(FeedbackData); // 
    // We will use useState for change feedback

  return (
    <>
      <Header />
      <div className="container">
        <FeedbackList feedback={feedback} /> // we sent feedback as prop.
      </div>
    </>
  );
}

export default App;

```



```react
FeedbackList.jsx

import FeedbackItem from "./FeedbackItem";

function FeedbackList({ feedback }) { // thats prop. we set this at app.js.
  if (!feedback || feedback.length === 0) {
    return <p>No Feedback Yet!</p>;
  }
  return (
    <div className="feedback-list">
      {feedback.map((item) => ( // this (item) is param.
        <FeedbackItem key={item.id} item={item} /> 
      ))}
    </div>
  );
}

export default FeedbackList;
```

 

``` react
FeedbackItem.jsx

function FeedbackItem({ item }) { // item is prop. We set it at FeedbackList when we add FeedbackItem component.
  return (
    <div className="card">
      <div className="num-display">{item.rating}</div>
      <div className="text-display">{item.text}</div>
    </div>
  );
}

export default FeedbackItem;

```

