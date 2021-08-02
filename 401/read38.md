# Readings: React 2

## Conditional Rendering

we have two components:
```
function UserGreeting(props) {
  return <h1>Welcome back!</h1>;
}

function GuestGreeting(props) {
  return <h1>Please sign up.</h1>;
}
```
response depands on user status login or not 
we can write it :
```
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <UserGreeting />;
  }
  return <GuestGreeting />;
}

ReactDOM.render(
  // Try changing to isLoggedIn={true}:
  <Greeting isLoggedIn={false} />,
  document.getElementById('root')
);
```
### Element Variables

render a part of the component while the rest of the output doesn’t change.
### Lists and Keys
build collections of elements and include them in JSX using curly braces {}.
this example explane the way :
```
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
   <li key={number.toString()}>
      {number}
);
```
### Forms
#### Controlled Components
In React, mutable state is typically kept in the state property of components, and only updated with setState().
```
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```
#### The file input Tag
Because its value is read-only, it is an uncontrolled component in React. It is discussed together with other uncontrolled components later in the documentation.



#### Resources: 
* [React - Conditional Rendering](https://reactjs.org/docs/conditional-rendering.html)
* [React - Lists & Keys](https://reactjs.org/docs/lists-and-keys.html)
* [React - Forms](https://reactjs.org/docs/forms.html)
* [React - Lifting State](https://reactjs.org/docs/lifting-state-up.html)
* [React - Composition vs Inheritance](https://reactjs.org/docs/composition-vs-inheritance.html)
* [Thinking in React](https://reactjs.org/docs/thinking-in-react.html)
* [Hero Icons](https://www.youtube.com/watch?v=cVa1UiKPJN8)
* [React - Comprehensive Guide](https://ui.dev/reactjs-tutorial-a-comprehensive-guide-to-building-apps-with-react/)
* [Heroicons](https://heroicons.com/)

