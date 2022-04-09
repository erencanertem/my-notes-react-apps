```react
function App() {
  const title = "Blog Post";  
  const body = "This is My Blog Post";
  const comments = [
    { id: 1, text: "Comment One" },
    { id: 2, text: "Comment Two" },
    { id: 3, text: "Comment Three" },
  ];
  return (
    <div className="container">
      <h1>{title.toUpperCase()}</h1>  {/ With jsx we set to vars. Not states, For states we use, UseState hook.
      <p>{body}</p>
		{/ Also we can logged here {5 + 5}
      <div className="comments">
        <h3>Comments({comments.length})</h3>
        <ul>
          {comments.map((comment, index) => (
            <li key={index}>{comment.text}</li>
          ))}
        </ul>
      </div>
    </div>
  );
}

export default App;

```

OUTPUT will be like below

![Dynamic-value](https://user-images.githubusercontent.com/66770659/162552387-52a681a2-13b8-491d-a62c-237cb49ba78c.png)
