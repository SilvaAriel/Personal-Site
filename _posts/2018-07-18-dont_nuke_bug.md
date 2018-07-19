---
layout: post
title: "Don't nuke the bug"
ref: nuke_the_bug
date: 2018-07-18
categories: bug
lang: en
---

We all have. 

When we see ourselves before a real bug we don't use big tools to kill it. We use our feet or a insecticide.
But things are a little different when we find a bug in our code. We usually try to solve it without much thinking and end up using a nuke weapon. It might kill the bug but it will also create a mess even bigger than there was before. 
We have to use the right tools to solve our bugs. But to do that, we have to understand it first. 
I have nuked a few bugs myself and I know the damage it causes. Thanks to that I decided to take a different approach to solve ~~crush~~ those nasty bugs.

These are the steps I follow:
* Write the main problem.
* Find where it began.
* Create 3 hypothesis to solve the bug. 
* Try one at time. 

### Explanation
**Write the main problem**:
More often than not we lose ourselves trying to solve a problem. Maybe we begin to Google for the solution, but then we find something interesting and begin to read it instead. We have to keep in mind that our only goal is to solve the current bug. Leave the other cool stuff for later.

**Find where it began**:
Where the bug was born? We have to find where our data begin to misbehave to be able to understand what actually went wrong. 

**Create 3 hypothesis to solve the bug**:
What do you think is probably the cause of the bug? Write 3 possible solutions you think you can apply.
But why 3? It can be any number you want, but not just 1. Why? Because these steps are supposed to keep us focused. If we prove our only hypothesis wrong we might go back to aimlessly Google for the eternity! 

**Try one at time**:
Then, after all that above, we can choose the hypothesis we think it is closer to the root of the problem and begin to implement it.

These are the steps I take to solve a bug. You can take it and adapt to your way. It's not an exhaustive list, so I'm constantly improving it. You can do the same.

See ya!