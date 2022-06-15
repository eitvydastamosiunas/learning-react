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

# Brief history of React
 - 2004 - [E4X - ECMAScript For XML](https://svn.wso2.org/repos/wso2/tags/carbon/0.1alpha/mashup/java/xdocs/e4xquickstart.html)
 - 2010 - [XHP](https://github.com/facebookarchive/xhp-php5-extension)
 - 2011 - [FaxJS by Jordan Walke](https://github.com/jordwalke/FaxJs)
 - 2012 - Used in FaceBook and Instagram
 - 2013 - [React Open source release](https://www.youtube.com/watch?v=GW0rj4sNH2w)
 - 2015 - React Stable version and React Native releases
 - 2019 - [In v16.8 the Hooks are introduced](https://reactjs.org/blog/2019/02/06/react-v16.8.0.html)

---
layout: center
---

<img style="width: 400px;" src="/images/jsx-reactions.png" />

---
layout: center
hideInToc: true
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

[State of JS](https://2021.stateofjs.com/en-US/libraries/front-end-frameworks/)
<img style="width: 550px;" src="https://stateofx-images.netlify.app/captures/js2021/en-US/front_end_frameworks_experience_marimekko.png">

---

[Google](https://trends.google.com/trends/explore?cat=1227&date=today%205-y&q=react,jquery,angular,vue)
<img style="width: 700px;" src="/images/react-google.png">

---
layout: two-cols
---

# What is React?
A JavaScript <b>library</b> for building user <b>interfaces</b>. 

- Component-Based
- Declarative
- Immutable

::right::

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/React-icon.svg/2300px-React-icon.svg.png" />

---

# Component-Based
Build <b>encapsulated components</b> that manage their <b>own state</b>, then <b>compose them</b> to make <b>complex UIs</b>.

Since component logic is written in JavaScript instead of templates, you can easily pass rich data through your app and keep state out of the DOM.

<img style="width: 600px;"  src="/images/react-component.png" />
---

# Declarative
Developer should <b>focus</b> on <b>data transformation</b> and leave <b>DOM</b> manipulation for the <b>react</b>.

<img style="width: 550px;" src="/images/virtual-dom.png" />
---

# Immutable 
The existing <b>data</b> should <b>not</b> be <b>mutated</b>, but instead <b>new state</b> should be <b>created</b>.

<img style="width: 600px;" src="https://velopert.com/wp-content/uploads/2017/12/react-love-immutable.png">
---

# JSX
Is <b>syntax extension</b> to JavaScript. 
- Describes what the UI should look like. 
- Comes with the full power of JavaScript.
- Produces React “elements”

<i>Example: JSX syntax</i>
```jsx 
const element = <h1 className="greeting">Hello, world!</h1>;
```
<i>is translated to</i>

```js 
  const element = React.createElement(
    'h1',
    {className: 'greeting'},
    'Hello, world!'
  );
```
---

<section class="grid grid-cols-2 gap-4">

  ```jsx {2|all}
  const name = 'Josh Perez';
  const element = <h1>Hello, {name}</h1>;
  ```
  <i>Embedding Expressions in JSX.</i>

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx {6|8|1-3|all}
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
  <i>JSX is an Expression Too.</i>

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx {1|all}
  const element = <img src={user.avatarUrl}></img>;
  ```
  <i>Specifying Attributes with JSX.</i>

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
  <i>Specifying Children with JSX.</i>

</section>
---

# Elements
Are the <b>smallest building blocks</b> of React apps.

Unlike browser DOM elements, <b>React elements</b> are <b>plain objects</b>, and are <b>cheap to create</b>. <b>React DOM</b> takes care of <b>updating the DOM</b> to <b>match</b> the <b>React elements</b>.

<i>Let’s say there is a div element somewhere in your HTML file</i>
```html
<div id="root"></div>
```
<i>To render a React element, first pass the DOM element to ReactDOM.createRoot(), then pass the React element to root.render()</i>
```jsx {1-3|4|5|all}
const root = ReactDOM.createRoot(
  document.getElementById('root')
);
const element = <h1>Hello, world</h1>;
root.render(element);
```

<b>[Task: Fix application to display user info](https://codepen.io/gaearon/pen/PGEjdG?editors=1010)</b>
---

# Components
Let you <b>split</b> the <b>UI</b> into <b>independent</b>, <b>reusable</b> pieces, and <b>think</b> about <b>each piece</b> in <b>isolation</b>. 

<i>Function component</i>
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
<i>Class component</i>
```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```
Components must be <b>defined</b> by <b>starting</b> with <b>capital letter</b>. This is <b>required</b> for React to <b>distinguish</b> them from <b>standard HTML elements</b>.

---

# Reusing the components
Components can <b>refer</b> to <b>other</b> components in their output. This lets us <b>use</b> the <b>same component</b> abstraction for <b>any level</b> of detail. <b>Components</b> are <b>designed</b> to be <b>isolated</b> so always try to <b>split big parts</b> into <b>smaller components</b>.

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
When <b>React</b> sees an element representing a <b>user-defined component</b>, it <b>passes JSX attributes and children</b> to this component as a <b>single object</b>. <b>Props</b> are treated as <b>readonly</b>. This allows React to <b>determine</b> the <b>difference</b> and let know if the <b>props are different</b>.

<section class="grid grid-cols-2 gap-4">

  ```jsx 
  <MyComponent message="hello world">
  ```
  <i>Passing props as a string</i>

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  let greeting = "Hello world!";
  return <MyComponent message={greeting}>
  ```
  <i>Passing props as an object</i>

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  <MyComponent foo={1 + 2 + 3 + 4}>
  ```
  <i>Passing props as an evaluation</i>

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
  <i>Using props as a for condition inside component.</i>

</section>

---

<section class="grid grid-cols-2 gap-4">

  ```jsx
  <MyTextBox autocomplete />
  ```
  <i>Props with no value defaults to true</i>

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
  <i>Passing props using spread operator</i>

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  function deleteUser(id) {
    const index = users.findIndex(x => x.id === id);
    setUsers(users.splice(index))
  }
  return <User deleteCalback={deleteUser} userId={user.id}>
  ```
  <i>Passing props a callback function</i>
</section>

---

# State 
Is used to create <b>encapsulated components</b> which <b>have</b> its <b>own data</b> and <b>manage</b> how its <b>changing</b>. When then <b>model</b> has <b>changed</b>, <b>React updates necessary DOM elements</b>. 

In React <b>v16.8</b> the <b>hooks</b> were <b>introduced</b>. They allow to <b>use state</b> and <b>other</b> React <b>features without</b> writing a <b>class</b>. As the developers are <b>encouraged</b> to write <b>function</b> components the <b>class</b> components are still <b>supported</b>.

There is a <b>big difference</b> how the <b>lifecycle</b> and <b>state management</b> works in <b>class</b> and <b>function</b> components. We will <b>primarily focus</b> on the <b>function</b> components but it is important to understand how class component works aswell.

---

# State management and Lifecycle in Class components
```jsx {2-5|6-8|12-16|17-22|9-11|all}
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
- The <b>default state</b> must be defined in class <b>constructor</b>.
- The <b>componentDidMount</b> method is called <b>after</b> the component output is <b>rendered into DOM</b>
- The <b>componentWillUnmount</b> is called when component is <b>removed from the DOM</b>.
- To <b>update</b> the state <b>this.setState</b> method should be used.
- All <b>event functions</b> which are used should be <b>binded</b>.
- <b>State</b> and <b>functions</b> are accessed by using <b>this</b> keyword.

```jsx {2|8|3|2,3,8,11|all}
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
The <b>hooks</b> were introduced in <b>React v16.8</b> and allowed to use <b>state</b> and other React <b>features</b> <b>without</b> writing a class.
- Hooks do <b>provide a more direct API</b> to the <b>React concepts</b>.
- The <b>same hook</b> can be <b>used more than once</b>.
- Hooks are <b>executed in order</b> from top to the bottom.
- Hooks <b>reduce</b> the <b>boilerplate</b> of <b>class</b> components.
- Developers can <b>write own hooks</b> and <b>reuse</b> accross the many <b>components</b> (useYourHookName)
- Function components are <b>easier to test</b>.

```jsx {2|7|3-6|all}
function Address() {
  const [address, setAddress] = React.useState('');
  function onTextChanged(e) {
    e.preventDefault();
    setAddress(e.target.value);
  }
  return <input type='text' onChange={onTextChanged} value={address} />
}
```
---

# useState
This hook <b>allows</b> to add the local <b>state</b> inside <b>functional</b> component. React will <b>preserve</b> its <b>state</b> between <b>re-renders</b>. 

It is the <b>function</b> which is taking the <b>default value</b> as a parameter and <b>returning</b> pair of:
- the <b>current state value</b>
- a <b>function</b> which lets to <b>update</b> the <b>state</b>

<i>It can use objects, arrays or other primitive types.</i>

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
<b>Data fetching</b>, <b>subscriptions</b>, or <b>manually changing</b> the DOM from React components are called <b>“side effects”</b> because they can <b>affect other components</b> and <b>can’t</b> be done during <b>rendering</b>.

The <b>useEffect</b> serves the same purpose as <i>componentDidMount</i>, <i>componentDidUpdate</i>, and <i>componentWillUnmount</i> in React classes, but unified into a <b>single</b> API.

<section class="grid grid-cols-2 gap-4">

  ```jsx
  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });
  ```
  <i>Runs on <b>every</b> render</i>

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx {7-9|5|11|all}
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
  - <i><b>return function</b> acts <b>cleanup</b>, useEffect will be <b>invoked</b> again only <b>if friend id changes</b>.</i>
  - <i>If leaving <b>blank array</b>, it will be triggered <b>only once</b>.</i>

</section>

---

# Events
Handling <b>events</b> with React elements is very <b>similar</b> to handling events on <b>DOM</b> elements but there are some <b>syntax differences</b>.

<section class="grid grid-cols-2 gap-4">

  ```html
  <button onclick="activateLasers()">
    Activate Lasers
  </button>
  ```
  <i>HTML</i>

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  <button onClick={activateLasers}>
    Activate Lasers
  </button>
  ```
  - <i>React events are <b>named</b> using <b>camelCase</b>, rather than lowercase.</i>
  - <i>With JSX you pass a <b>function</b> as the <b>event handler</b>, rather than a <b>string</b>.</i>

</section>
---

Another <b>difference</b> is that you <b>cannot</b> <i>return false;</i> to <b>prevent default behavior</b> in React. You must call preventDefault explicitly. 

<i>For example, with plain HTML, to prevent the default form behavior of submitting, you can write:</i>

```html
<form onsubmit="console.log('You clicked submit.'); return false">
  <button type="submit">Submit</button>
</form>
```

<i>In react preventDefault() function should be called from event object</i>

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

---

Inside a <b>loop</b>, it is common to <b>pass</b> an <b>extra parameter</b> to an <b>event handler</b>. 

<i>For example, if id is the row ID, either of the following would work.</i>

```jsx{9-11|2-5|all}
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

<i><b>Note!</b> It is <b>Ok</b> to use <b>arrow function</b> within the <b>loop</b>, but is better to <b>avoid</b> its usage in <b>single</b> elements. In most cases, this is fine. However, if this <b>callback</b> is <b>passed</b> as a <b>prop</b> to <b>lower components</b>, those components might <b>do</b> an <b>extra re-rendering</b>.</i>

---

Mostly used events

<section class="grid grid-cols-2 gap-4">

  ```jsx
  function onClick(e) {
    e.preventDefault();
  }

  <input type="submit" onClick={onClick}>
  ```
  <i>Occurs when the user clicks on an element</i>

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  function onTextChanged(e) {
    e.preventDefault();
  }
  <input type="text" onChange={onTextChanged}>
  ```
  <i>Occurs when the value of an element has been changed</i>

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
  function onFocus(e) {
    e.preventDefault();
  }
  <input type="text" onFocus={onFocus}>
  ```
  <i>Occurs when an element gets focus</i>

</section>

<section class="grid grid-cols-2 gap-4">

  ```jsx
   function saveInput(e) {
    e.preventDefault();
  }
  <input type="text" onBlur={saveInput}>
  ```
  <i>Occurs when an object loses focus</i>

</section>

---

# Conditional rendering
In React, you can create <b>distinct</b> components that encapsulate <b>behavior</b> you need. Then, you can <b>render only some</b> of them, <b>depending</b> on the <b>state</b> or <b>props</b> of your application.

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
<i>using <b>return</b> with <b>if</b> statement</i>

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
<i><b>Preventing</b> component from rendering</i>

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

<i>Using as a <b>variable</b></i>

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

<i>Using <b>inline If-Else</b> with Conditional Operator</i>

</section>

---

# Lists

When working with the <b>arrays</b> the <i>map()</i> <b>function</b> should be used to create <b>new elements</b>. 

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

The <i>map()</i> function can be used in the <b>return</b> <b>function</b> aswell.
```jsx
return (
    <ul>
      {numbers.map((number) =>
        <li key={number.toString()}>{number}</li>
      )}
  </ul>
  );
```

---

<b>Keys</b> help React <b>identify</b> which items have <b>changed</b>, are <b>added</b>, or are <b>removed</b>. Use a <b>string</b> that <b>uniquely identifies</b> a list item among its <b>siblings</b>. <b>Don't</b> use <b>indexes</b> for <b>keys</b> if the order of items <b>may change</b>. This can <b>negatively impact performance</b> and <b>may cause issues with component state</b>.

```jsx {1-4,6-7,9-12,14-20|1-3,5-7,9-11,13-20|all}
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
layout: two-cols
---

# Thinking in React

React can <b>change</b> how you <b>think</b> about the <b>designs</b> you look at and the apps you <b>build</b>. Where once you might have seen a <b>forest</b>, after working with React, you will appreciate the <b>individual trees</b>. React makes it easier to <b>think</b> in <b>design systems</b> and <b>UI states</b>.

<i>Imagine your API returns you this following data structure</i>

```json
[
  { category: "Fruits", price: "$1", stocked: true, name: "Apple" },
  { category: "Fruits", price: "$1", stocked: true, name: "Dragonfruit" },
  { category: "Fruits", price: "$2", stocked: false, name: "Passionfruit" },
  { category: "Vegetables", price: "$2", stocked: true, name: "Spinach" },
  { category: "Vegetables", price: "$4", stocked: false, name: "Pumpkin" },
  { category: "Vegetables", price: "$1", stocked: true, name: "Peas" }
]
```

::right::

<i>And following mockup</i>

<img style="width: 300px;" src="https://beta.reactjs.org/images/docs/s_thinking-in-react_ui.png" />

---
layout: two-cols
---
<b>1. Break the UI into a component hierarchy</b>

1. <i>FilterableProductTable</i> (grey) contains the entire app.
2. <i>SearchBar</i> (blue) receives the user input.
3. <i>ProductTable</i> (lavander) displays and filters the list according to the user input.
4. <i>ProductCategoryRow</i> (green) displays a heading for each category.
5. <i>ProductRow</i> (yellow) displays a row for each product.


::right::
<img style="width: 500px;" src="https://beta.reactjs.org/images/docs/s_thinking-in-react_ui_outline.png">

<b>Final hierarchy</b>
* FilterableProductTable
    * SearchBar
    * ProductTable
      * ProductCategoryRow
      * ProductRow

---

<b>2. Build a static  version</b>

When component hierarchy is <b>decided</b> start <b>implementing</b> your app. The <b>easiest</b> way to do this is to make an apllication which <b>renders</b> the whole <b>structure without any interactivity</b>. Building a <b>static</b> version requires a lot of <b>typing and no thinking</b>, but <b>adding interactivity requires</b> a <b>lot of thinking</b> and not a lot of typing.

To <b>build</b> a <b>static</b> version of your app that <b>renders</b> your <b>data model</b>, you’ll want to <b>build</b> components that <b>reuse other</b> components and <b>pass data using props</b>. <b>Don’t use state</b> at all to build this <b>static</b> version.

You can either build <b>"top down"</b> by starting with building the components higher up in the hierarchy (<i>like FilterableProductTable</i>) or <b>"bottom up"</b> by working from components lower down (<i>like ProductRow</i>). In <b>simpler</b> examples, it’s usually <b>easier</b> to go <b>top-down</b>, and on <b>larger projects</b>, it’s <b>easier</b> to go <b>bottom-up</b>.

---

<b>3. Find minimal but complete representation of UI state</b>

To  make the <b>UI interactive</b>, you need to let <b>users change</b> your underlying <b>data model</b>. You will <b>use state</b> for this.

<b>Think</b> of state as the <b>minimal set</b> of <b>changing data</b> that your <b>app needs</b> to remember. The most important principle for structuring state is to keep it [DRY (Don’t Repeat Yourself)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself). <b>Figure out</b> the <b>absolute minimal</b> representation of the <b>state</b> your <b>application needs</b> and <b>compute everything else</b> on-demand.


<i>Let's distiguish what is the state and what is the props</i>

1. The original <b>list of products</b> is passed in as <b>props</b>, so it’s <b>not state</b>.
2. The <b>search text</b> seems to be <b>state</b> since it <b>changes over time</b> and <b>can’t be computed</b> from anything.
3. The <b>value</b> of the <b>checkbox</b> seems to be <b>state</b> since it <b>changes over time</b> and <b>can’t be computed</b> from anything.
4. The <b>filtered list</b> of products <b>isn’t state</b> because it can be <b>computed</b> by taking the <b>original list</b> of products and <b>filtering</b> it according to the <b>search text</b> and value of the <b>checkbox</b>.
5. This means <b>only</b> the <b>search text</b> and the <b>value of the checkbox</b> are <b>state</b>!

---

<b>4. Identify where your state should live</b>

After <b>identifying</b> your app’s <b>minimal state</b> data, you need to <b>identify</b> which component is <b>responsible</b> for <b>changing</b> this state, or <b>owns</b> the <b>state</b>.

React is all about <b>one-way data flow down the component hierarchy</b>. It may <b>not</b> be immediately <b>clear</b> which <b>component</b> should <b>own what state</b>. This is often the <b>most challenging part to understand</b>, so follow these steps to figure it out:

1. <b>Identify every component</b> that <b>renders</b> something based on that <b>state</b>.
2. <b>Find</b> a <b>common owner</b> component (<i>a <b>single</b> component <b>above</b> all the components that <b>need</b> the <b>state</b> in the <b>hierarchy</b></i>).
3. <b>Decide</b> where the <b>state should live</b>:
    1. Often, you can <b>put</b> the state <b>directly</b> into their <b>common parent</b>.
    2. You can also <b>put</b> the state <b>into</b> some component <b>above</b> their <b>common parent</b>.
    3. If you <b>can’t find</b> a component where it <b>makes sense</b> to <b>own the state</b>, <b>create a new component</b> solely for <b>holding the state</b> and <b>add it</b> somewhere in the <b>hierarchy above</b> the <b>common parent component</b>.

---

<b>5. Add inverse data flow</b>

Currently app renders <b>correctly</b> with <b>props</b> and <b>state</b> flowing <b>down the hierarchy</b>. But to <b>change</b> the <b>state</b> according to <b>user input</b>, you will need to <b>support data flowing the other way</b>. This means the <b>components deep in the hierarchy need to update the state</b>. React makes this data flow explicit, but it requires a little more typing than two-way data binding. You need to <b>send</b> the state setter <b>functions</b> created in useState() as a <b>callbacks</b> to the <b>child components</b> via <b>props</b>.

```jsx {2,3|7-11|12-15|all}
function FilterableProductTable({ products }) {
  const [filterText, setFilterText] = useState('');
  const [inStockOnly, setInStockOnly] = useState(false);
  return (
    <div>
      <SearchBar 
        filterText={filterText} 
        inStockOnly={inStockOnly} 
        onFilterTextChange={setFilterText} 
        onInStockOnlyChange={setInStockOnly} />
      <ProductTable 
        products={products} 
        filterText={filterText}
        inStockOnly={inStockOnly} />
    </div>
  );
}
```

---

# Practical task "Static site"

Create <b>static page</b> and <b>implement todo</b> functionality using techniques you learned.
1. Create new <b>HTML page</b> and add <b>standard HTML elements</b>
2. Register following <b>script links</b>:
  - script src="https://unpkg.com/react@17/umd/react.development.js"
  - script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js
  - script src="https://unpkg.com/@babel/standalone/babel.min.js
  - script type="text/jsx"
3. <b>Render react app</b> displaying <b>"Hello World!"</b>
4. <b>Mock some todos</b> in <b>array</b>
5. <b>Create component</b> which <b>shows todo count</b>
6. <b>Create component</b> which <b>displays todos</b>
7. <b>Create component</b> which allow to <b>add new todos</b>

---

# Modern Development Environment

<img style="width: 800px" src="https://miro.medium.com/max/1400/1*bbxDiplpyPrwg-g7GXC-FA.png">

---

<img style="width: 800px" src="https://c.tenor.com/9nkS4ZhI5kQAAAAC/conspiracy-theory.gif">

---
layout: two-cols
---

# NodeJS

[Node.js®](https://nodejs.org/en/) is a <b>JavaScript runtime</b> built on <b>Chrome's V8 JavaScript engine</b>. As an <b>asynchronous event-driven JavaScript runtime</b>, Node.js is <b>designed</b> to <b>build</b> scalable <b>network applications</b>.

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

The package manager will <b>provide</b> a method to <b>install</b> new <b>dependencies</b> (also referred to as "packages"), <b>manage</b> where packages are <b>stored</b> on your file system, and offer capabilities for you to <b>publish</b> your own packages.

- <b>Finding</b> all the correct package JavaScript files.
- <b>Checking</b> them to make sure they don't have any known <b>vulnerabilities</b>.
- <b>Downloading</b> them and putting them in the correct locations in your project.
- <b>Writing</b> the code to include the package(s) in your application (<i>import</i> / <i>export</i>).
- Doing the same thing for <b>all of the packages' sub-dependencies</b>, of which there could be tens, or hundreds. 
- <b>Removing</b> all the files again if you want to remove the packages.

---
layout: center
hideInToc: true
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

[State of JS](https://2021.stateofjs.com/en-US/libraries/monorepo-tools)

<img style="width: 500px;" src="https://stateofx-images.netlify.app/captures/js2021/en-US/monorepo_tools_experience_marimekko.png">

---

[Google](https://trends.google.com/trends/explore?cat=31&date=today%205-y&q=npm,yarn)

<img style="width: 700px;" src="/images/packages-google.png">

---

# npm / pnpm 

Npm is <b>installed</b> with NodeJS <b>automatically</b>. If you want to use <b>pnpm</b>, it needs to be <b>installed</b> using <b>npm</b> first.

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

if using <b>pnpm</b> <i>'p'</i> letter needs to be added to the <b>begining of each command</b>.

---

<img style="width: 900px;" src="/images/node-modules-memes.png">

---

# Bundlers

A bundler is a development <b>tool></b> that <b>combines many</b> JavaScript code <b>files</b> into a <b>single one</b> file that is <b>production-ready</b> loadable in the <b>browser</b>. It generates a <b>dependency graph</b> as it traverses your <b>first code files</b>. This implies that beginning with the <b>entry point</b> you specified, the module bundler keeps track of both your <b>source files</b>’ dependencies and <b>third-party dependencies</b>. This dependency graph <b>guarantees</b> that <b>all source</b> and <b>associated code files</b> are kept <b>up to date</b> and <b>error-free</b>. By <b>default</b> bundlers <b>does not require</b> any <b>configuration file</b> at the beggining, but in some specific scenarios it is possible to add the <b>configuration</b> file.

---
layout: center
hideInToc: true
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

[State of JS](https://2021.stateofjs.com/en-US/libraries/build-tools)
<img style="width: 500px;" src="https://stateofx-images.netlify.app/captures/js2021/en-US/build_tools_experience_marimekko.png">

---

[Google](https://trends.google.com/trends/explore?cat=31&date=today%205-y&q=webpack,gulp,browserify,vite)
<img style="width: 700px;" src="/images/bundlers-google.png">

---

# Webpack
Most of the popular fraweworks are using <b>webpack</b> as the <b>default bundler</b>.

At its core, webpack is a <b>static module bundler</b> for modern JavaScript applications. When webpack processes your application, it internally builds a dependency graph from one or more entry points and then combines every module your project needs into one or more bundles, which are static assets to serve your content from.

<img style="width: 650px" src="https://www.saaspegasus.com/static/images/web/modern-javascript/js-pipeline-with-django.png">

---

# Babel
Babel is a <b>toolchain</b> that is mainly used to <b>convert ECMAScript 2015+ (ES6)</b> code into a <b>backwards compatible version of JavaScript</b> in current and older browsers or environments. 
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

JavaScript is an <b>interpreted programming language</b>. It requires an <b>engine/runtime</b> to actually do anything. Some JavaScript engines <b>interpret code</b> until the engine <b>recognizes</b> that compilation would help <b>performance</b>. It will compile portions of the code to achieve <b>better performance</b>. It is an <b>implementation</b> detail of the <b>engine/runtime</b>, <b>not the language</b>. 

<img style="width: 600px;" src="https://miro.medium.com/max/700/1*XCd11j_E0N5Po1oKQxMDLw.png">

[This time we have a video](https://www.destroyallsoftware.com/talks/wat)

---
layout: center
hideInToc: true
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

[State of JS](https://2020.stateofjs.com/en-US/technologies/javascript-flavors)

<img style="width: 700px;" src="https://stateofx-images.netlify.app/captures/js2020/en-US/javascript_flavors_experience_marimekko.png">

---

[Google](https://trends.google.com/trends/explore?cat=31&date=today%205-y&q=typescript,reason,elm,closurescript)

<img style="width: 700px;" src="/images/flavors-google.png">

---
layout: two-cols
---

# Typescript

Typescript is a <b>superset</b> of Javascript. It is a <b>strongly typed</b> programming <b>language</b> that builds on JavaScript.

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
ESLint is a <b>tool</b> for <b>identifying</b> and <b>reporting</b> on <b>patterns</b> found in <b>ECMAScript/JavaScript code</b>, with the goal of <b>making</b> code <b>more consistent</b> and <b>avoiding bugs</b>.

- Statically analyzes your code to quickly find problems. ESLint is built into most text editors.
- Many problems ESLint finds can be automatically fixed. 
- Preprocess code, use custom parsers, and write your own rules that work alongside ESLint's built-in rules.

<img style="width: 450px;" src="https://resources.jetbrains.com/help/img/idea/2022.1/ws_node_docker_eslint_dark.png" />

---

# Tool-chains
A software <b>toolchain</b> is a set of software development <b>tools</b> used in <b>combination</b> with one <b>another</b> to <b>complete complex</b> software development <b>tasks</b> or to <b>deliver</b> a <b>software product</b>.

<img style="width: 750px" src="https://www.saaspegasus.com/static/images/web/modern-javascript/2008-vs-2021.png">

---
layout: center
hideInToc: true
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

[State of JS](https://2021.stateofjs.com/en-US/libraries/back-end-frameworks)

<img style="width: 500px;" src="https://stateofx-images.netlify.app/captures/js2021/en-US/back_end_frameworks_experience_marimekko.png">

---

[Google](https://trends.google.com/trends/explore?cat=31&date=today%205-y&q=next%20js,gatsby,create%20react%20app)

<img style="width: 700px;" src="/images/tool-chains-google.png">

---

# Create React APP

<b>Cons</b>:
- Best for learning
- Use if creating single page app
- Client side only
- Hot-reload
- No need to configure anything
- Webpack, babel, typescript, Eslint under the hood
- easy to upgrade  <i>npm install react-scripts@latest</i> 

<b>Pros</b>:
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

[More in detail](https://create-react-app.dev/docs/getting-started/)
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

[More in detail](https://nextjs.org/docs/getting-started)

---

Practical task: create <b>new</b> next.js application using <b>typescript</b>.

- Run command "npx create-next-app nextjs-playground --use-npm --typescript --example "https://github.com/vercel/next-learn/tree/master/basics/learn-starter"
- <b>Transfer</b> Todo application from static page to the new application
- <b>Improve</b> your application with possibility to <b>delete existing to do's</b>. 
- <b>Improve</b> your application to with possibility to <b>mark todo as completed</b>.

---

# Forms

- HTML form elements work a bit <b>differently</b> from <b>other</b> DOM elements in React, because <b>form</b> elements naturally <b>keep</b> some <b>internal state</b>. 
- In React, <b>mutable state</b> is typically kept in the <b>state property of components</b>, and <b>only updated with <i>useState()</i></b>. 
- We can combine the two by making the React state be the <b>"single source of truth"</b>. 
- Then the React component that <b>renders</b> a <b>form</b> also <b>controls</b> what <b>happens</b> in that form on subsequent <b>user input</b>. 
- An <b>input form element</b> whose value is <b>controlled</b> by React in this way is called a <b>"controlled component"</b>.

---

```jsx {2-3|13,16|11|5-8|all}
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

Create <b>custom hook</b> which will handle value <b>update</b> and <b>automatically binds</b> to <b>onChange event</b>.

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

<b>Reuse</b> created <b>custom hook</b> to <b>simplify</b> code in form component

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
Often, <b>several</b> components need to <b>reflect</b> the same changing data. It is <b>recommended</b> lifting the <b>shared state</b> up to their <b>closest common ancestor</b>. 

This common <b>problem</b> is really obvious while <b>working</b> with <b>arrays</b>. While trying to <b>split</b> everything to <b>small components</b> the new issue appears. <b>Multiple</b> components <b>rely</b> on the <b>same data</b> and all components should be <b>updated</b> when the data <b>changes</b>.

```jsx {1-3|5-13|all}
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

```jsx {2|5-7|12-25|all}
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
React has a <b>powerful composition</b> model, and it is <b>recommended</b> using composition <b>instead of inheritance</b> to <b>reuse code</b> between components.

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

While this is less <b>common</b>, sometimes you might need <b>multiple</b> “holes” in a component. In such cases you may come up with <b>your own convention</b> instead of using children.

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

<b>Composition</b> and <b>Specialization</b> works together

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

# Context
The React context <b>provides data</b> to components no matter <b>how deep</b> they are in the <b>components tree</b>. The context is <b>used</b> to <b>manage global data</b>, e.g. global state, theme, services, user settings, and more.

<img style="width: 400px;" src="https://dmitripavlutin.com/90649ae4bdf379c482ad24e0dd220bc4/react-context-3.svg" />

---

<section class="grid grid-cols-2 gap-4">

```jsx {2|all}
import { createContext } from 'react';
const Context = createContext('Default Value');
```
<i>Creating the context</i>

</section>

<section class="grid grid-cols-2 gap-4">

```jsx {4-6|all}
function Main() {
  const value = 'My Context Value';
  return (
    <Context.Provider value={value}>
      <MyComponent />
    </Context.Provider>
  );
}
```
<i>Providing the context</i>

</section>

<section class="grid grid-cols-2 gap-4">

```jsx {1,3-4,9-11|all}
import { useContext } from 'react';
function MyComponent() {
  const value = useContext(Context);
  return <span>{value}</span>;
}

function MyComponent() {
  return (
    <Context.Consumer>
      {value => <span>{value}</span>}
    </Context.Consumer>
  );
}
```
<i>Consuming the context</i>

</section>

---

<b>Use cases</b>

The <b>main idea</b> of using the context is to <b>allow</b> your <b>components</b> to <b>access</b> some <b>global data</b> and <b>re-render</b> when that <b>global data</b> is <b>changed</b>. Context <b>solves</b> the <b>props drilling problem</b>: when you have to pass down props from parents to children.

You can hold inside the context:
- global state
- theme
- application configuration
- authenticated user name
- user settings
- preferred language
- a collection of services

---

<b>Before you start using!</b>

First, <b>integrating</b> the context <b>adds complexity</b>. <b>Creating</b> the context, <b>wrapping</b> everything <b>in</b> the <b>provider</b>, <b>using</b> the <i>useContext()</i> in every <b>consumer</b> — this <b>increases complexity</b>.

Secondly, <b>adding</b> context <b>makes</b> it more <b>difficult</b> to <b>unit test</b> the components. <b>During</b> unit testing, you would have to <b>wrap</b> the <b>consumer</b> components into a <b>context provider</b>. <b>Including</b> the components that are <b>indirectly affected</b> by the context — the <b>ancestors</b> of context consumers!

If you <b>only</b> want to <b>avoid passing</b> some <b>props</b> through <b>many levels</b>, component <b>composition</b> is often a <b>simpler solution</b> than context.

---

# useReducer

Is usually <b>preferable</b> to <i>useState</i> when you have <b>complex</b> state <b>logic</b> that <b>involves</b> multiple <b>sub-values</b> or when the <b>next state depends on the previous one</b>. useReducer also lets you <b>optimize performance</b> for components that <b>trigger deep updates</b> because you can pass <b>dispatch</b> down <b>instead of callbacks</b>.

<img style="width: 500px;" src="https://dmitripavlutin.com/5c33affee33e7c40e73028fb48a8367b/diagram.svg">

---

```jsx {1|3-12|15|18|19-20|all}
const initialState = {count: 0};

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
    </>
  );
}
```

---

# useMemo

If React must perform <b>expensive calculations</b> during <b>each render</b> (e.g. filter) the <b>performance</b> could be <b>improved</b> using <i>useMemo()</i> hook. 

```jsx {2-4|8|15|all}
import { useState, useMemo } from 'react';
function factorialOf(n) {
  return n <= 0 ? 1 : n * factorialOf(n - 1);
}
export function CalculateFactorial() {
  const [number, setNumber] = useState(1);
  const [inc, setInc] = useState(0);
  const factorial = useMemo(() => factorialOf(number), [number]);
  const onChange = event => {
    setNumber(Number(event.target.value));
  };
  const onClick = () => setInc(i => i + 1);
  return (
    <div>
      Factorial of <input type="number" value={number} onChange={onChange} /> is {factorial}
      <button onClick={onClick}>Re-render</button>
    </div>
  );
}
```

---

# useCallback
Returns a <b>memoized</b> version of the <b>callback</b> that <b>only changes</b> if one of the <b>dependencies</b> has <b>changed</b>. This is useful when <b>passing callbacks</b> to <b>optimized child</b> components that rely on <b>reference equality</b> to prevent unnecessary renders.

---

<b>Problem:</b> the Todo component re-renders when todos does not change, because addTodo function gets recreated...

``` jsx {17|9|all}
import { useState } from "react";
import ReactDOM from "react-dom/client";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);

  const increment = () => { setCount((c) => c + 1); };
  const addTodo = () => { setTodos((t) => [...t, "New Todo"]); };

  return (
    <>
      <Todos todos={todos} addTodo={addTodo} />
      <div> 
        Count: {count} 
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

```

---

<b>Solution</b>

```jsx {10-12|all}
import { useState, useCallback } from "react";
import ReactDOM from "react-dom/client";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);

  const increment = () => { setCount((c) => c + 1); };
  const addTodo = useCallback(() => {
    setTodos((t) => [...t, "New Todo"]);
  }, [todos]);

  return (
    <>
      <Todos todos={todos} addTodo={addTodo} />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};
```

---

While <b>useMemo()</b> or <b>useCallback()</b> can <b>improve the performance</b> of the component, you have to <b>make sure</b> to <b>profile</b> the component <b>with and without the hook</b>. Only after that make the <b>conclusion</b> whether <b>memoization worth</b> it.

When <b>memoization</b> is used <b>inappropriately</b>, it could <b>harm</b> the <b>performance</b>.

---

# useRef 
Works <b>similar</b> like <i>useState()</i>, but <b>does not force</b> component to <b>re-render</b>. It could be <b>used</b> for <b>storing values</b> <b>without</b> causing the <b>re-render</b>, or <b>perform</b> some <b>interactions</b> with <b>other elements</b>.

```jsx {3|10|11|4-7|all}
import React, { useRef } from 'react'
function TextInputWithFocusButton() {
  const inputEl = useRef(null);
  const onButtonClick = () => {
    // `current` points to the mounted text input element
    inputEl.current.focus();
  };
  return (
    <>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focus the input</button>
    </>
  );
}
```

---

It could be <b>used</b> to store the <b>previous state</b> aswell.

```jsx {4-5|13|7-9|14|all}
import React, { useRef, useState, useEffect } from 'react'

function App() {
  const [name, setName] = useState('');
  const prevName = useRef('');

  useEffect(() => {
    prevName.current = name;
  }, [name])

  return (
    <>
      <input type="text" value={name} onChange={e => setName(e.target.value)} />
      <div>My name is {name} and it used to be {prevName}</div>
      <button onClick={onButtonClick}>Focus the input</button>
    </>
  );
}
```

---

# Accessibility
Web accessibility (also referred to as a11y) is the <b>design</b> and <b>creation</b> of <b>websites</b> that can be used by <b>everyone</b>. Accessibility support is <b>necessary</b> to allow <b>assistive technology</b> to <b>interpret</b> web pages.

Note that <b>all</b> aria-* HTML <b>attributes</b> are fully <b>supported</b> in JSX. Whereas most DOM properties and attributes in React are camelCased, these attributes should be <b>hyphen-cased</b> (also known as kebab-case, lisp-case, etc) as they are in plain HTML:

```jsx {3-4|all}
<input
  type="text"
  aria-label={labelText}
  aria-required="true"
  onChange={onchangeHandler}
  value={inputValue}
  name="name"
/>
```

---

# Fragments
A common pattern in React is for a component to return <b>multiple</b> elements. Fragments let you <b>group</b> a <b>list</b> of <b>children without</b> adding <b>extra nodes</b> to the DOM. Fragments can have <b>key</b> property which is <b>required</b> to be set in <b>collections</b>. Fragments allow <b>not</b> to <b>break</b> HTML <b>Semantics</b> across component tree.

```jsx {3,7|all}
render() {
  return (
    <React.Fragment> | <> - short syntax
      <ChildA />
      <ChildB />
      <ChildC />
    </React.Fragment> | </> - short syntax
  );
}
```

---

<b>Semantics problem</b>

```jsx {16,19|all}
function Table (props) {
  render() {
    return (
      <table>
        <tr>
          <Columns />
        </tr>
      </table>
    );
  }
}

function Columns(props) {
  render() {
    return (
      <div>
        <td>Hello</td>
        <td>World</td>
      </div>
    );
  }
}

```

--- 

# Code splitting
Code-Splitting is a <b>feature</b> supported by bundlers like <i>Webpack, Rollup and Browserify</i> (via factor-bundle) which can <b>create multiple bundles</b> that can be <b>dynamically loaded</b> at runtime.

The best way to introduce code-splitting into your app is through the <b>dynamic</b> <i>import()</i> syntax.

<section class="grid grid-cols-2 gap-4">

```jsx {4-6|all}
import { add } from './math';
console.log(add(16, 26));
```
<i>standard import</i>

</section>

<section class="grid grid-cols-2 gap-4">

```jsx {4-6|all}
import("./math").then(math => {
  console.log(math.add(16, 26));
});
```
<i>dynamic import</i>

</section>

When <b>bundler</b> comes across this syntax, it <b>automatically starts</b> code-splitting your app. If you’re using <b>Create React App</b>, this is already <b>configured</b> for you and you can start using it immediately. It’s also supported out of the box in <b>Next.js</b>.

---

The <i>React.lazy</i> function lets you <b>render</b> a <b>dynamic import</b> as a regular component. <b>It supports only default imports</b>.

The lazy component <b>should</b> then be <b>rendered</b> inside a <i>Suspense</i> component, which allows us to show some <b>fallback</b> content (<i>such as a loading indicator</i>) while we’re waiting for the lazy component to load.

```jsx {3-4|9,14|11-12|all}
import React, { Suspense } from 'react';

const OtherComponent = React.lazy(() => import('./OtherComponent'));
const AnotherComponent = React.lazy(() => import('./AnotherComponent'));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <section>
          <OtherComponent />
          <AnotherComponent />
        </section>
      </Suspense>
    </div>
  );
}
```

---

# Portals
Portals <b>provide</b> a first-class <b>way</b> to <b>render children</b> into a DOM node that <b>exists outside</b> the DOM <b>hierarchy of the parent</b> component.

<section class="grid grid-cols-2 gap-4">

```jsx {4,6|all}
render() {
  // React mounts a new div and renders the children into it
  return (
    <div>
      {this.props.children}
    </div>
  );
}
```
<i>Standard composition approach</i>

</section>

<section class="grid grid-cols-2 gap-4">

```jsx {6|all}
render() {
  // React does *not* create a new div. It renders the children into `domNode`.
  // `domNode` is any valid DOM node, regardless of its location in the DOM.
  return ReactDOM.createPortal(
    this.props.children,
    domNode
  );
}
```
<i>Inserting a child into a different location in the DOM using portal</i>

</section>

[Example](https://codepen.io/gaearon/pen/jGBWpE)

---

# Profiler

The Profiler <b>measures</b> how often a React application <b>renders</b> and what the <b>“cost”</b> of rendering <b>is</b>. Its <b>purpose</b> is to <b>help identify parts</b> of an application that are <b>slow</b> and may <b>benefit</b> from <b>optimizations</b> such as <b>memoization</b>.

```jsx {3,5,8|all}
render(
  <App>
    <Profiler id="Panel" onRender={callback}>
      <Panel {...props}>
        <Profiler id="Content" onRender={callback}>
          <Content {...props} />
        </Profiler>
        <Profiler id="PreviewPane" onRender={callback}>
          <PreviewPane {...props} />
        </Profiler>
      </Panel>
    </Profiler>
  </App>
);
```

---

Calback function has following parameters

```js
function onRenderCallback(
  id, // the "id" prop of the Profiler tree that has just committed
  phase, // either "mount" (if the tree just mounted) or "update" (if it re-rendered)
  actualDuration, // time spent rendering the committed update
  baseDuration, // estimated time to render the entire subtree without memoization
  startTime, // when React began rendering this update
  commitTime, // when React committed this update
  interactions // the Set of interactions belonging to this update
) {
  // Aggregate or log render timings...
}
```

---

# Render props 
The term “render prop” refers to a <b>technique</b> for <b>sharing code</b> between React components using a <b>prop</b> whose value is a <b>function</b>.

A component with a render prop <b>takes</b> a <b>function</b> that <b>returns</b> a React element and <b>calls it instead of implementing its own render logic</b>.

```jsx
<DataProvider render={data => (
  <h1>Hello {data.target}</h1>
)}/>
```

Libraries that use render props include React Router, Downshift and Formik.

---

```jsx
import React from "react";

const Cat = ({mouse}) => {
  return (<img src="/cat.png" alt="cat" style={{ position: "absolute", left: mouse.x, top: mouse.y }} />)
};

const Mouse = (props) => {
  const [state, setState] = React.useState();
  const handleMouseMove = (event) => {
    setState({ x: event.clientX, y: event.clientY});
  };
  return (
    <div style={{ height: "100vh" }} onMouseMove={handleMouseMove}>
      {props.render(state)}
    </div>
  );
};

const MouseTracker = () => {
  return (
    <div>
      <Mouse render={(mouse) => <Cat mouse={mouse} />} />
    </div>
  );
};

```

---
layout: two-cols
---
# Testing

* <b>Unit tests</b>
  * Small test that test a single peact of functionality (component, function, service, .etc)
* <b>Integration Tests</b>
  * Higher level tests that test how different units work together as a whole
* <b>End-to-end tests</b>
  * Run in a browser and test the whole application by interacting with UI

::right::

<img style="width: 500px;" src="/images/test-types.png" >

---
layout: center
hideInToc: true
---

<img style="width: 550px;" src="https://mir-s3-cdn-cf.behance.net/project_modules/disp/26f9d324573221.563367aa26099.jpg">

---

# Popularity
---
title: StackOverflow
layout: iframe
url: https://insights.stackoverflow.com/trends?tags=enzyme%2Cjasmine%2Cjestjs%2Cmocha.js%2Creact-testing-library%2Ccypress
preload: false
hideInToc: true
---

---
hideInToc: true
---

[State of JS](https://2021.stateofjs.com/en-US/libraries/testing)

<img style="width: 500px;" src="https://stateofx-images.netlify.app/captures/js2021/en-US/testing_experience_marimekko.png">
---

[Google](https://trends.google.com/trends/explore?cat=31&date=today%205-y&q=jasmine,enzyme,jest,Testing%20library,Cypress)

<img style="width: 700px;" src="/images/testing-google.png">

---

# Unit tests
The <b>backbone</b> of testing a React application is <b><i>Jest</i></b>. It gives <b>test runner</b>, <b>assertion library</b> and <b>spying/mocking/stubbing</b> functionalities. Everything that's needed from a comprehensive test framework.

 ```js
export const sum = (a, b) => {
  return a + b;
}
 ```

 ```js
import { sum } from './sum';

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});
 ```

---

# Integration tests

 React Testing Library (RTL) -- which is used within the <i>Jest</i> testing environment -- for a more elaborate testing library for React. RTL makes it possible to <b>render</b> your components and to <b>simulate events</b> on HTML elements. Afterward, <i>Jest</i> is used for the <b>assertions</b> on the DOM nodes.

```jsx
// __tests__/index.test.tsx

import { render, screen } from '@testing-library/react'
import Home from '../pages/index'
import '@testing-library/jest-dom'

describe('Home', () => {
  it('renders a heading', () => {
    render(<Home />)

    const heading = screen.getByRole('heading', {
      name: /welcome to next\.js!/i,
    })

    expect(heading).toBeInTheDocument()
  })
})
```

---

Optionally, you add a <b>snapshot</b> test to <b>keep track</b> of any <b>unexpected changes</b> to your component:

```jsx
// __tests__/snapshot.tsx

import { render } from '@testing-library/react'
import Home from '../pages/index'

it('renders homepage unchanged', () => {
  const { container } = render(<Home />)
  expect(container).toMatchSnapshot()
})
```

---

Getting started with Jest and RTL

```js
npx create-next-app --example with-jest with-jest-app
npm i
npm run test
```

---

# End-to-end tests
Cypress is a next generation front end testing <b>tool</b> built for the modern web. We address the key pain points developers and QA engineers face when testing modern applications.

<img src="/images/cypress.png">

---

Cypress <b>enables</b> you to write <b>all types</b> of tests:

- End-to-end tests
- Integration tests
- Unit tests

---

<b>Features</b>

- <b>Time Travel</b>: Cypress takes snapshots as your tests run. 
- <b>Debuggability</b>: Debug directly from familiar tools like Developer Tools.
- <b>Automatic Waiting</b>: Cypress automatically waits for commands and assertions before moving on. 
- <b>Spies, Stubs, and Clocks</b>: Verify and control the behavior of functions, server responses, or timers. 
- <b>Network Traffic Control</b>: Easily control, stub, and test edge cases without involving your server.
- <b>Consistent Results</b>: Our architecture doesn’t use Selenium or WebDriver.
- <b>Screenshots and Videos</b>: View screenshots taken automatically on failure, or videos of your entire test suite when run from the CLI.
- <b>Cross browser Testing</b>: Run tests within Firefox and Chrome-family browsers (including Edge and Electron) locally and optimally in a Continuous Integration pipeline.

---

<b>Getting started with cypress</b>

```js
npx create-next-app@latest --example with-cypress with-cypress-app
npm i
npm run test
```

---

#  What to do next?

<b>I encourage you to start learning by yourself. Here is a list of good sources.</b>

[React documentation](https://reactjs.org/docs/getting-started.html)

[Create React App documentation](https://create-react-app.dev/docs/getting-started)

[Next JS Documentation](https://nextjs.org/learn/foundations/about-nextjs?utm_source=next-site&utm_medium=homepage-cta&utm_campaign=next-website)

[NPM site](https://www.npmjs.com/)

[Popular React libraries overview of 2022](https://www.robinwieruch.de/react-libraries/)

[Jest documentation](https://jestjs.io/docs/getting-started)

[React Testing Library documentation](https://testing-library.com/docs/react-testing-library/intro/)

[Cypress Documentation](https://docs.cypress.io/guides/overview/why-cypress)

[Dmitry Pavlutin blog](https://dmitripavlutin.com/)

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