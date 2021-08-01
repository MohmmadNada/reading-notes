# Readings: React 1

## ES6 Syntax and Feature Overview
### Variables and constant feature comparison


| Lab Keyword       | Scope |Hoisting |Can Be Reassigned	 |Can Be Redeclared |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| var  | Function scope	| Yes | Yes | Yes |
| let  | Block scope		| No | Yes | No |
| const  | Block scope		| No | No | No |

### Arrow functions
> Note: Arrow functions do not have their own this, **No Scope**
> Note: Arrow functions do not have prototypes.
> Note: Arrow functions cannot be used for constructors.
> Note: Arrow functionsNote: Arrow functions should not be used as object methods.

```
let func = (a) => {} // parentheses optional with one parameter
let func = (a, b, c) => {} // parentheses required with multiple parameters
```

### Template literals
#### Concatenation/string interpolation

```
let str = `Release Date: ${date}`
```
#### Multi-line strings
```
let str = `This text
            is on
            multiple lines`
```
### Implicit returns

let func = (a, b, c) => a + b + c // curly brackets must be omitted

### Key/property shorthand
ES6 introduces a shorter notation for assigning properties to variables of the same name.

```let obj = {
  a,
  b,
}
``` 
ths mean a = a and b = b 

### Method definition shorthand without function keyword
The function keyword can be omitted when assigning methods on an object.

```
let obj = {
  a(c, d) {},
  b(e, f) {},
}
obj.a() // call method a

```
### Destructuring (object matching)
```
let {a, b, c} = obj  
```
### Array iteration (looping)

```
for (let i of arr) {
  console.log(i)
}
```
### Default parameters
```
let func = (a, b = 2) => {
  return a + b
} // if a and b == 2 return 
```
### Classes/constructor functions
class syntax on top of the prototype-based constructor function.


```
class Func {
  constructor(a, b) {
    this.a = a
    this.b = b
  }

  getSum() {
    return this.a + this.b
  }
}

let x = new Func(3, 4)
x.getSum() // returns 7

```

### Modules - export/import
export and import code between files.
as html file : 

```
<script src="export.js"></script>
<script type="module" src="import.js"></script>

```
js export 
```
// func , ibj and x are var names 
export {func, obj, x}
```
## React 
### Hello World
do it with rect : 
```
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);
```

### Knowledge Level Assumptions

**React **: React is a JavaScript library.
### Introducing JSX

keep in your mind JSX 
```const element = <h1>Hello, world!</h1>;```

JSX produces React “elements”.
#### Embedding Expressions in JSX
this example explane alot :
```
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);

ReactDOM.render(
  element,
  document.getElementById('root')
);
```
#### JSX is an Expression Too
you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions.

#### Specifying Attributes with JSX
add atributes in html tag by : 
1. string `<div tabIndex="0"></div>`
2. curly bracing `src={user.avatarUrl}`

> Big Note: React DOM uses camelCase property naming convention instead of HTML attribute names.

#### JSX Represents Objects
uses React.createElement()
 ```
    const element = (
    <h1 className="greeting">
        Hello, world!
    </h1>
    );
```
```
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```
```
// Note: this structure is simplified
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};
```

### Rendering Elements into the DOM
```const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```
note: remember root is an id 

### Updating the Rendered Element

important note: React elements are immutable(like constant ). Once you create an element, you can’t change its children or attributes. 
```
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(element, document.getElementById('root'));
}

setInterval(tick, 1000);
```
it is show in the UI Clock

It is 12:36:48 AM.

### React Only Updates What’s Necessary
by compare between the element and his childs

## Components and Props

### Function and Class Components

```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
it is return react element 

### Rendering a Component
When React sees an element representing a user-defined component, it passes JSX attributes and children to this component as a single object. We call this object “props”.

### Composing Components
see the example first 
```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Sara" />
      <Welcome name="Cahal" />
      <Welcome name="Edite" />
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```

create an App component that renders Welcome many times. 

### Extracting Components
```
function Comment(props) {
  return (
    <div className="Comment">
      <div className="UserInfo">
        <img className="Avatar"
          src={props.author.avatarUrl}
          alt={props.author.name}
        />
        <div className="UserInfo-name">
          {props.author.name}
        </div>
      </div>
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}
```
extract Avatar:
```
function Avatar(props) {
  return (
    <img className="Avatar"
      src={props.user.avatarUrl}
      alt={props.user.name}
    />
  );
}
```
The Avatar doesn’t need to know that it is being rendered inside a Comment. This is why we have given its prop a more generic name: user rather than author.

### Props are Read-Only
