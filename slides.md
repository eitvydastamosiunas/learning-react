---
theme: ./theme
background: /images/cover-start.gif
background-position-x: 200%
highlighter: shiki
hideInToc: true
title: Day 1
---

# Day 1

## React - the basics

---
hideInToc: true
---

# Agenda

<Scroller>
    <Toc />
</Scroller>

---

# Breef history of react
 - 2004 - [ECMAScript For XML](https://svn.wso2.org/repos/wso2/tags/carbon/0.1alpha/mashup/java/xdocs/e4xquickstart.html)
 - 2010 - [XHP](https://github.com/phplang/xhp)
 - 2011 - [FaxJS by Jordan Walke](https://github.com/jordwalke/FaxJs)
 - 2012 - Used in FaceBook and Instagram
 - 2013 - [React Open source release](https://www.youtube.com/watch?v=GW0rj4sNH2w)
 - 2015 - React Stable version, React Native releases
 - 2019 - [In v16.8 the Hooks are introduced](https://reactjs.org/blog/2019/02/06/react-v16.8.0.html)
---

<img style="width: 350px;" src="/images/jsx-reactions.png" />
::right::
---

# Popularity
---
title: StackOverflow 
layout: iframe
url: https://insights.stackoverflow.com/trends?tags=reactjs%2Cvue.js%2Cangular%2Cangularjs%2Cknockout.js%2Cjquery
preload: false
hideInToc: true
---

---
hideInToc: true
---

StateOfJS
<img style="width: 500px;" src="https://stateofx-images.netlify.app/captures/js2021/en-US/front_end_frameworks_experience_marimekko.png">

[Source](https://2021.stateofjs.com/en-US/libraries/front-end-frameworks/)
---

Google
<img style="width: 700px;" src="/images/react-google.png">

[Source](https://trends.google.com/trends/explore?cat=1227&date=today%205-y&q=react,jquery,angular,vue)
---

# What is React?
A JavaScript library for building user interfaces. 

- Declarative
- Component-Based
- Immutable

::right::

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/React-icon.svg/2300px-React-icon.svg.png" />

---
layout: two-cols
---

# Component-Based
Build encapsulated components that manage their own state, then compose them to make complex UIs.

Since component logic is written in JavaScript instead of templates, you can easily pass rich data through your app and keep state out of the DOM.

<img style="width: 600px;"  src="/images/react-component.png" />
---

# Declarative
Developer should focus on data transformation and leave DOM manipulation for the react.

<img style="width: 550px;" src="/images/virtual-dom.png" />
---

# Immutable 
The existing data should not be mutated, but instead new state should be created.

<img style="width: 600px;" src="https://velopert.com/wp-content/uploads/2017/12/react-love-immutable.png">
---




# JSX syntax
JSX is syntax extension to JavaScript. 
- Describes what the UI should look like. 
- Comes with the full power of JavaScript.
- Produces React “elements”

Example: JSX syntax
```jsx 
const element = <h1 className="greeting">Hello, world!</h1>;
```
is translated to

```js 
  const element = React.createElement(
    'h1',
    {className: 'greeting'},
    'Hello, world!'
  );
```
---

# JSX syntax
<section class="grid grid-cols-2 gap-4">

  ```jsx {2}
  const name = 'Josh Perez';
  const element = <h1>Hello, {name}</h1>;
  ```
  Embedding Expressions in JSX.

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx {6|8|all}
  function formatName(user) {
    return user.firstName + ' ' + user.lastName;
  }
  function getGreeting(user) {
    if (user) {
      return <h1>Hello, {formatName(user)}!</h1>;
    }
    return <h1>Hello, Stranger.</h1>;
  }
  ```
  JSX is an Expression Too.

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  const element = <img src={user.avatarUrl}></img>;
  ```
  Specifying Attributes with JSX.

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx {3|4|all}
  const element = (
    <div>
      <h1>Hello!</h1>
      <h2>Good to see you here.</h2>
    </div>
  );
  ```
  Specifying Children with JSX.

</section>
---

# Elements
Elements are the smallest building blocks of React apps.
Unlike browser DOM elements, React elements are plain objects, and are cheap to create. React DOM takes care of updating the DOM to match the React elements.

Let’s say there is a div element somewhere in your HTML file
```html
<div id="root"></div>
```
To render a React element, first pass the DOM element to ReactDOM.createRoot(), then pass the React element to root.render()
```jsx {1-3|4|5|all}
const root = ReactDOM.createRoot(
  document.getElementById('root')
);
const element = <h1>Hello, world</h1>;
root.render(element);
```

[Task: Fix application to display user info](https://codepen.io/gaearon/pen/PGEjdG?editors=1010)
---

# Components
Components let you split the UI into independent, reusable pieces, and think about each piece in isolation. 

Function component
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
Class component
```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```
Components must be defined by starting with capital letter. This is required for React to distinguish them from standard HTML elements.

---

# Reusing the components
Components can refer to other components in their output. This lets us use the same component abstraction for any level of detail. Components are designed to be isolated so always try to split big parts into smaller components.

```jsx {1-3|8-10|all}
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
```
---

# Props
When React sees an element representing a user-defined component, it passes JSX attributes and children to this component as a single object. Props are treated as readonly. This allows React to determine the difference and let know if the props are different.

<section class="grid grid-cols-2 gap-4">

  ```jsx
  <MyComponent message="hello world">
  ```
  Passing props as a string

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  let greeting = "Hello world!";
  return <MyComponent message={greeting}>
  ```
  Passing props as an object

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  <MyComponent foo={1 + 2 + 3 + 4}>
  ```
  Passing props as an evaluation

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  function NumberDescriber(props) {
    let description;
    if (props.number % 2 === 0) {
      description = <strong>even</strong>
    } else {
      description = <i>odd</i>
    }
    return <div>{props.numer} is an {description} number</div>
  }
  ```
  Using props as a for condition inside component.

</section>

---

# Props

<section class="grid grid-cols-2 gap-4">

  ```jsx
  <MyTextBox autocomplete />
  ```
  Props with no value defaults to true

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  function App1() {
    return <Greeting firstName="Ben" lastName="Hector" />;
  }

  function App2() {
    const props = {firstName: 'Ben', lastName: 'Hector'};
    return <Greeting {...props} />;
  }
  ```
  Passing props using spread operator

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  function deleteUser(id) {
    const index = users.findIndex(x => x.id === id);
    setUsers(users.splice(index))
  }
  return <User deleteCalback={deleteUser} userId={user.id}>
  ```
  Passing props a callback function
</section>

---

# State 
The state is used to create encapsulated components which could have its own data and how its changing. When then model has changed React ensures that necessary DOM elements get updated. 

In React v16.8 the hooks were introduced. They let to use state and other React features without writing a class. As the developers are encouraged to write function components the class components are still supported.

There is a big difference how the state management and lifecycle works in class and function components. We will primarely primarily focus on the function components but it is important to understand how class component works aswell.

---

# State management and Lifecycle in Class components
```jsx {4|12-16|6-8|9-11|17-22|all}
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }
  componentDidMount() {
    this.timerID = setInterval(() => this.tick(), 1000);
  }
  componentWillUnmount() {
    clearInterval(this.timerID);
  }
  tick() {
    this.setState({
      date: new Date()
    });
  }
  render() {
    return (
      <div><h2>It is {this.state.date.toLocaleTimeString()}.</h2></div>
    );
  }
}
```
---

# Rules of state management and Lifecycle in Class components
- The default state must be defined in class constructor.
- The componentDidMount method is called after the component output is rendered into DOM
- The componentWillUnmount is called when Clock component is removed from the DOM.
- To update the state this.setState method should be used.
- All event functions which are used should be binded.
- State and functions are accessed by using this keyword.

```jsx 
contructor(props) {
  this.state = {address: ''};
  this.onTextChanged = this.onTextChanged.bind(this);
}
...
function onTextChanged(e) {
  e.preventDefault();
  this.setState( { address: e.target.value  });
}
...
<input type='text' onChange={onTextChanged} value={this.state.address}>
```
---

<iframe width="800" height="500" src="https://www.youtube.com/embed/dpw9EHDh2bM?start=1061&end=268" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


---

# State management and Lifecycle in function components
```jsx {2|9-11|5|6|4-7|13-15|all}
function Clock(props) {
  const [date, setDate] = React.useState(new Date());

  React.useEffect(() => {
    var timerID = setInterval(() => tick(), 1000);
    return () => clearInterval(timerID);
  })

  function tick() {
    setDate(new Date());
  }

  return (
    <div><h2>It is {this.state.date.toLocaleTimeString()}.</h2></div>
  );
}
```

---

# Rules of state management and Lifecycle in function components
The hooks were introduced in React v16.8 and allowed to use state and other React features without writing a class.
- Hooks do provide a more direct API to the React concepts.
- The same hook can be used more than once.
- Hooks are executed in order from top to the bottom.
- Hooks reduce the boilerplate of class components.
- Developers can write own hooks and reuse accross the many components (useYourHookName)
- Function components are easier to test.

```jsx
function Address() {
  const [address, setAddress] = React.useState('');
  function onTextChanged(e) {
    e.preventDefault();
    setAddress(e.target.value);
  }
  return <input type='text' onChange={onTextChanged} value={this.state.address} />
}
```
---

# useState
This hook allows to add the local state inside functional component. React will preserve its state between re-renders. 
The hook is the function which is taking the default value as a parameter and returning pair of:
- the current state value
- a function which lets to update the state

This hook can use objects, arrays or other primitive types.

```jsx {3-5|all}
  function ExampleWithManyStates() {
  // Declare multiple state variables!
  const [age, setAge] = React.useState(42);
  const [fruit, setFruit] = React.useState('banana');
  const [todos, setTodos] = React.useState([{ text: 'Learn Hooks' }]);
  // ...
}
```

---

# useEffect
Data fetching, subscriptions, or manually changing the DOM from React components are called “side effects” (“effects”) because they can affect other components and can’t be done during rendering.

The <b>useEffect</b> serves the same purpose as <i>componentDidMount</i>, <i>componentDidUpdate</i>, and <i>componentWillUnmount</i> in React classes, but unified into a single API.

<section class="grid grid-cols-2 gap-4">

  ```jsx
  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });
  ```
  Without cleanup and runs on every render 

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx {7-9|5,|11|all}
  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    // Specify how to clean up after this effect:
    return function cleanup() {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
    // Only re-subscribe if props.friend.id changes
  }, [props.friend.id]); 
  ```
  With cleanup, useEffect will be invoked again only if friend id changes 

</section>

---

# Events
Handling events with React elements is very similar to handling events on DOM elements. There are some syntax differences.

<section class="grid grid-cols-2 gap-4">

  ```html
  <button onclick="activateLasers()">
    Activate Lasers
  </button>
  ```
  HTML 

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  <button onClick={activateLasers}>
    Activate Lasers
  </button>
  ```
  - React events are named using camelCase, rather than lowercase.
  - With JSX you pass a function as the event handler, rather than a string.

</section>
---

Another difference is that you cannot return false to prevent default behavior in React. You must call preventDefault explicitly. For example, with plain HTML, to prevent the default form behavior of submitting, you can write:

<section class="grid grid-cols-2 gap-4">

  ```html
 <form onsubmit="console.log('You clicked submit.'); return false">
    <button type="submit">Submit</button>
  </form>
  ```
  HTML 

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  function Form() {
    function handleSubmit(e) {
      e.preventDefault();
      console.log('You clicked submit.');
    }

    return (
      <form onSubmit={handleSubmit}>
        <button type="submit">Submit</button>
      </form>
    );
  }
  ```
  React

</section>

---

Inside a loop, it is common to want to pass an extra parameter to an event handler. For example, if id is the row ID, either of the following would work.

```jsx{2-5|10|all}
function Rows() {
  function deleteRow(id, e) {
    e.preventDefault();
    ...
  }

  return(
    <div>
      {rows.map(row => {
        return <button onClick={(e) => deleteRow(id, e)}>Delete Row</button>
      })}
    </div>
  )
}
```

Note! It is Ok to use arrow function within the loop, but is better to avoid its usage in single components. In most cases, this is fine. However, if this callback is passed as a prop to lower components, those components might do an extra re-rendering. 

---

Mostly used events

<section class="grid grid-cols-2 gap-4">

  ```jsx
  function onClick(e) {
    e.preventDefault();
  }

  <input type="submit" onClick={onClick}>
  ```
  Occurs when the user clicks on an element

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  function onTextChanged(e) {
    e.preventDefault();
  }
  <input type="text" onChange={onTextChanged}>
  ```
  Occurs when the value of an element has been changed

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  function onFocus(e) {
    e.preventDefault();
  }
  <input type="text" onFocus={onFocus}>
  ```
  Occurs when an element gets focus

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
   function saveInput(e) {
    e.preventDefault();
  }
  <input type="text" onBlur={saveInput}>
  ```
  Occurs when an object loses focus

</section>

---

# Conditional rendering
In React, you can create distinct components that encapsulate behavior you need. Then, you can render only some of them, depending on the state or props of your application.

<section class="grid grid-cols-2 gap-4">

```jsx
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <UserGreeting />;
  }
  return <GuestGreeting />;
}
```
using return with if statement

</section>

<section class="grid grid-cols-2 gap-4">

```jsx
function WarningBanner(props) {
  if (!props.warn) {
    return null;
  }

  return (
    <div className="warning">
      Warning!
    </div>
  );
}
```
Preventing componet from rendering

</section>

---

<section class="grid grid-cols-2 gap-4">

```jsx
const isLoggedIn = this.state.isLoggedIn;
let button;
if (isLoggedIn) {
  button = <LogoutButton onClick={this.handleLogoutClick} />;
} else {
  button = <LoginButton onClick={this.handleLoginClick} />;
}

return (
  <div>
    <Greeting isLoggedIn={isLoggedIn} />
    {button}
  </div>
);
```

Using as a variable

</section>

<section class="grid grid-cols-2 gap-4">

```jsx
const isLoggedIn = this.state.isLoggedIn;

return (
  <div>
    <Greeting isLoggedIn={isLoggedIn} />
    { isLoggedIn 
      ? <LogoutButton onClick={this.handleLogoutClick} />
      : <LoginButton onClick={this.handleLoginClick} />
    }
  </div>
);
```

Using inline If-Else with Conditional Operator

</section>

---

# Lists
When working with the arrays the map() function should be used to create new object array. 

```jsx {3-5|7|all}
function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    <li key={number.toString()}>{number}</li>
  );
  return (
    <ul>{listItems}</ul>
  );
}
```

Inside the return function map() function should be used as well.
```jsx {3-6}
return (
    <ul>
      {numbers.map((number) =>
        <li key={number.toString()}>{number}</li>
      )}
  </ul>
  );
```

---

Keys help React identify which items have changed, are added, or are removed. Use a string that uniquely identifies a list item among its siblings. Don't use indexes for keys if the order of items may change. This can negatively impact performance and may cause issues with component state.

```jsx {2-4,6,10-12,14|2,5-6,10-11,13-14|all}
function ListItem(props) {
  const value = props.value;
  return (
    <li key={value.toString()}>{value}</li> // Wrong! There is no need to specify the key here:
    <li>{value}</li> // Correct! There is no need to specify the key here
  );
}

function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    <ListItem value={number} /> // Wrong! The key should have been specified here:
    <ListItem key={number.toString()} value={number} />// Correct! Key should be specified inside the array.
  );
  return (
    <ul>
      {listItems}
    </ul>
  );
}
```

---

# Forms

- HTML form elements work a bit differently from other DOM elements in React, because form elements naturally keep some internal state. 
- In React, mutable state is typically kept in the state property of components, and only updated with useState(). 
- We can combine the two by making the React state be the “single source of truth”. 
- Then the React component that renders a form also controls what happens in that form on subsequent user input. 
- An input form element whose value is controlled by React in this way is called a “controlled component”.

---

```jsx {2-3|13,16|5-8|11|all}
function LoginForm() {
  const [username, setUsername] = React.useState('');
  const [password, setPassword] = React.useState('');

  const printValues = e => {
    e.preventDefault();
    console.log(username, password);
  };

  return (
    <form onSubmit={printValues}>
      <label> Username:
        <input value={username} onChange={event => setUsername(event.target.value)} type="text" />
      </label>
      <label> Password:
        <input value={password} onChange={event => setPassword(event.target.value)} type="password" />
      </label>
      <button>Submit</button>
    </form>
  );
}
```

---

```jsx {2-5|19,22|11-13|17,7-10|all}
function LoginForm() {
  const [form, setState] = react.useState({
    username: '',
    password: ''
  });

  const printValues = e => {
    e.preventDefault();
    console.log(form.username, form.password);
  };

  const updateField = e => {
    setState({ ...form, [e.target.name]: e.target.value });
  };

  return (
    <form onSubmit={printValues}>
      <label> Username:
        <input value={form.username} name="username" onChange={updateField} /> 
      </label>
      <label> Password:
        <input value={form.password} name="password" type="password" onChange={updateField} />
      </label>
      <button>Submit</button>
    </form>
  );
}
```

---

Create custom hook which will handle value update and automatically binds to onChange event.

```jsx {2|4-6|8-11|all}
const useInput = (initialValue) => {
  const [value, setState] = React.useState(initialValue);

  const handleChange = (event) => {
    setValue(event.target.value);
  };

  return {
    value,
    onChange: handleChange
  };
};
```

---

Reuse created hook to simplify code in form component

```jsx {2-3|13,16|11|5-8|all}
function LoginForm() {
  const username = useInput("");
  const password = useInput("");

  const printValues = e => {
    e.preventDefault();
    console.log(username, password);
  };

  return (
    <form onSubmit={printValues}>
      <label> Username:
        <input {...username} /> 
      </label>
      <label> Password:
        <input type="password" {...password} />
      </label>
      <button>Submit</button>
    </form>
  );
}
```

---

# Lifting State Up
Often, several components need to reflect the same changing data. We recommend lifting the shared state up to their closest common ancestor. 

This common problem is really obvious while working with arrays. While trying to split everything to small components the new issue appears. Multiple components rely on the same data and all components should be updated when the data changes.

```jsx
function TodoCount({ todos }) {
  return <div>Total Todos: {todos.length}</div>;
}

function TodoList({ todos }) {
  return (
    <ul>
      {todos.map((todo) => (
        <li key={todo}>{todo}</li>
      ))}
    </ul>
  );
}
```

---

```jsx
function App() {
  const [todos, setTodos] = React.useState(["item 1", "item 2", "item 3"]);
  return (
    <>
      <TodoCount todos={todos} />
      <TodoList todos={todos} />
      <AddTodo setTodos={setTodos} />
    </>
  );
}

function AddTodo({ setTodos }) {
  function handleSubmit(event) {
    event.preventDefault();
    const todo = event.target.elements.todo.value;
    setTodos(prevTodos => [...prevTodos, todo]);
  }

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" id="todo" />
      <button type="submit">Add Todo</button>
    </form>
  );
}
```

---

# Composition
React has a powerful composition model, and it is recommended using composition instead of inheritance to reuse code between components.

```jsx {4|all}
function FancyBorder(props) {
  return (
    <div className={'FancyBorder FancyBorder-' + props.color}>
      {props.children}
    </div>
  );
}
```

```jsx {4-9|all}
function WelcomeDialog() {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">
        Welcome
      </h1>
      <p className="Dialog-message">
        Thank you for visiting our spacecraft!
      </p>
    </FancyBorder>
  );
}
```

---

While this is less common, sometimes you might need multiple “holes” in a component. In such cases you may come up with your own convention instead of using children

```jsx {5,8|16-18|all}
function SplitPane(props) {
  return (
    <div className="SplitPane">
      <div className="SplitPane-left">
        {props.left}
      </div>
      <div className="SplitPane-right">
        {props.right}
      </div>
    </div>
  );
}

function App() {
  return (
    <SplitPane
      left={ <Contacts />}
      right={ <Chat /> } />
  );
}
```

---

# Specialization

Sometimes we think about components as being “special cases” of other components. For example, we might say that a WelcomeDialog is a special case of Dialog. 


```jsx {16-18|5,8}
function Dialog(props) {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">
        {props.title}
      </h1>
      <p className="Dialog-message">
        {props.message}
      </p>
    </FancyBorder>
  );
}

function WelcomeDialog() {
  return (
    <Dialog
      title="Welcome"
      message="Thank you for visiting our spacecraft!" />
  );
}
```

---

Composition and Specialization works together

```jsx {15-18|4-6|all}
function Dialog(props) {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">{props.title}</h1>
      <p className="Dialog-message">{props.message}</p>
      {props.children}
    </FancyBorder>
  );
}

function SignUpDialog(props) {
  const [login, setLogin] = useState('');
  
  return (
    <Dialog title="Mars Exploration Program" message="How should we refer to you?">
      <input value={this.state.login} onChange={this.handleChange} />
      <button onClick={this.handleSignUp}>Sign Me Up!</button>
    </Dialog>
    );

  handleChange(e) { setLogin(e.preventDefault(); e.target.value); }
  handleSignUp() { alert(`Welcome aboard, ${this.state.login}!`); }
}
```

---

# Modern Development Environment

<img style="width: 800px" src="https://miro.medium.com/max/1400/1*bbxDiplpyPrwg-g7GXC-FA.png">

---

<img style="width: 800px" src="https://c.tenor.com/9nkS4ZhI5kQAAAAC/conspiracy-theory.gif">

---
layout: two-cols
---

# NodeJS

Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine. As an asynchronous event-driven JavaScript runtime, Node.js is designed to build scalable network applications.

[download link](https://nodejs.org/en/)

```js
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

::right::

<img src="https://nodejs.org/static/images/logo.svg" />

---

# Package managers

The package manager will provide a method to install new dependencies (also referred to as "packages"), manage where packages are stored on your file system, and offer capabilities for you to publish your own packages.

- Finding all the correct package JavaScript files.
- Checking them to make sure they don't have any known vulnerabilities.
- Downloading them and putting them in the correct locations in your project.
- Writing the code to include the package(s) in your application (this tends to be done using JavaScript modules, another subject that is worth reading up on and understanding).
- Doing the same thing for all of the packages' sub-dependencies, of which there could be tens, or hundreds. 
- Removing all the files again if you want to remove the packages.

---

# Popularity
---
title: StackOverflow
layout: iframe
url: https://insights.stackoverflow.com/trends?tags=npm%2Cyarnpkg
preload: false
hideInToc: true
---

---
hideInToc: true
---

StateOfJS
<img style="width: 500px;" src="https://stateofx-images.netlify.app/captures/js2021/en-US/monorepo_tools_experience_marimekko.png">

[Source](https://2021.stateofjs.com/en-US/libraries/monorepo-tools)
---

Google
<img style="width: 700px;" src="/images/packages-google.png">

[Source](https://trends.google.com/trends/explore?cat=31&date=today%205-y&q=npm,yarn)
---

# npm / pnpm 

Npm is installed with NodeJS automatically. If you want to use pnpm, it needs to be installed using npm first.

Most popular commands:

```js
npm install
npm install react react.dom        -g  /  --save   / --save-dev
npm install react@18.1.0  
npm uninstall react  
npm update react  
npm list      -g --depth=0
npm outdated    -g --depth=0
npm start
npm build
```

if using pnpm 'p' letter needs to be added to the begining of each command.

---

<img style="width: 900px;" src="/images/node-modules-memes.png">

---

# Bundlers

A bundler is a development tool that combines many JavaScript code files into a single one that is production-ready loadable in the browser. It generates a dependency graph as it traverses your first code files. This implies that beginning with the entry point you specified, the module bundler keeps track of both your source files’ dependencies and third-party dependencies. This dependency graph guarantees that all source and associated code files are kept up to date and error-free. By default bundlers does not require any configuration file at the beggining, but in some specific scenarious it is possible to add the configuration file.

---

# Popularity
---
title: StackOverflow
layout: iframe
url: https://insights.stackoverflow.com/trends?tags=webpack%2Cgulp%2Cbrowserify
preload: false
hideInToc: true
---

---
hideInToc: true
---

StateOfJS
<img style="width: 500px;" src="https://stateofx-images.netlify.app/captures/js2021/en-US/build_tools_experience_marimekko.png">

[Source](https://2021.stateofjs.com/en-US/libraries/build-tools)
---

Google
<img style="width: 700px;" src="/images/bundlers-google.png">

[Source](https://trends.google.com/trends/explore?cat=31&date=today%205-y&q=webpack,gulp,browserify,vite)
---

# Webpack
Most of the popular fraweworks are using webpack as the default bundler.

At its core, webpack is a static module bundler for modern JavaScript applications. When webpack processes your application, it internally builds a dependency graph from one or more entry points and then combines every module your project needs into one or more bundles, which are static assets to serve your content from.

<img style="width: 650px" src="https://www.saaspegasus.com/static/images/web/modern-javascript/js-pipeline-with-django.png">

---

# Babel
Babel is a toolchain that is mainly used to convert ECMAScript 2015+ code into a backwards compatible version of JavaScript in current and older browsers or environments. 
- Transform syntax
- Polyfill features that are missing in your target environment
- Source code transformations (codemods)

```jsx
<button onClick={() => this.setState({ liked: true })}>Like</button>
```

```js
"use strict";

var _this = void 0;

/*#__PURE__*/
React.createElement("button", {
  onClick: function onClick() {
    return _this.setState({
      liked: true
    });
  }
}, "Like");
```

---

<img style="width: 500px;" src="https://i.redd.it/9h8gb3qua0l31.jpg">

---

# Javascript flavors

JavaScript is an interpreted programming language. It requires an engine/runtime to actually do anything. Some JavaScript engines interpret code until the engine recognizes that compilation would help performance. It will compile portions of the code to achieve better performance. It is an implementation detail of the engine/runtime, not the language.

<img style="width: 600px;" src="https://miro.medium.com/max/700/1*XCd11j_E0N5Po1oKQxMDLw.png">

[This time we have a video](https://www.destroyallsoftware.com/talks/wat)

---

# Popularity
---
title: StackOverflow
layout: iframe
url: https://insights.stackoverflow.com/trends?tags=typescript%2Ccoffeescript
preload: false
hideInToc: true
---

---
hideInToc: true
---

StateOfJS
<img style="width: 700px;" src="https://stateofx-images.netlify.app/captures/js2020/en-US/javascript_flavors_experience_marimekko.png">

[Source](https://2020.stateofjs.com/en-US/technologies/javascript-flavors)

---

Google
<img style="width: 700px;" src="/images/flavors-google.png">

[Source](https://trends.google.com/trends/explore?cat=31&date=today%205-y&q=typescript,reason,elm,closurescript)

---
layout: two-cols
---

# Typescript

Typescript is a superset of Javascript.

- Expands the language of Javascript with types, enums, decorators, interfaces and more
- Auto-complete
- Editor checks for errors
- JSX support
- [Typescript Playground](https://www.typescriptlang.org/play)

::right::

<img src="https://mblogthumb-phinf.pstatic.net/MjAxOTA5MThfMjUz/MDAxNTY4Nzc1NjcwODU4.xFOImjrZShTTuPsRzemtz1FI-RCuruHnMEEGZL3BOEUg.ZQ0MifFlaaGRKn6bmbFCsujHt2kC2V1wQv0hmigWuO4g.PNG.bluesky4381/TypeScript_JavaScript.png?type=w800" />

---

# Typescript example

```ts {1|3-8|10-14|16-19|21-24|all}
const myLanguage: 'js' | 'ts' = 'ts';

enum CodingSkill {
  Junior,    // 0
  Mid,       // 1
  Senior,    // 2
  Macaronni, // 3
}

interface Candidate {
  name: string;
  skill: CodingSkill;
  language: 'js' | 'ts';
}

const developer: Candidate {
  name: 'John Doe',
  skill: CodingSkill.Advanced,
  language: 'ts'
}

function evaluateCandidate(someCandidate: Candidate): boolean { ... };
```

---

# ESLint
ESLint is a tool for identifying and reporting on patterns found in ECMAScript/JavaScript code, with the goal of making code more consistent and avoiding bugs.

- Statically analyzes your code to quickly find problems. ESLint is built into most text editors.
- Many problems ESLint finds can be automatically fixed. 
- Preprocess code, use custom parsers, and write your own rules that work alongside ESLint's built-in rules.

<img style="width: 450px;" src="https://resources.jetbrains.com/help/img/idea/2022.1/ws_node_docker_eslint_dark.png" />

---

# Tool-chains
A software toolchain is a set of software development tools used in combination with one another to complete complex software development tasks or to deliver a software product.

<img style="width: 750px" src="https://www.saaspegasus.com/static/images/web/modern-javascript/2008-vs-2021.png">

---

# Popularity
---
title: StackOverflow
layout: iframe
url: https://insights.stackoverflow.com/trends?tags=create-react-app%2Cnext.js%2Cgatsby
preload: false
hideInToc: true
---

---
hideInToc: true
---

StateOfJS
<img style="width: 500px;" src="https://stateofx-images.netlify.app/captures/js2021/en-US/back_end_frameworks_experience_marimekko.png">

[Source](https://2021.stateofjs.com/en-US/libraries/back-end-frameworks)
---

Google
<img style="width: 700px;" src="/images/tool-chains-google.png">

[Source](https://trends.google.com/trends/explore?cat=31&date=today%205-y&q=next%20js,gatsby,create%20react%20app)
---

# Create React APP

Cons:
- Best for learning
- Use if creating single page app
- Client side only
- Hot-reload
- No need to configure anything
- Webpack, babel, typescript, Eslint under the hood
- easy to upgrade  <i>npm install react-scripts@latest</i> 

Pros:
- Is not friendly for SEO
- One big JS bundle
- Possible slow route transitions

---

# Get started 

```js
npx create-react-app my-app --template typescript
cd my-app
npm start
```

[In detail](https://create-react-app.dev/docs/getting-started/)
---

# Next JS

- Do not need to configure, easy to start
- To create a page its enough to add new file to pages folder
- Supports Server Side Rendering
- Supports Client Side Rendering
- Code splitting into multiple bundles
- Routing
- Image optimization
- Supports Incremental Static Regeneration (ISG) and Static Site Gerenation (SSG)

<img src="/images/nextjs-things-of-internet.png" />

---

# Get started

```js
npx create-next-app@latest --typescript
npm run dev
```

[In detail](https://nextjs.org/docs/getting-started)
---

---
layout: center
hideInToc: true
---

# Good luck and have fun!

---
layout: cover
background: /images/cover-end.png
title: Closing slide
large: true
hideInToc: true
---

- Respect
- Reliability
- Innovation
- Competence
- Team spirit

<style>
    .slidev-layout ul {
        @apply text-2xl;
        
        color: var(--secondary-text-color);
        list-style: none;
        padding: 0;
        margin: 0;
    }
</style>