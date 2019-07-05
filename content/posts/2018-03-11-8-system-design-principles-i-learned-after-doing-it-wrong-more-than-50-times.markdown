---
author: priyankvex
date: 2018-03-11 07:16:00+00:00
draft: false
title: 8 System Design Principles I learned After Doing It Wrong More than 50 Times!
type: post
url: /2018/03/11/8-system-design-principles-i-learned-after-doing-it-wrong-more-than-50-times/
tags:
- '8'
- coding
- deisgn pattern
- design
- engineer
- engineering
- google
- how
- iterate
- lean
- pattern
- principles
- product
- programming
- ship
- software
- software engineing
- system
- technology
---

![laptop-3190194_960_720](https://priyankvex.files.wordpress.com/2018/03/laptop-3190194_960_720.jpg)




At [Squad](https://www.squadplatform.com/), we strive to build awesome products to solve customer(internal and external) needs. As a product engineer, paramount part of your job is to design and build products. Dig deep into the root cause of the problems, design solutions and implement them as the end product.

Over the course of my journey so far, here are the 8 system and product design principles that I've learned from other awesome people at Squad, from feedback and simply doing it not right enough multiple times.


# 1. What is the underlying problem that led to the feature request?


At Squad, you don't just code the requirements into the software. As a product engineer, it's your responsibility to remove the layers and expose the root problem that led to the feature requirement.

Get to know the root cause of the problem that you are trying to solve. Or even better, as the lean principles say "genchi genbutsu" i.e go and see it yourself.


# 2. How can you make the feature more robust, reliable and usable?


Once the essential feature requirements are finalized, we must press on how can we make the feature more robust, reliable and usable?

Things to ponder upon and take into consideration can be :



	  1. The persona of the users that's going to use that.
	  2. Scenarios in which that feature would be used. Ex, if in the case of fires, than show more data than needed for faster resolutions.
	  3. Building in the quality in the product itself or "Jidoka" as said in lean.



# 3. What is the first iteration going to be?


Given the time and resources you have., what is the best possible first iteration of the product going to be? If it's a large system or something you are building from scratch, there are always going to be iterations.

The main idea here should be to move fast and get things shipped. Good enough and shipped on time is always better than perfect and in-development forever.


# 4. How easy will it be to make iterations on the current feature?


The design should incorporate all the non-functional requirements to make future iterations easy.

Scale the feature? Change a component? Use a different 3rd party service? Your implementation should be flexible enough to incorporate and encourage these enhancements.

Design patterns are your best friend here.


# 5. What are the potential bottlenecks with scale?


Scale-land is where everyone wants to be, but it is scary. It breaks what was not supposed to break and has witnessed more horror stories than a haunted castle.

What are the potential bottlenecks that are not a problem now, but will break at 5X, 10X or 100X scale?

List them down on the feature ticket, or better document it in the code itself.


# 6. What's the data that has to be captured and how will it be consumed?


Every feature in the product will need some data that needs to be captured to track it. It can be but not limited to:



	  1. Action logs.
	  2. Event logs.
	  3. Metrics
	  4. Failures.
	  5. Anamolies.

What affects this majorly is **how that data will be consumed**? Store it in a structure that will make the consumption of data easy and efficient. Afterall, the only motive to store data is to use it.


# 7. How good the developer experience will be when interacting with the code base of that feature?


There can be many developers who'll use or modify the code that you are going to write.

How will be their experience when doing that? Ex. Will the test cases you wrote, make them feel confident enough to make changes fast?

Few points to consider:



	  1. Is the code well documented?
	  2. Are test cases strong enough?
	  3. Is the code, re-usable where it makes sense?
	  4. Are functions small and code, simple to read?



# 8. What metrics will determine that the feature has been implemented successfully?


Finally, after all the fun-time you had creating the feature, what will determine that the feature has been implemented successfully?

The data you tracked will be of paramount importance here.

It can be the case that to track this quantitatively is not possible, but can you track the qualitatively in that case?

The idea here is that you can't improve what you can't measure?

Processing 100,000 requests? Fewer errors by the users? 95% work done by the new system instead of old one?

This can and will involve more stakeholders of the team and not just the developer.


# Conclusion


Obviously, this is not the exhaustive things to take into consideration while designing a system or a product as an engineer. This just covered what I have learned so far by just doing things wrong or not right enough multiple-times.

It's fun to build stuff! Continuously improve ("Kaizen" in lean)! Keep iterating! Keep shipping!






# That’s all, folks!



