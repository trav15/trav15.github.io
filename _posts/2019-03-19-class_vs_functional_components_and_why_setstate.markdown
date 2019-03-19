---
layout: post
title:      "Class vs Functional Components & Why setState()?"
date:       2019-03-19 23:48:08 +0000
permalink:  class_vs_functional_components_and_why_setstate
---


For my Final Project review it became evident that I did not fully understand two major concepts. First, what is the difference between class versus functional components? Second, why use setState to manage state? I will demonstrate my new understanding of these two concepts in this post and hopefully it will be helpful for anyone who might have the same problem. This is why Project Reviews can be so vital to expose your learning and understanding. Thank you to all the section leads, Nancy, Luisa, Jennifer, Howard, and Alice, who have given me great feedback and help along the way!

## Class vs Functional Components

So what is the difference between class and functional components? Well let's start off by defining each. A functional component is just what it's name implies: a function. It takes props as an argument and returns a React element. Pretty straightforward. But one gotcha is that you cannot use *setState()*. That is why it is sometimes refered to as a *stateless component*. 

The class component uses ES6 class syntax (which is syntatic sugar, let's remember) and requires an extension from React.component. This React.component extends a lot of functionality like the ability to use *setState()*. Another big difference is the use of lifecycle hooks like componentDidMount() and componentWillMount(). 

So why not use class components all the time then? Well the functional component is much simpler and with less code that is extended from React.component it serves it's purpose without bloating up your project with unneeded functionality. You can utilize separation of concerns by using these functional components as presentational components and not worry about things like state or lifecycle hooks that will be make it clearer to understand and test. 

## Why use setState()?
So with a class component you get to use setState(). So if you wanted to update state when I user clicks a "like" button you would do this:
```
this.setState({likes: this.state.likes+1})
```

but why not just change state like this:

```
this.state.likes += 1
```

Well, according to the [React documentation](https://reactjs.org/docs/components-and-props.html#props-are-read-only), 
> "Props are Read-Only. Whether you declare a component as a function or a class, it must never modify its own props. Such functions are called “pure” because they do not attempt to change their inputs, and always return the same result for the same inputs."
