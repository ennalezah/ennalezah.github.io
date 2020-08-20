---
layout: post
title:      "Props vs State"
date:       2020-08-20 10:29:13 +0000
permalink:  props_vs_state
---

Wow, so this is it. It's the last project I'm working on for Flatiron, and this time around, we were asked to create a React/Redux app with a Rails API. For my final project, I decided to create an app that would help people like me, who are working on improving their coding skills, to find projects they are interested in and work with a partner, just like in pair-pogramming. I realized that as you're trying to learn how to code, building projects is the best way to solidify what you learned. I think it also helps when you do pair-programming because it keeps you motivated to complete the project, and you have an extra set or eyes to help you debug.

As I was working on my app, I still felt a little iffy with props and states, which are two things that are important to know and understand when working with React or Redux. So here is a blog about it, hoping that it can help someone who is also having trouble understanding the difference as well...

## Props
Props are short for "properties", and they're attributes passed from a parent component to a child component--very similar to function parameters. With props, this data is immutable (or read-only), meaning that the child component is unable to alter the props that is coming from its parent component. 

```
class App extends Component {
  render() {	  
    name = "Daphne"
    message= "Pspsps... here kitty, kitty!"
		
    return(
      <div>
        <h1>Parent Component</h1>
		
        <CatGreeting catName={ name } catCall={ message } />
      </div>
    )
  }
} 


const CatGreeting = (props) => {  
  return (
    <div>
      <h1>Child Component</h1>
			
      <p>Hi {props.catName}! {props.catCall}</p>
    </div>
  )
}
```

In the example above, we have the parent component (App) passing the two props, ```catName``` and ```catMessage```, to the child component (CatGreeting).  In order for the child component to access these values, ```props``` is passed as an argument.  Because ```props``` returns an object, dot notation  is used to access the specific property (```props.catName``` and ```props.catCall```).

CatGreeting renders the following:
```
<h1>Child Component</h1>

<p>Hello Daphne! Pspsps... here kitty, kitty!</p>
```


## State
Unlike props where it's immutable, state is an object can be updated as necessary. State is where the component's properties are stored and is managed in the component it is initalized in.

```
class App extends Component {
  constructor() {
    super();
		this.state = {
		  name: "Daphne",
			message: "Pspsps... here kitty, kitty!"
		}
	}
	
  render() {	 		
    return(
      <div>
        <h1>Parent Component</h1>
		
        <CatGreeting catName={ this.state.name } catCall={ this.state.message } />
      </div>
    )
  }
} 


const CatGreeting = (props) => {  
  return (
    <div>
      <h1>Child Component</h1>
			
      <p>Hello {props.catName}! {props.catCall}</p>
    </div>
  )
}
```

Looking at the example above, state is initialized in the ```constructor``` method in App. To pass the value to the child component, we use ```this.state.name``` or ```this.state.message```. The child component accesses those values the same way as our previous example from props.

With state, it's meant to be updated, and this usually happens on a user event. For example, let's say we have a button in our parent component, and whenever a user clicks on it, the name and message changes. To update the state, we would use ```setState()```. It would look something like this:

```
onClick = () => {
  this.setState({
	  name: "Robocat"
		message: "Beep boop... meow!"
	})
}
```

When state is updated, this causes the component to re-render with the updated information. In this case, once the button is clicked and state is updated, the child component should render ```Hello Robocat! Beep boop... meow!```



