# Tyler McGinnis React Course

## Questions
https://tm.dev/react-course-project gives a 404 page, but\
https://tm.dev/react-course-project/ is valid

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
