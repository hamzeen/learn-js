# Boilerplate

  this experiment can be previewed [here](https://codepen.io/hamzeen/pen/VwzrBBy?editors=0010).

```js
const { useState } = React

var user = 'hamzeen';
class AppHeader extends React.Component {
  constructor(props) {
    super(props);
  }
  capitalize(s) {
    return (s && s.length > 0) ? s[0].toUpperCase() + s.slice(1) : '';
  }
  render () {
    return <h1>Hello, <span>{this.capitalize(this.props.name)}!</span></h1>
  }
}

class RepoList extends React.Component {
  constructor(props) {
    super(props);
  }

  render () {
    return (
      <ul className="list-group"> 
        {console.log(this.props)}
        {this.props.repos.map(repo =>
          <li className="list-group-item" id={repo.id} key={repo.id}>
            {repo.name}
          </li>
        )}
      </ul>
    )
  }
}

const App = () => {
  
  const [input, setValue] = useState("");
  const [name, setName] = useState(user);
  const [repos, setRepos] = useState([]);  

  React.useEffect(() => {
    axios.get(`https://api.github.com/users/${name}/repos`)
      .then(response => 
            setRepos(response.data))
      .catch(error => 
            console.log(error));
      }, []);


  getRepos = (newUser) => {
    axios.get(`https://api.github.com/users/${newUser}/repos`)
      .then(response => 
            setRepos(this.sortData(response.data)))
      .catch(error => 
            console.log(error));
  }

  sortData = (data) => {
    console.log(data);
    return data.sort((a, b) => a.name.localeCompare(b.name));
  }
  
  handleInput = (event) => {
    setValue(event.target.value);
  }
  
  updateName = (event) => {
    event.preventDefault();
    setName(input);
    getRepos(input);
    setValue("");
  }
  
  return (
    <div className="box">

      <AppHeader name={name}/>
      
      <form className="form">
        <div class="field">
          <label for="name-1">Update Name</label>
          <div class="control">
            <input type="text" value={input} name="name-1" onChange={handleInput} class="input"/>
          </div>
        </div>
        <div class="field">
          <div class="control">
            <button onClick={updateName} class="button is-dark">Save</button>
          </div>
        </div>
      </form>
      
      <RepoList repos={repos} />
    </div>
  )
}

ReactDOM.render(<App />,
document.getElementById("root"))
```