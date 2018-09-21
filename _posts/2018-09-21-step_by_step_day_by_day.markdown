---
layout: post
title:      "Step by Step, Day by Day"
date:       2018-09-21 13:14:47 +0000
permalink:  step_by_step_day_by_day
---


> What's something subtle but important to understand about Procedural Ruby? Explain why it's important and what you need to know about it.

Procedural Ruby separates states and behaviors of whatever problem you're trying to solve. You have your data, that may represent the state of something like a person's name or weight:
```
name = "Travis"
weight = 170
```
And then you have your methods, that may represent how that person's weight may change after a big meal:
```
def eat_big_meal
  puts "I just ate a big meal"
  weight += 5
end
```

All of these thing just exisit in a big, open world that is your program. And that means that you can use any of your methods anywhere within the program. Compared to OOP where methods would be encapsulated in an Object and thus can only be used by that Object, methods are more free and open to be used by anything in your program. Any change made to a method will be simpler to implement(since it's only change in one method) and immediately available "globally" as well. 

![](https://i.giphy.com/media/WoD6JZnwap6s8/200w_d.gif)

Procedural Ruby sets the baseline for learning and understanding the different data types and variables that Ruby has to offer, and then allows you to create methods that can act and/or effect data. You get introduced into thinking in steps or procedures, breaking down each element or action into simple components. For the Procedural Ruby section on Flatiron's Learn.co they teach you through the problem of a CLI tic-tac-toe game. Tic-tac-toe can be broken down into steps, like the alternating turns of the players, and also states like what player is "X" or "O" and what the game board looks like at the current time. 

So to start with Procedural Ruby is a great way to start thinking in a way that breaks down your problem into components and steps. Separating state and behaviors is a good way to more simply understand these different sections and how they feed into and relate to each other. Once I moved into OOP I understood the combining of state and behavior as *encapsulation* of what would have been separate in Procedural Ruby. 


