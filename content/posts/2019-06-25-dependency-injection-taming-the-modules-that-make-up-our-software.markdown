---
author: priyankvex
date: 2019-06-25 13:29:07+00:00
draft: false
title: 'Dependency Injection: Taming the modules that make up our software.'
type: post
url: /2019/06/25/dependency-injection-taming-the-modules-that-make-up-our-software/
categories:
- Software Engineering
tags:
- code quality
- dependency injection
- design patterns
- inversion of control
- JS
- software engieering
- testing.
- unit testing
---




## Introduction







All software projects, (even relatively smaller ones) are the result of aggregation of several components and modules. As these software projects grow and evolve, the way we connect these components becomes a **win or lose factor**.  
I believe, that the way we orchestrate these components decides if the software will evolve as fast as the business needs it to, or gets tangled in its own complexity and slows the business down. If we set down the path to follow something like _Domain Driven Design_, where modules map to the domain model, this problem becomes even more prevalent.







Stripping this down to its first principles, we are left with a simple problem:  
_"Given a module X, how does it procures an instance of module Y"?_   
There are many methodologies, design patterns (ServiceLocator, Dependency Injection) and frameworks (Dagger, PicoContainer) which have taken a stab at this problem. But to understand and leverage these patterns to their fullest, it's very important that we understand the problem itself.






    
    Note: Recently I have switched to a JS stack, so I'll try to keep the code samples in JS.







### What's a Module?







Whenever I discuss the topic of wiring software "elements" together, I always find this overloaded term being used extensively in the discussions. It'll be really helpful we set the meaning of this here for the context of this post.  
By module I simply mean a glob of code that does one thing and is intended to be used without change by the application or other modules. By "without change" I mean the application doesn't alter the functionality of the module.  
As a general rule of thumb, modules should have **_high cohesion _**and**_ low coupling_**.







### A Simple Example







To get ourselves to the meat of the problem, let's consider a simple example.  
Let's say we are implementing a `PokemonFightController` which depends on a `PokemonDBLayer` to access the persistence layer. 








https://gist.github.com/priyankvex2/1e46089329965c675c60da76b968783f









https://gist.github.com/priyankvex2/3ad057fa89c76815ff921514c92f16fa








The implementation of this function is very naive. I have deliberately tried to keep it very simple. Whether you like Pokemon or not is not the point. The main point of this example is the `PokemonDBLayer` object.  
  
Let's say my friend wants to use the same controller for her application but needs to plug-in a different data source.  
If it's a different Postgres DB, then we can try to handle it by having different conf files.	    But what if by different I mean, the data source is completely different, instead of reading from a database, we want use an API service, or read from a CSV file?  
  
How does this controller procures the instance of the `PokemonDBLayer` is very interesting and decides how reusable and decoupled our `PokemonController` remains.







Expanding this into a real system, we will have many modules, each dependent on other modules to delegate some part of the work.  
And if we want our modules to be reusable, we need them to be able to use plugins, which can have different implementations but have same the interface.







So the core problem is how do we assemble these plugins that make up our application.  
This is what we are going to focus in the rest of this post?







## Inversion of Control







Whenever we talk about IoC in context of something like dependency injection, I feel very puzzled. I feel that this makes us miss the essence of this simple but rather powerful idea.  
The pressing point is, _"what aspect of control are you inverting"_?   
A simple weather checking program that polls the weather API for updates, can get the weather updates via a webhook.  The control of the program was inverted, moved away from the polling mechanism to the webhook.







![](https://priyankvex.files.wordpress.com/2019/06/screen-shot-2019-06-24-at-1.02.07-pm.png)
Dependency Diagram







For applications and modules, the inversion is how modules lookup their dependencies.  
In our example above, the Pokemon controller gets the instance of Pokemon DB Layer by directly instantiating it. This makes it rather coupled with a specific implementation of the Pokemon DB Layer. 







The approach that inverts the control here, is that the user of the plugin follows some protocol to use the plugin so that different plugins following the same protocol can be used.  
This arises a need for a specific term that denotes this patterns, IoC is rather generic. Hence we reach **Dependency Injection**.







## Dependency Injection







The basic idea of dependency injection is to have a separate object, a sort of assembler, that provides an implementation of the Pokemon DB plugin to our Pokemon controller class.







![](https://priyankvex.files.wordpress.com/2019/06/screen-shot-2019-06-24-at-1.06.20-pm.png)
Dependency Injection Dependency Diagram







In other terms, a module should be provided or injected with its dependencies instead of it creating its own. The user of the plugin should have no knowledge about how to instantiate or get the dependencies it needs. This allows the module to remain "stateless".







There are mainly a couple of forms of dependency injection:  
1. Constructor Injection:  
   Dependencies are injected into the constructor of the object.  
2. Property Injection:  
	  Dependencies are injected into the properties of the object.  
  
But since property injection requires that the object must be instantiated in an inconsistent state, it's generally avoided until and unless it's explicitly required.  
  
Let's see how we can refactor our PokemonController and PokemonDBLayer to follow a DI pattern.  
  
First step is to convert our module into a module factory. Note how we are using the Factory Pattern and passing the dependencies that the module need to the factory method.








https://gist.github.com/priyankvex2/589e87afb3d328c0f43f8c3934da874e








Next is how we wire things together. Note how our PokemonController remains reusable and decoupled with any concrete implementation of the PokemonDBLayer as it's being injected into it.








https://gist.github.com/priyankvex2/86d3a486c4b778f6b44e7d228d754a4c








## Advantages of DI







So, a question that must be arising in our minds will be, "Is DI even worth all this effort"? After all it does involve some learning curve and wiring dependencies graph manually.  
Sometimes people see DI as a way to ease out testing. I think this is just one of the many advantages that DI provides.  
Few of the many advantages that come with DI are:  
  
**1. Higher level modules stay reusable:**  
Noticed how our PokemonController was reusable against different PokemonDBLayer implementations? Using DI our higher level modules that depend on lower level modules remain reusable, even if our system if deployed in different ways.  
  
**2. Code against to an interface:**  
Dependency Injection is possible because instead of coding against a concrete implementation of a module, we code against its standard protocol or interface.  
  
**3. Easier testing:**  
The most obvious benefit of DI is ease in testing. We can easily supply testing implementation of dependencies to the module being tested without need to mock method calls.







## Concluding Thoughts







Managing dependencies within an application has been a problem that many frameworks and personalities have tried to address. Dependency Injection, Service Locator etc focus on separating the configuration of objects from their usage, which is indeed a powerful idea can has many benefits.  
DI can get complex if the dependency graph is huge, but in that case there are libraries to manage DI containers and help us out here.  




