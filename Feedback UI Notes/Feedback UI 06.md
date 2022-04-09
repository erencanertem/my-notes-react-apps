``` react
// We Created new component FeedbackItem.js

import { useState } from "react"; // Use State eklendi.

function FeedbackItem() {
  const [rating, setRating] = useState(7); // rating default olarak (7) alacak
  const [text, setText] = useState("This is and example of a feedback item");//text default string alır.
    // Yukarıda 7 ve "This is and example of a feedback item" state olur.

  return (
    <div className="card">
      <div className="num-display">{rating}</div>
      <div className="text-display">{text}</div>
    </div>
  );
}

export default FeedbackItem;

```

![Screenshot_11](https://user-images.githubusercontent.com/66770659/162552491-5dba25ec-eb65-4dea-bb91-8549cabd5d4b.png)



``` react

import { useState } from "react";

function FeedbackItem() {
  const [rating, setRating] = useState(7);
  const [text, setText] = useState("This is and example of a feedback item");

  const handleClick = () => {
    // Bir buton ekleyip ratingi 10 yapmak için işlem yapalım.
    rating = 10; // bu geçersiz olacaktır.
    setRating(10) // Geçerli olacak. Bu sebeple react ta useState yapısı kullanırız
  };

  return (
    <div className="card">
      <div className="num-display">{rating}</div>
      <div className="text-display">{text}</div>
      <button onClick={handleClick}>Click</button> {// onClick eventiyle button oluşturduk.
    </div>
  );
}

export default FeedbackItem;
```

![Screenshot_12](https://user-images.githubusercontent.com/66770659/162552494-88737cca-43c8-4110-8ade-ad12cdea3f08.png)


````react
import { useState } from "react";

function FeedbackItem() {
  const [rating, setRating] = useState(7);
  const [text, setText] = useState("This is and example of a feedback item");

  const handleClick = () => {
    setRating(() => {
      return 10;  // Bu şekilde arrow function ile yine aynı şekilde 10 yazdırabiliriz.
    });
  };
    
  const handleClick = () => {
      setRating((prev) => {  // Bu şekilde olursa eğer counter app gibi bir önceki değer + 1 şeklinde devam edecektir.
          console.log(prev)
          return prev + 1
      })
  }

  return (
    <div className="card">
      <div className="num-display">{rating}</div>
      <div className="text-display">{text}</div>
      <button onClick={handleClick}>Click</button>
    </div>
  );
}

export default FeedbackItem;

````

