---
author: priyankvex
date: 2018-03-25 11:32:12+00:00
draft: false
title: 'Practical Problem Solving Framework: Inspired By The Toyota Way'
type: post
url: /2018/03/25/practical-problem-solving-framework-inspired-by-the-toyota-way/
tags:
- books
- business
- coding
- design
- developer
- engineer
- entrepreneurship
- framework
- fun
- ideas
- inspiration
- Internet
- lean
- learning
- problem
- programming
- software
- solving
- technology
- toyota
---

![toyota-7-step-pratical-problem-solving-process](https://priyankvex.files.wordpress.com/2018/03/toyota-7-step-pratical-problem-solving-process.png)


We all will agree to a certain point that having a system/process for anything reduces chances of errors.

As an engineer or someone people look forward to propose solutions to problems it's beneficial to have a framework in place to solve problems effectively.

Recently I was reading _**The Toyota Way, **_and it suggested a framework to **_Practical Problem Solving. _**It almost felt trivial that this sort of framework would be invaluable to software engineers too (in fact for everyone).

When confronted with a problem, first we want to make it crystal clear and get a grasp of the real point of cause. That's followed by a series of 5 WHYs? to investigate the root cause. And finally countermeasures, evaluations, and countermeasures.


## 1. Initial Problem Perception


Large, vague and complicated problem is presented. The first step is to perceive all the information available at this point information of time.

Ex. "Hey! Metric X is showing incorrect value"

This doesn't show the actual problem, but just a perception of how some internal user saw it.


## 2. Clarify The Problem


Next step is to clarify the problem to scope it down. Go and see the problem yourself. Analyse it and get a clear understanding.

As you are seeing the problem first hand, we want to gather as much information as possible.

Ex. So the entire analytics data was actually not consistent.


## 3. Locate Point Of Cause


Next step is to dig a little deeper and try finding the point fo cause.

Where is the problem observed? Where is the likely cause? This will lead us to the vicinity of the root cause, which we find in step 4.

Ex. Analytics system is working correctly, just that it sometimes doesn't get updated every 5 minutes like it's supposed to.

Here we rule out other possible causes, like a bug in the code or wrong data was tracked in the first place.


## 4. Ask, 5 WHYs? Investigation of  the root cause


Here from the direct cause, we expose and go deep to the root cause of the problem by asking WHY five times.

Ex.

1. 1st why - Why was data inconsistent: Because analytics didn't get updated on time.

2. 2nd Why - Why analytics were not updated on time - Because scheduled ETL jobs didn't run on time.

3. 3rd Why - Why the schedule jobs didn't run on time - Because CPU usage was 100%

4. 4th Why - Why CPU reached 100% - Because server instance size was not enough to handle increased number jobs.

5. 5th Why - Why server size was not enough to handle the spike in usage -  Because our auto-scaling is slow.

By asking a series of 5 whys, we can generally get to the root cause of the problem and fix it there instead of just duct-taping it and be waiting for it to rise again.


## 5. Countermeasures


This step is fixing the root cause of the problem so that this doesn't come up again.

Ex. Moved to a more sophisticated auto-scaler to manage spikes in usages and setting up alerts to monitor the performance.


## 6. Evaluate


After the countermeasure have been executed, it's important to evaluate the effect post that. Was the problem solved?

Ex. "Now analytics are always in sync and even if they miss getting updated, we get an alert to know it beforehand and take action."


## 7. Standardize


This resonates with another Toyota principle of_** jidoka**, _meaning building in the quality.

How can we standardize the countermeasures such that similar problems are not faced again? How can we propagate our learnings across the organization?

Ex. "Document and standardize the process that for all our instances and jobs proper alerts must be in place so that we know when they are malfunctioning"


## Conclusion


This was my take on how we can learn from a cross-discipline organization like Toyota on how to have a process and framework in place to solve problems effectively.

Afterall, problem-solving is supposed to be fun and having a proper framework in place, helps us keep it that way!


# That’s all, folks!



