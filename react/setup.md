## 01. Initialize with CRA

```sh
npx create-react-app react-boilerplate
cd react-boilerplate && npm install
```

```sh
echo "SKIP_PREFLIGHT_CHECK=true" > .env && open .env
npm start
```

## 02. Setup Libraries

Axios is a promise based http client library. it's ismerphic works on node js backend as well as front-end projects.
in the front-end uses xmlhttp reqeust. You can use use-axios for syntactic sugar in React.js projects.

```sh
npm install axios use-axios-client
```  


### axios example
```js
      axios
        .post(baseURL, {
          title: "Hello World Post", 
          body: "new post content"
        })
        .then((response) => {
          setPost(response.data);
        })
        .catch(error => {
            console.log(error)
        });

      axios
        .get(`https://api.github.com/users/${user}/repos`)
        .then(response => 
            setRepos(this.sortData(response.data)))
        .catch(error => 
            console.log(error));
```


### use-axios hook example

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

## 03. hitchhiker's guide

 ### iterate an array
```js
    // src/components/users.js
    import React from 'react'

    const Users = ({ users }) => {
      return (
        <div>
          <center><h1>Users List</h1></center>
          {users.map((user) => (
            <div class="card">
                <h5 class="card-title">{user.name}</h5>
                <h6 class="card-subtitle mb-2 text-muted">{user.email}</h6>
                <p class="card-text">{user.company.catchPhrase}</p>
            </div>
          ))}
        </div>
      )
    };

    export default Users
```

 ### hooks
```js
    // src/App.js

    import React, { Component } from 'react'
    import Contacts from './components/contacts'

    class App extends Component {
      const [post, setPost] = React.useState(null);
      const [contacts, setContacts] = React.useState([]);
      
      componentDidMount() {
        fetch('http://jsonplaceholder.typicode.com/users')
        .then(res => res.json())
        .then((data) => {
          this.setContacts(data)
        })
        .catch(console.log)
      }

      /*React.useEffect(() => {
        axios.get(`${baseURL}/1`).then((response) => {
          setPost(response.data);
        });
      }, []);*/

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
 ### prevent re-renders on functional comps
`const factorial = useMemo(() => factorialOf(number), [number]);`

# 04. More Reads

 * Axios: [post](https://www.freecodecamp.org/news/how-to-use-axios-with-react/)
 * Consuming API: [post](https://pusher.com/tutorials/consume-restful-api-react/)
 * Setting up Tailwind: [post](https://tailwindcss.com/docs/guides/create-react-app)
 * API Consumtion SmashMag: [post](https://www.smashingmagazine.com/2020/06/rest-api-react-fetch-axios/)
 * NavBar with Tailwind: [post](https://dev.to/franciscomendes10866/create-a-responsive-navbar-using-react-and-tailwind-3768)
 * Using [State](https://stackblitz.com/edit/react-template-hamzeen)
