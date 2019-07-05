---
author: priyankvex
date: 2018-09-17 07:51:56+00:00
draft: false
title: 'Practical Design Patterns Part 1: The Command Pattern'
type: post
url: /2018/09/17/practical-design-patterns-part-1-the-command-pattern/
categories:
- Software Engineering
tags:
- architecutre
- command pattern
- design pattern
- home
- home system
- practical
- priyankvex
- smak
- smart home
- software
---

## ![nature-3616194_960_720](https://priyankvex.files.wordpress.com/2018/09/nature-3616194_960_720.jpg)





## **
Introduction**


Most software these days support undoing/redoing actions. For example, text editors support undoing what we have written, file managers support undoing file creation/deletion etc. It's a good UX practice to make software forgiving and allow users to undo their actions.

I always wondered how was this implemented?  On a critical analysis, it seems as if the object on which the actions are taking place receives them from somewhere else, like a _command. _The object that invokes the actions, the object on which the actions are performed and the actions themselves are _decoupled._ This is exactly why the Command Pattern exists.


## **
The Command Pattern**


The Command Pattern is a behavioral design pattern, i.e it tries to simplify communication among objects and improve flexibility, in which an operation is encapsulated with all the information it needs to perform the action in an object.

What the above statement simply means is that we create a class that represents an operation and its instance holds all the data and methods that are needed to perform the action.


## **Advantages of The Command Pattern**





	  1. The Invoker and the actions can be decoupled. The invoker doesn't need to know how the operations are implemented.
	  2. It is easy to change an operation and add new operations.
	  3. Multiple commands can be grouped together to execute them in order. (This is especially helpful in designing systems that support multi-level _undo_.)



## **
Implementation and Usage**


We are going to implement a simple home control system that supports a certain set of actions that the user can perform and an undo feature to allow a user to undo her actions.

Overview of the system looks as follows:



	  1. Home is the class on which the actions are performed.
	  2. SmartRemote is the class that allows performing actions on the Home.
	  3. FanOnCommand, FanoffCommand, FanSlowCommand, FanFastCommand are 4 commands that are supported.
	  4. A user can undo her actions.

Following is the implementation of the system explained above and showcases the power of the command pattern.

The example is complex enough to properly showcase the functionality and advantages of the design pattern.

https://gist.github.com/priyankvex/d594872a222fbc50b72105f4d7b3c038


## 
Conclusion


The Command Pattern is a behavioral design pattern that allows encapsulating actions in an object that has all the information available with it to perform the action.

This makes it a good candidate to implement systems that have GUI driven actions, transactional behaviors, multi-level undo etc.

Practical Design Patterns is an attempt to cover the most common design patterns with strong and practical explanation and implementation. Stay tuned for the next post in the series.


# That’s all, folks!



