# 01. Initialize with CRA

```sh
npx create-react-app react-boilerplate
cd react-boilerplate && npm install
```

```sh
echo "SKIP_PREFLIGHT_CHECK=true" > .env && open .env
npm start
```

# 02. Setting up Axios

 * install axios: `npm install axios`
 * examples below
 * setting up `useAxios` Hook

```sh
npm install use-axios-client
```
```js
import { useAxios } from "use-axios-client";

export default function App() {
  const { data, error, loading } = useAxios({
    url: "https://jsonplaceholder.typicode.com/posts/1"
  });

  if (loading || !data) return "Loading...";
  if (error) return "Error!";

  return (
    <div>
      <h1>{data.title}</h1>
      <p>{data.body}</p>
    </div>
  ) 
}
```

# 03. List View

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
      const [post, setPost] = React.useState(null);
      ...
      
      componentDidMount() {
        fetch('http://jsonplaceholder.typicode.com/users')
        .then(res => res.json())
        .then((data) => {
          this.setState({ contacts: data })
        })
        .catch(console.log)
      }

      /*React.useEffect(() => {
        axios.get(`${baseURL}/1`).then((response) => {
          setPost(response.data);
        });
      }, []);*/

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

      render() {
        return (
          <>
            <button onClick={createPost}>Create Post</button>
            <Contacts contacts={this.state.contacts} />
          </>
        )
      }
    }

    export default App
```


# 04. References

 * Axios: [post](https://www.freecodecamp.org/news/how-to-use-axios-with-react/)
 * Consuming API: [post](https://pusher.com/tutorials/consume-restful-api-react/)
 * Setting up Tailwind: [post](https://tailwindcss.com/docs/guides/create-react-app)
 * API Consumtion SmashMag: [post](https://www.smashingmagazine.com/2020/06/rest-api-react-fetch-axios/)
 * NavBar with Tailwind: [post](https://dev.to/franciscomendes10866/create-a-responsive-navbar-using-react-and-tailwind-3768)
 * Using [State](https://stackblitz.com/edit/react-template-hamzeen)
