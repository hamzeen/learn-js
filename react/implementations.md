# Initialize with CRA

```sh
npx create-react-app react-boilerplate
cd react-boilerplate && npm install
```

```sh
echo "SKIP_PREFLIGHT_CHECK=true" > .env && open .env
npm start
```

# HTTP Calls using Axios

 * Using [State](https://stackblitz.com/edit/react-template-hamzeen)

 * install axios: `npm install axios`

 * Invoke a REST API via Axios:  


```js
import axios from "axios";
import React from "react";

const baseURL = "https://jsonplaceholder.typicode.com/posts";

export default function App() {
  const [post, setPost] = React.useState(null);

  React.useEffect(() => {
    axios.get(`${baseURL}/1`).then((response) => {
      setPost(response.data);
    });
  }, []);

  function createPost() {
    axios
      .post(baseURL, {
        title: "Hello World!", 
        body: "This is a new post."
      })
      .then((response) => {
        setPost(response.data);
      });
  }

  if (!post) return "No post!";
  return (
    <div>
      <h1>{post.title}</h1>
      <p>{post.body}</p>
      <button onClick={createPost}>Create Post</button>
    </div>
  );
}
```
