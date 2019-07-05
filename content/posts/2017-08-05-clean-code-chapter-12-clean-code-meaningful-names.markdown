---
author: priyankvex
date: 2017-08-05 08:21:28+00:00
draft: false
title: 'Clean Code Chapter 1&2: Clean Code & Meaningful names'
type: post
url: /2017/08/05/clean-code-chapter-12-clean-code-meaningful-names/
tags:
- c
- clean
- code
- coding
- design
- engineering
- gist
- java
- martin
- meaningful
- names
- pattern
- programming
- robert
- short
- software
- summary
- system
---

I have started reading the book _Clean Code by Robert C. Martin, _which is considered to be a industry standard for writing maintainable and elegant code.

Because this book is such a heavy read, and each chapter is full of content and a knowledge bank in itself, for personal reference I've decided to summarise each chapter in a set of blog posts.


## **Chapter 1 : Clean Code**


This was more like chapter 0. Author describes what is clean code and cost of maintaining it. How clean code is directly related to team productivity and what makes clean code clean.

It contains views on clean code by many of industries best known people like Bjarne Stroustrup, Michael Feathers etc.

One of my favourite definitions form the book covers it best :


<blockquote>I like my code to be elegant and efficient. The logic should be straightforward to make it hard for bugs to hide, the dependencies minimal to ease maintenance, error handling complete according to an articulated strategy, and performance close to optimal so as not to tempt people to make the code messy with unprincipled optimizations. Clean code does one thing well - Bjarne Stroustrup</blockquote>




## **Chapter 2 : Meaningful Names**


Names are everywhere in software. We name our variables, our functions, our arguments, classes, and packages. Because we do it so much, we should do it well.

**1. Use intention revealing names : **

The name of a variable, function, or class, should answer all the big questions. It should tell you why it exists, what it does, and how it is used.

    
    int d; // time elapsed


Here d reveals nothing. A better name would be

    
    int timeElapsedSinceCreation;


**2. Avoid Disinformation : **
Programmers must avoid leaving false clues that obscure the meaning of code. We should avoid words whose entrenched meanings vary from our intended meaning.
ex

    
    int accountsList;


Should only be named so if it is a actually a list data structure that's used to store the accounts. Not an array or set.

**3. Make meaningful distinctions**
Entities named different, should be different, mean different.

If we have classes called

    
    ProductInfo


or

    
    ProductData


, you have made the names different without making them mean anything different. Info and Data are indistinct noise that doesn't differentiates what they actually mean.

**4. Use pronounceable names**

Makes communicating about the code easy.
ex.

    
    long genydhms;


is not a good name.

    
    long generationTimestamp;


is a better choice

**5. Use searchable names**
Avoid single letter variables and constants as they are difficult to search.

**6. Avoid Encodings**

Hungarian notations, member prefixes, interface and implementations should be avoided.

It just adds another burden to remember the encoding format being used.

**7. Avoid mental mappings**
Readers shouldn’t have to mentally translate your names into other names they already know.
ex.

    
    int r;


Where

    
    r


is _lower cased url with host name removed_ adds to much requires too much mental juggling and mapping when working with the code.

A better name would be,

    
    int urlWithoutHostName;


**8. Class Names **
Classes and objects should have noun or noun phrase names like Customer, WikiPage, Account, and AddressParser.
Avoid words like Manager, Processor, Data, or Info in the of a class. A class name should not be a verb.

**9. Method Names**
Methods should have verb or verb phrase names like postPayment, deletePage, or save.

**10. Don't be cute**

If names are too clever, they will be memorable only to people who share the
author’s sense of humor, and only as long as these people remember the joke.

Don’t tell little culture-dependent jokes like eatMyShorts() to mean abort().

**11. Pick one work per concept**
Pick one word for one abstract concept and stick with it.

It’s confusing to have a controller and a manager and a driver in the same
code base. What is the essential difference between a DeviceManager and a ProtocolController?

**11. Use solution domain names**
It's OK and preferable to use names from computer science and programming domains.
ex.
In transctionObserver

the word observer means a great deal to person who knows the observer pattern.

**12. Use problem domain name**
The code that has more to do with problem domain concepts should have names drawn from the problem domain.
ex..

    
    int mriRecord


In a healthcare app will give a great deal of context than just

    
    int record


.

**13. Add meaningful context **
Enclose names in well named functions, classes, namespaces, etc.
ex.

    
    String state;


In a class called FiniteStateMachine will mean different that in a class called Address.

**14. Don’t Add Gratuitous Context**
In an imaginary application called “Gas Station Deluxe,” it is a bad idea to prefix every class with GSD.
Frankly, you are working against your tools. You type G and press the completion
key and are rewarded with a mile-long list of every class in the system. Is that
wise? Why make it hard for the IDE to help you?



This was part one of a 16 part series on the book _Clean Code by Robert C. Martin, where e_ach post covers a gist of a single chapter.

Thanks!
