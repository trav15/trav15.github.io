---
layout: post
title:      "Class vs Functional Components & Why use setState()?"
date:       2019-03-19 19:48:09 -0400
permalink:  class_vs_functional_components_and_why_setstate
---


For my Final Project review it became evident that I did not fully understand two major concepts. First, what is the difference between class versus functional components? Second, why use setState to manage state? I will demonstrate my new understanding of these two concepts in this post and hopefully it will be helpful for anyone who might have the same problem. This is why Project Reviews can be so vital as it exposes your learning and understanding or lack thereof. Thank you to all the section leads: Nancy, Luisa, Jennifer, Howard, and Alice, who have given me great feedback and help along the way! And as my journey with Flatiron School comes to an end, there will be more learning and blog posts about that learning that will be be an integral part of my career in the future. 

## Class vs Functional Components

So what is the difference between class and functional components? Well let's start off by defining each. A functional component is just what it's name implies: a function. It takes props as an argument and returns a React element. Pretty straightforward. But one gotcha is that you cannot use *setState()*. That is why it is sometimes refered to as a *stateless component*. 

```
//A functional component to display likes:

function showLikes(props) {
  return <p>You have {props.likes} likes</p>;
}
```

The class component uses ES6 class syntax (which is syntatic sugar, let's remember) and requires an extension from React.component. This React.component extends a lot of functionality like the ability to use *setState()*. Another big difference is the access to *this* and lifecycle hooks like componentDidMount() and componentWillMount(). 

```
//Here's the same component but written as a class component:

class showLikes extends React.Component {
  render() {
    return <p>You have {this.props.likes} likes</p>;
  }
}
```

So why not use class components all the time then? Well the functional component is much simpler and with less code it serves it's purpose without bloating up your project with unneeded functionality. You can utilize separation of concerns by using these functional components as presentational components to remove complications like state or lifecycle hooks in order to make it easier to understand and test. 

## Why use setState()?
So with a class component you get the method setState(). If you wanted to update state when a user clicks a "like" button you would do something like this:
```
this.setState({likes: this.state.likes+1})
```

but why not just change state like this:

```
this.state.likes += 1
```

Well, according to the [React documentation](https://reactjs.org/docs/react-component.html#state):
> Never mutate this.state directly, as calling setState() afterwards may replace the mutation you made. Treat this.state as if it were immutable. Think of setState() as a request rather than an immediate command to update the component. For better perceived performance, React may delay it, and then update several components in a single pass. React does not guarantee that the state changes are applied immediately.

React has setState() in place as part of it's state management and handles it's updates to give "better perceived performance". Calling setState() also always leads to re-render "unless shouldComponentUpdate() returns false". React also batches updates and so while using React it is best to abide and use setState() so that you can let React do it's thing the best way it sees fit. 

Understanding the React description of setState() reveals a deeper dive into how it works as it updates *asynchronously*. This can affect calls to this.state when there are multiple setState() called. From Learn.co here is a gif that shows how this asynchronous update affects when state is actually updated. 

![setState gif](https://curriculum-content.s3.amazonaws.com/react/asynchronous-state-setting-example.gif)
> The component finishes doing its current task before updating the state. In this case, it finishes executing the increment function in full before updating the state.

So knowing the why and how setState() works is a glimpse into the innerworkings of React and helps you understand what is happening under the hood. Knowing the setState() updates asynchronously will save some headaches down the road as React views it more as "request" than "immediate command to update". 
