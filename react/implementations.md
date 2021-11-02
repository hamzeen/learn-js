# Initialize with CRA

```sh
npx create-react-app react-boilerplate
cd react-boilerplate && npm install
```

```sh
echo "SKIP_PREFLIGHT_CHECK=true" > .env && open .env
npm start
```
# List View

```js
    // src/components/users.js
    import React from 'react'

    const Users = ({ contacts }) => {
      return (
        <div>
          <center><h1>Contact List</h1></center>
          {contacts.map((contact) => (
            <div class="card">
              <div class="card-body">
                <h5 class="card-title">{contact.name}</h5>
                <h6 class="card-subtitle mb-2 text-muted">{contact.email}</h6>
                <p class="card-text">{contact.company.catchPhrase}</p>
              </div>
            </div>
          ))}
        </div>
      )
    };

    export default Users
```

```js
    // src/App.js

    import React, { Component } from 'react'
    import Contacts from './components/contacts'

    class App extends Component {
      ...
      
      componentDidMount() {
        fetch('http://jsonplaceholder.typicode.com/users')
        .then(res => res.json())
        .then((data) => {
          this.setState({ contacts: data })
        })
        .catch(console.log)
      }

      render() {
        return (
          <Contacts contacts={this.state.contacts} />
        )
      }
    }

    export default App
```

# Setting up Axios for HTTP Calls

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
        title: "Hello World Post", 
        body: "new post content"
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
