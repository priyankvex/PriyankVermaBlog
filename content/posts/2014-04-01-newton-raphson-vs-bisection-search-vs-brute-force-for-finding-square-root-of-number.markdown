---
author: priyankvex
date: 2014-04-01 06:28:36+00:00
draft: false
title: Newton-Raphson vs Bisection Search vs Brute force for finding square root of  number.
type: post
url: /2014/04/01/newton-raphson-vs-bisection-search-vs-brute-force-for-finding-square-root-of-number/
tags:
- algorithms
- bisection
- newton raphson
- phython
- square root
---

**Computers** are meant to compute things. Finding square root is a very basic algorithm which can be coded in basically 3 ways :
All 3 ways are based on the **_Guess and check method _** A.K.A **_Exhaustive Enumeration_**.
_ >1. Brute force method :_

__ In this method we test all the possible values and test them .

_2. Bisection Search : _

By cutting the problem into the half after every iteration. This is much more effective then brute force method which we will see later in this post.

_3. Newton-Raphson method :_

This method is based on the formula given by sir newton that if, g is a guess of a root of polynomial then,
**g= g - g(x)/g'(x) **
is a better guess.


### We will be using phython to code the algorithms because it is most easy to understand.




## Brute force method


[caption id="attachment_17" align="aligncenter" width="300"][![brute force](http://priyankvex.files.wordpress.com/2014/04/bisection.png?w=300)
](http://priyankvex.files.wordpress.com/2014/04/bisection.png) Algorithm of brute force method to find square root.[/caption]

The pic shows the algorithm of brute force method and also counts the steps taken to find the square root.
Output of the above code is :

[caption id="attachment_18" align="aligncenter" width="300"][![Output of Brute force method ](http://priyankvex.files.wordpress.com/2014/04/pic1.png?w=300)
](http://priyankvex.files.wordpress.com/2014/04/pic1.png) The pic shows the output of brute force method to find the square root of 255.  
Look at the number of steps.[/caption]

As you can see the square root of 255 was approximated to 15.9685 , which is pretty close but the guesses made by the computer were 159685, which is pretty large.
This is the drawback of this method.


## Bisection Search method :


Algorithm of bisection search method is shown in the pic, which also shows the number of steps.

[caption id="attachment_19" align="aligncenter" width="300"][![Bisection Method](http://priyankvex.files.wordpress.com/2014/04/pic2.png?w=300)
](http://priyankvex.files.wordpress.com/2014/04/pic2.png) Bisection method to find the square root of a number.[/caption]

The output of the above code is given below.

[caption id="attachment_20" align="aligncenter" width="300"][![Output of bisection Search.](http://priyankvex.files.wordpress.com/2014/04/pic3.png?w=300)
](http://priyankvex.files.wordpress.com/2014/04/pic3.png) Output of bisection search . Look at the number of steps.[/caption]

So, this also approximated the answer pretty well. But look at the number of steps, just 12. Compare this to the previous result.
Surely, this method is much better and faster but we can get much better results using the next method.


## Newton-Raphson method :


The algorithm of this method is shown in the pic, along with the number of guesses made by the computer.

[caption id="attachment_21" align="aligncenter" width="300"][![Newton raphson method ](http://priyankvex.files.wordpress.com/2014/04/pic4.png?w=300)
](http://priyankvex.files.wordpress.com/2014/04/pic4.png) Algorithm of newton raphson method.[/caption]

The output of the above method is given below. Look at the number of guesses taken and the accuracy of the result.

[caption id="attachment_22" align="aligncenter" width="300"][![Output of newton Raphson method](http://priyankvex.files.wordpress.com/2014/04/pic5.png?w=300)
](http://priyankvex.files.wordpress.com/2014/04/pic5.png) Ouptut of newton Raphson method. look at the number of guesses made by the computer.[/caption]

As this method is clearly the fastest of all. And took only 6 steps to guess the pretty accurate value.
