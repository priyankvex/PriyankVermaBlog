---
author: priyankvex
date: 2018-04-14 18:16:23+00:00
draft: false
title: 'Fail Fast: Hone Your Ability to Recover and Respond Quickly'
type: post
url: /2018/04/14/fail-fast-hone-your-ability-to-recover-and-respond-quickly/
tags:
- A
- abilities
- ability
- about
- activity
- actual
- against
- all
- allows
- an
- and
- API
- applied
- are
- arise.
- around
- as
- ask
- aspects
- at
- automated reporting
- available
- be
- becomes
- best
- better
- bound
- broker
- bug
- bugs.
- But
- called
- can
- careful
- cases
- certainly
- Chaos
- check
- close
- Conclusion
- confidence
- contingency
- control
- counter-intuitive
- creating
- critical
- date
- day.
- debugging.
- decide
- defense
- deployed
- develop
- dilemma
- Don't
- done
- down?
- drills
- due
- during
- effective
- effectively
- email
- emails.
- emergencies.
- engineering
- engineers
- enough
- enough for actual
- even
- every
- face
- fail
- failing
- failures
- fast
- feature
- find
- folks!
- for
- forward
- from
- gaping
- get
- gets
- getting
- gives
- Go
- goes
- handle
- have
- having
- helps
- helps them
- high
- higher
- holes
- hone
- hours
- how
- ideal
- if
- important
- in
- increase
- infrastructure
- investing
- is
- It's
- it.
- kills
- know
- knows
- learning
- levels.
- leverage
- log
- logs
- lower
- made
- major
- management
- matter
- may
- member
- metrics
- midnight
- mind
- mock
- monitoring
- Monkeyrandomlyndonly
- more
- move
- much
- my
- Netflix
- new
- next
- 'No'
- Not
- of
- off.
- office
- often.”
- 'on'
- our
- out
- own
- pager-duty
- panic
- peace
- perform
- performance
- plan
- plans
- point
- Practice
- prepare
- prepares
- prioritization?
- problems
- processes.
- product
- properly.
- questions
- quickly.
- raises
- ready
- realize that
- recover
- recovering
- recovery
- release?
- reliability.
- reliable
- reponed?
- resolve
- respond
- right
- scenarios
- scripts
- service
- services
- sets
- should
- sick?
- sites
- So
- software
- some
- sound
- spike
- strategy
- streamed
- stress
- success
- such
- Suddenly
- Surfaces
- systems.
- tackle
- talk
- task
- team
- that
- that's
- the
- their
- them.
- theme
- there
- they
- things
- this
- ticket?
- time.
- to
- tool.
- tools
- turns
- unexpected
- urgent
- us
- usage?
- used
- user
- using
- via
- way
- we
- well
- what
- when
- why
- will
- with
- work-through
- working
- wrap
- wring
- write
- you
- Your
- yourself
---

![veteran-turned-software-engineer-e1485204975427](https://priyankvex.files.wordpress.com/2018/04/veteran-turned-software-engineer-e1485204975427.jpg)


It's close to midnight and you are about to wrap your day off. Suddenly you get a pager-duty to resolve a critical bug that's failing some of the automated reporting emails.

You go on to check the logs in the log management tool. This is not the ideal time to find out that logs are not getting streamed to the log management service properly.

Next, you decide to check the performance metrics of the email API and you realize that you don't know the new monitoring tool well enough to get the right metrics quickly.

That sets the theme to why as effective engineers we should fail fast and hone our abilities to recover and respond quickly to failures.

**Another post I wrote on failing fast:**

[https://priyankvex.wordpress.com/2017/07/08/philosophy-behind-the-offensive-programming/](https://priyankvex.wordpress.com/2017/07/08/philosophy-behind-the-offensive-programming/)


<blockquote>“The best defense against major unexpected failures is to fail often.”</blockquote>


Netflix knows its way around when we talk about creating reliable systems. What engineers at Netflix have done may sound counter-intuitive, but they have made a tool called [Chaos Monkey](https://github.com/Netflix/SimianArmy/wiki/Chaos-Monkey). It randomly kills services in their own infrastructure.

It turns out that this strategy helps Netflix to increase site's reliability. Failing services during office hours when all the engineers are available, helps them perform recovery drills effectively and prepares them well enough for actual emergencies.


## 




## Why is it so important to prepare for failures?


As software engineers, our systems are bound to fail at some point and some releases certainly will have some bugs. In such scenarios, learning and investing time in the ability to recover quickly becomes a high leverage activity. It gives you the confidence to move fast with your product having peace of mind that you are ready to tackle problems if they arise.

Few reasons to invest time in recovering from failures:



	  1. Prepares the team to write scripts for success via mock drills.
	  2. Surfaces gaping holes in the systems used for monitoring and debugging.
	  3. Helps develop better tools and processes to handle emergencies.
	  4. Helps control stress and panic in the cases of actual failures.



## 




## Write your contingency plans


![what-if-800x435](https://priyankvex.files.wordpress.com/2018/04/what-if-800x435.png)


Ask yourself "what if" questions and work-through contingency plans:



	  1. What if a critical bug gets deployed with a release?
	  2. What if a user raises an urgent ticket?
	  3. What if my message broker goes down?
	  4. What if my systems face a spike in usage?

This can be applied to even more aspects of software engineering:

	  1. What if the due date for a feature gets preponed?
	  2. What if a critical team member goes sick?
	  3. What if there is a dilemma in the product plan and prioritization?



## 




## Conclusion


No matter how careful we are and what we are working on, things will go wrong some of the time.

The better our tools and processes for recovering quickly from failures, and the more we practice using them, the higher our confidence and the lower our stress levels will be. This allows us to move forward much more quickly.


# 




# That’s all, folks!



