---
author: priyankvex
date: 2019-01-06 15:54:40+00:00
draft: false
title: 'How To Objectively Reason About Systems: Correctness Properties Of A System'
type: post
url: /2019/01/06/how-to-objectively-reason-about-systems-correctness-properties-of-a-system/
categories:
- Software Engineering
tags:
- design
- distributed
- distributed systems
- model
- safety
- system
- system design
---




![](https://www.tcmworld.org/wp-content/uploads/2018/05/tree-in-forest_balance.jpg)








_This post is a part of a newsletter that I run: "[Scamming The Coding Interview](http://scammingthecodinginterview.com)", which is geared towards helping people **ACE** their coding interviews. We send a coding question on weekdays along with a system design article like this one on weekends. Do subscribe If you find this article valuable._







When a new system is to be designed, the first and the most important step is to generally get the expectations from the system to be crystal clear.  
Getting this step done correctly lays the foundation for every design iteration that we make and makes sure that the system will deliver to its expectations.  
But how do we go about reasoning objectively, what is the system expected to do, or in other terms what guarantees it must make?  
  
  







[https://intravert.co/serve/e2130d1460.72.js](https://intravert.co/serve/e2130d1460.72.js)






###   
Correctness of a system







To reason about the correctness of a system, we can try listing its _**properties**_.  
For example, a URL shortener system will have the following properties:  
  
1. Uniqueness:  
Each URL is given a unique shortened URL.  
  
2. Availability of generating shortened URL:  
If any node is up which can serve the request, every request to generate the shortened URL must be fulfilled within a reasonable time.  
  
3. Correct original URL is returned for the shortened URL:  
For any shortened URL, the correct original URL is returned.  
  
4. Availability of getting the original URL:  
If any node is up which can serve the request, every request to get the original URL must return the original URL within a reasonable time.  
  
A system can be analyzed for correctness if it adheres to the properties that are expected from it.  
But can we be more incisive when defining properties of a system too?







###   
Safety and Liveness







Borrowed from the distributed systems concepts, properties of a system can be distinguished between two kinds of properties:  






  * Safety Properties  * Liveness properties





In the above example, getting a unique shortened URL for a URL is a safety guarantee, whereas getting a shortened URL for a URL in a reasonable time is a liveness guarantee.  
  
**Safety Guarantee**  
They can be informally defined as "nothing bad happens".  
More formally, if a safety property is violated, we can point to a particular point in time when it was broken.  
Once a safety guarantee has been broken, the damage has been done to the system and we cannot undo it.  
  
Ex, in the example above, we cannot afford our system to generate duplicate shortened URL of 2 different original URL.  
  
  
**Liveness Guarantee**  
Liveness property is defined as "eventually something good happens".  
It may not hold true at some point in time, but it can be restored, (ex, by giving a shortened URL back for a given URL).







An advantage of distinguishing between safety and liveness properties is that it helps in dealing with various system models and reason about the correctness of the system.  
  
Safety guarantees must hold true and cannot be broken even in the case of faults like node crashes, network failures. The system must ensure that it never does anything wrong.  
  
However, liveness guarantees can have some caveats. We could say that the system should return a response only if more than 1/3rd of the nodes are up. 







##   
Conclusion







While designing systems, it's always a very important first step to write down all the properties that the system is expected to guarantee.  
We can then classify each of those properties under either a safety guarantee or liveness guarantee.  
A system must be designed in such a way that the safety guarantees always hold true, even in the case of faults. Liveness guarantees must be served with the best effort.  
This gives us a slightly objective way to reason about the correctness of the systems.







  
_This post is a part of a newsletter that I run: "[Scamming The Coding Interview](http://scammingthecodinginterview.com)", which is geared towards helping people **ACE** their coding interviews. We send a coding question on weekdays along with a system design article like this one on weekends. Do subscribe If you find this article valuable._









