``` react

function App() {
  const title = "Blog Post";
  const body = "This is My Blog Post";
  const comments = [
    { id: 1, text: "Comment One" },
    { id: 2, text: "Comment Two" },
    { id: 3, text: "Comment Three" },
  ];

  const loading = false;
  const showComments = true; / We logged showComment as yes or no with ternary operator query. If we set as false, our log we'll be no instead yes.

  if (loading) return <h1>Loading...</h1>;
  return (
    <div className="container">
      <h1>{title.toUpperCase()}</h1>
      <p>{body}</p>

      {showComments ? "yes" : "no"}

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

![conditionals](C:\Users\erenc\Desktop\React Notlarım\Feedback UI Notes\conditionals.png)

``` react

function App() {
  const title = "Blog Post";
  const body = "This is My Blog Post";
  const comments = [
    { id: 1, text: "Comment One" },
    { id: 2, text: "Comment Two" },
    { id: 3, text: "Comment Three" },
  ];

  const loading = false;
  const showComments = true;  / This time we add div with comments class into ternary operator. Like above if we set is false, div not show and only log "no".

  if (loading) return <h1>Loading...</h1>;
  return (
    <div className="container">
      <h1>{title.toUpperCase()}</h1>
      <p>{body}</p>

      {showComments ? (
        <div className="comments">
          <h3>Comments({comments.length})</h3>
          <ul>
            {comments.map((comment, index) => (
              <li key={index}>{comment.text}</li>
            ))}
          </ul>
        </div>
      ) : (
        "no" {/ In case of false, there is no something to show, so we can leave here null.
      )}
    </div>
  );
}

export default App;


```

![conditionals-2](C:\Users\erenc\Desktop\React Notlarım\Feedback UI Notes\conditionals-2.png)



``` react
{showComments && (   / We can use && operator for get return when its only true 
        <div className="comments">
          <h3>Comments({comments.length})</h3>
          <ul>
            {comments.map((comment, index) => (
              <li key={index}>{comment.text}</li>
            ))}
          </ul>
        </div>
      )}
```





``` react

function App() {
  const title = "Blog Post";
  const body = "This is My Blog Post";
  const comments = [
    { id: 1, text: "Comment One" },
    { id: 2, text: "Comment Two" },
    { id: 3, text: "Comment Three" },
  ];

  const loading = false;
  const showComments = true;

  const commentBlock = (     / We define a commentBlock var and send the values from the div 
    <div className="comments">
      <h3>Comments({comments.length})</h3>
      <ul>
        {comments.map((comment, index) => (
          <li key={index}>{comment.text}</li>
        ))}
      </ul>
    </div>
  );

  if (loading) return <h1>Loading...</h1>;
  return (
    <div className="container">
      <h1>{title.toUpperCase()}</h1>
      <p>{body}</p>

      {showComments && commentBlock} {/ Like above we did a query for showComments. Again, div will be displayed, because we set showComments true. 
    </div>
  );
}

export default App;
```

