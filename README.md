
# React--Robofriends

This project is fully a react project where its fundaments such as ```components, props and its css``` and others linked are shown

## Demo

## Features

- Making of React components.
- Use of state related with props and others recently learned techniques such as destructuring and others.

## Lessons Learned

Few of the lessons learned are, how to start react app, the alerts it gives and how to break components and the use of props.

1. In index.js I changed the App.js to any other components I needed like the Card.js
2. I created the structure of Card.js & provided its HTML structure, these structure could be Hard coded but later on changed dynamic as per the properties passed in index.js which came from robots.js.
3. The respective Card.js will have its styling as well.
4. Then in index.js I came and passed the properties, and imported from robots.js and showed then per array values.
5. Same props need to pass into card.js with destrutring method to use them in this case and makes our life easier.

```
// Card.js
import React from 'react';

const Card = (props) => {
  const { name, email, id } = props
  return (
    <div className='tc bg-light-green dib br3 pa3 ma2 grow bw2 shadow-5'>
      <img src={`https://robohash.org/${id}?size=200x200`} alt='robots' />
      <div>
        <h2>{name}</h2>
        <p>{email}</p>
      </div>
    </div >


  )
};


export default Card;



// Index.js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import Card from './Card';
import 'tachyons';
import reportWebVitals from './reportWebVitals';
import { robots } from "./robots"

ReactDOM.render(
  <React.StrictMode>
    <div>
      <Card id={robots[0].id} name={robots[0].name} email={robots[0].email} />
      <Card id={robots[1].id} name={robots[1].name} email={robots[1].email} />
      <Card id={robots[2].id} name={robots[2].name} email={robots[2].email} />
    </div>
  </React.StrictMode>,
  document.getElementById('root')
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```
### Stateless Functional Component
There are two ways to create a React component. The first way is to use a JavaScript ```function another is class Component```. Defining a component in this way creates a stateless functional component. The concept of state in an application will be covered in later challenges. For now, think of a stateless component as one that can receive data and render it, but does not manage or track changes to that data. 
To create a component with a function, you simply write a JavaScript function that returns either JSX
One important thing to note is that React 

```
const DemoComponent = function() {
  return (
    <div className='customClass' />
  );
};
```

### Class Components:
The other way to define a React component is with the ES6 class syntax. In the following example, Kitten extends React.Component:
```
class Kitten extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <h1>Hi</h1>
    );
  }
}
```
This creates an ES6 class Kitten which extends the React.Component class. So the Kitten class now has access to many useful React features, such as local state and lifecycle hooks. Don't worry if you aren't familiar with these terms yet, they will be covered in greater detail in later challenges. Also notice the Kitten class has a constructor defined within it that calls super(). It uses super() to call the constructor of the parent class, in this case React.Component. The constructor is a special method used during the initialization of objects that are created with the class keyword. It is best practice to call a component's constructor with super, and pass props to both. This makes sure the component is initialized properly. For now, know that it is standard for this code to be included. Soon you will see other uses for the constructor as well as props.

#### Parent & Child Component:

```
const ChildComponent = () => {
  return (
    <div>
      <p>I am the child</p>
    </div>
  );
};

class ParentComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>I am the parent</h1>
        { /* Change code below this line */ }
<ChildComponent/>

        { /* Change code above this line */ }
      </div>
    );
  }
};
```
Rendering ES6 style class components within other components is no different than rendering the simple stateless functions components 

A full Funtional Componets also including the Render Method: 

```
class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        {/* Change code below this line */}
<Fruits />
<Vegetables />
        {/* Change code above this line */}
      </div>
    );
  }
};

// Change code below this line
ReactDOM.render(<TypesOfFood />, document.getElementById("challenge-node"));
```

### Props (Next important feature in React)
Passing the properties to the child component. This can be a custom component created by us or supported by React.

```const Welcome = (props) => <h1>Hello, {props.user}!</h1>``` <br>

We use this concept in JavaScript Objects as well.

```PASS THE PROP TO THE APP ONE WHERE IT IS BEING RENDERED => COME AND USE IT IN THE STATELESS FUNCTION CREATED TO MAKE IT DYNAMIC```

Example 
```
const CurrentDate = (props) => {
  return (
    <div>
      { /* Change code below this line */ }
      <p>The current date is:  {props.date}</p>
      { /* Change code above this line */ }
    </div>
  );
};

class Calendar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>What date is it?</h3>
        { /* Change code below this line */ }
        <CurrentDate date={Date()}/>
        { /* Change code above this line */ }
      </div>
    );
  }
};
```

### An Array to the Prop

```
// Example also the power of join
const List = (props) => {
  { /* Change code below this line */ }
  return <p>{props.tasks.join(", ")}</p>
  { /* Change code above this line */ }
};

class ToDo extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>To Do Lists</h1>
        <h2>Today</h2>
        { /* Change code below this line */ }
        <List tasks={["wow", "wow"]}/>
        <h2>Tomorrow</h2>
        <List tasks={["wow", "wow", "woow"]}/>
        { /* Change code above this line */ }
      </div>
    );
  }
};
```
Assigning the Default Properties:
```MyComponent.defaultProps = { location: 'San Francisco' }``` // For Strings <br>
```MyComponent.defaultProps = { location: San Francisco }``` // For Numbers <br>

```//Props for Numbers =:
    return <Items quantity={10}/>

//Overriding the Default Props:
  return <Items quantity={10}/>
```

//Using the PropTypes:
```MyComponent.propTypes = { handleClick: PropTypes.func.isRequired }
Items.propTypes = { quantity: PropTypes.number.isRequired }
```

#### Accesing the Props in the Class Component of React:
```
   <Welcome name="sky" />
  <p>Hello, <strong>{this.props.name}</strong>!</p>  
```
A stateless functional component is any function you write which accepts props and returns JSX. A stateless component, on the other hand, is a class that extends React.Component, but does not use internal state (covered in the next challenge). Finally, a stateful component is a class component that does maintain its own internal state. You may see stateful components referred to simply as components or React components.

Our Objective is to create the best stateless fucntional components. This helps contain your state management to a specific area of your application. In turn, this improves development and maintenance of your app by making it easier to follow how changes to state affect its behavior.

### State and its different features (Another very important Topic):

State consists of any data your application needs to know about, that can change over time. <br>
You want your apps to respond to state changes and present an updated UI when necessary. React offers a nice solution for the state management of modern web applications. You create state in a React component by declaring a state property on the component class in its constructor. This initializes the component with state when it is created. The state property must be set to a JavaScript object. Declaring it looks like this: <br>
```
this.state = {
  name: "name"
}
```
You have access to the state object throughout the life of your component. You can update it, render it in your UI, and pass it as props to child components. 
Note that you must create a class component by extending React.Component in order to create state like this.

State is one of the most powerful features of components in React. It allows you to track important data in your app and render a UI in response to changes in this data. If your data changes, your UI will change. React uses what is called a virtual DOM, to keep track of changes behind the scenes. When state data updates, it triggers a re-render of the components using that data - including child components that received the data as a prop. React updates the actual DOM, but only where necessary. This means you don't have to worry about changing the DOM. You simply declare what the UI should look like.<br>

Note that if you make a component stateful, no other components are aware of its state. Its state is completely encapsulated, or local to that component, unless you pass state data to a child component as props. This notion of encapsulated state is very important because it allows you to write certain logic, then have that logic contained and isolated in one place in your code.

A quick example of State
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    return (
      <div>
        { /* Change code below this line */ }
<h1>{this.state.name} </h1>
        { /* Change code above this line */ }
      </div>
    );
  }
};


There is another way to access state in a component. In the render() method, before the return statement, you can write JavaScript directly. For example, you could declare functions, access data from state or props, perform computations on this data, and so on. Then, you can assign any data to variables, which you have access to in the return statement.

//Another Way to Render State in the UI

class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    // Change code below this line
const name = this.state.name
    // Change code above this line
    return (
      <div>
        { /* Change code below this line */ }
<h1>{name}</h1>
        { /* Change code above this line */ }
      </div>
    );
  }
};
```

// Set State with this.setState
The previous challenges covered component state and how to initialize state in the constructor. There is also a way to change the component's state. React provides a method for updating component state called setState. You call the setState method within your component class like so: this.setState(), passing in an object with key-value pairs. The keys are your state properties and the values are the updated state data. For instance, if we were storing a username in state and wanted to update it, it would look like this:

```
this.setState({
  username: 'Lewis'
});
```
This means is that state updates through the setState method can be asynchronous.

The Change of the state when clicked:
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    // Change code below this line
this.setState({
  name: "React Rocks!"
})
    // Change code above this line
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

#### Counter App 

```
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
    // Change code below this line
this.increment = this.increment.bind(this);
this.decrement = this.decrement.bind(this);
this.reset = this.reset.bind(this);
    // Change code above this line
  }
  // Change code below this line
increment() {
this.setState(state => ({
  count: state.count + 1
}))
}

decrement() {
this.setState(state => ({
  count: state.count - 1
}))
}

reset() {
this.setState({
  count: 0
})
}

  // Change code above this line
  render() {
    return (
      <div>
        <button className='inc' onClick={this.increment}>Increment!</button>
        <button className='dec' onClick={this.decrement}>Decrement!</button>
        <button className='reset' onClick={this.reset}>Reset</button>
        <h1>Current Count: {this.state.count}</h1>
      </div>
    );
  }
};
```


## Optimizations


## Screenshots



## Tech Stack

**Client:** React, JS, CSS

## Documentation


# Notes 

