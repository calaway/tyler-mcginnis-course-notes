# Tyler McGinnis React Course

## Course Overview
### Introduction, Philosiphy, and Tips
Philosophy: Ideal education happens when __mastery is fixed__, but __time spent__ to attain mastery __is variable__. Traditional education often gets this backward.

Lesson structure will be
- Introduction
- Practice
- Solution
- Quiz
- Project
- Bonus material

### Projects
We will build two projects, one together and one on our own, GitHub Battle and Hacker News, respectively.

GitHub Battle: https://tm.dev/react-course-project/

Hacker News: https://tm.dev/react-course-curriculum/

### State of React
This course will teach "classic" react, without hooks, since it is still relevant and important. React hooks will be covered in a separate course

## React Overview
### Why React?
React is a library for building user interfaces.

Elements that make React great:
- Composition
- Unidirectional dataflow
- Declarative UI
- Just JS
- The right abstraction
- Community
- The team

### The React Ecosystem
Babel is like a code transformer. You put code in that a browser could not understand and you get code out that a browser can understand.

Webpack will intelligently look at your exports & imports and bundle all your modules together into one file that the browser understands.

React router renders specific components based on the current url path. Entire API is simply react components.

Styling: You can use traditional styling, which is no different than styling any other website, or you can use CSS in JS that encapsulates styles to the component.

Styled components allows you to define CSS in JS styles as components themselves

Redux is a state maintainer. Recommend ignoring Redux entirely until you're comfortable with React.

### Imperative vs Declarative

Declarative says what needs to be done, without focusing on how. Imperative spells out the steps of how to get it done.

Many (if not all) declarative approaches have some sort of underlying imperative abstraction.

## The Road to Hello World
### First Component
Components can have three different aspects to them
1. State: Components manage their own state
1. Lifecycle
1. UI

```js
ReactDOM.render(
  // React element,
  // Where to render the element to
)
```

## Passing Data to Components
### Introduction to Props
Props are to components, what arguments are to functions.

## Rendering Lists
### Rendering Lists in React
>> "Eventually you come to accept that as an app developer, your primary job is to render lists."
>>
>>-- Wayne Gretzky
>
> -- Michael Scott

Always add a key to your list items so React can render them as efficiently as possible.

## Managing State
### The "this" keyword: Intro and Implicit Binding
Four rules:
- Explicit Binding
- Implicit Binding
- new Binding
- window Binding

Where is the function invoked?

Implicit Binding
Left of the dot at call time

### Managing State in React
```js
  constructor(props) {
    super(props)

    this.state = {
      mode: 'initial state'
    }

    this.handleEvent = this.handleEvent.bind(this)
  }
```
By binding `this`, regardless of where the `handleEvent` function is invoked, the `this` keyword is always going to reference this component.

## Functional Components
### Pure Functions
If a component is only a `render` method, then it can be written as a function instead of a class.

These two are equivalent:
```js
class HelloWorld extends React.Component {
  render () {
    return (
      <div>Hello {this.props.name}</div>
    )
  }
}
```
```js
function HelloWorld (props) {
  return (
    <div>Hello {props.name}</div>
  )
}
```

## The Component Lifecycle
### The Component Lifecycle
The component lifecycle can be broken down into three parts:
1. Mounting: When the component gets added to the DOM.
1. Updating: When the copmonent updates its state or receives new data via props.
1. Unmounting: When the component gets removed from the DOM.

Tools:

`constructor` is used to set initial state.

`componentDidMount` is invoked once when the component is mounted to the DOM.

`componentDidUpdate` is invoked every time the state or props change.

`componentWillUnmount` will be invoked once right before a component is unmounted from the DOM.

## Handling Form State
### Forms in React: Controlled vs Uncontrolled Components
In an uncontrolled component, the state is managed by the DOM, as usual. It can be accessed by React once it is submitted. This is _not_ the React way.

In a controlled component, the state of the form lives within the React state. This is the React way and gives full control within React.

## Building Reusable Components
### Default Props
Class component example:
```js
class StarRating extends React.Component {
  ...
}

StarRating.defaultProps = {
  color: '#ECB244'
}
```

Function component example:
```js
function StarRating ({ color = '#ECB244' }) {
  ...
}
```

## Code Sharing
### Higher Order Components
When you pass a function as an argument, that function is called a __callback function__. The function you're passing the callback function to is called a **higher-order function**.

### Hover Render Prop
We were able to accomplish the same thing with a Hover render prop that we were with a Higher Order Component.

Tyler prefers render props over HOC. Tyler prefers passing the render prop as a child rather than a prop.

## Better Classes with Class Fields
### Class Fields
Class fields are currently a stage 3 ECMAScript proposal. To use them, first install this babel pluggin:
```
npm install --save-dev @babel/plugin-proposal-class-properties
```
Then add this to `package.json`
```json
  "babel": {
    "plugins": [
      "@babel/plugin-proposal-class-properties"
    ]
```
Then this class
```js
class PlayerInput extends Component {
  constructor(props) {
    super(props)
    this.state = {
      username: ''
    }

    this.handleChange = this.handleChange.bind(this)
  }
  handleChange(event) {
    this.setState({
      username: event.target.value
    })
  }
  render() {
    ...
  }
}

PlayerInput.propTypes = {
  id: PropTypes.string.isRequired,
  label: PropTypes.string.isRequired,
  onSubmit: PropTypes.func.isRequired,
}

PlayerInput.defaultProps = {
  label: 'Username',
}
```
can be refactored to
```js
class PlayerInput extends Component {
  static propTypes = {
    id: PropTypes.string.isRequired,
    label: PropTypes.string.isRequired,
    onSubmit: PropTypes.func.isRequired,
  }
  static defaultProps = {
    label: 'Username'
  }
  state = {
    username: ''
  }
  handleChange = (event) => {
    this.setState({
      username: event.target.value
    })
  }
  render() {
    ...
  }
}
```
