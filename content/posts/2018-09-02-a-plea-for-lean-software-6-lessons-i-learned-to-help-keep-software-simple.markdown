---
author: priyankvex
date: 2018-09-02 17:42:58+00:00
draft: false
title: 'A plea for lean software: 6 Lessons I learned to help keep software simple'
type: post
url: /2018/09/02/a-plea-for-lean-software-6-lessons-i-learned-to-help-keep-software-simple/
categories:
- Software Engineering
tags:
- '"FAT'
- (or
- '-'
- '1.'
- '10'
- '2.'
- '3.'
- '4.'
- '5.'
- '6.'
- A
- abstractions
- acceptable
- accommodate
- accurately
- add
- adding
- admiration.
- age-old
- ago.
- aids
- all
- allows
- also
- am
- an
- analytics
- and
- any
- appropriate
- architecture
- are
- armies
- as
- at
- available
- away
- baffling.
- be
- because
- become
- belief
- better
- bigger
- brain
- browsing
- built
- bulky
- But
- by
- can
- cannot
- cause
- causes
- changed
- 'changes:'
- code
- codebase
- communication
- company
- compared
- compiler
- complex.
- complexity
- components
- conceivable
- Conclusion
- confidence
- consider
- consumed
- continue
- curtail
- customers
- customized
- dashboards
- decomposed
- decomposition
- degree
- deletion
- deliberately
- deprecated
- design
- designed
- designers
- designing
- detail
- detailed
- development
- disagree
- disciplined
- discussed
- does
- doesn't
- Don't
- duplication.
- each
- either
- Enhanced
- enough
- entire
- entirety
- errors
- essential
- essentials.
- etc.
- even
- every
- expands
- experience
- exploring
- explosion
- extensibility
- extensions
- extent
- faster
- feature
- features
- fill
- Finding
- first
- flexibility
- following
- for
- foremost
- form
- found
- from
- functional
- functionality
- get
- getting
- goal
- grows
- hard
- hardware
- has
- have
- help
- hierarchy
- higher
- holds
- hope
- how
- huge.
- I
- I'll
- ideas
- if
- ignored
- important
- improve
- in
- incompatibility
- Incomprehensibility
- increase
- increased
- individual
- influenced
- insanely
- interfaces
- Internet
- into
- introduction
- irrelevant
- is
- It's
- it.
- justify
- keep
- keeping
- key
- kill
- killed
- languages
- largely
- laws
- lean
- Learned
- least
- lessons
- Let's
- lies
- like
- live
- machines
- main
- maintainability.
- Make
- Making
- me
- measured.
- memory
- methodologies
- mind
- minimizing
- modern
- modules
- Monolithic
- more
- most
- much
- must
- my
- naive
- need
- needed?
- needless
- nerve
- never
- new
- 'No'
- Not
- now
- number
- of
- 'on'
- one
- order
- original
- outset.
- over
- page
- paper
- part
- passes
- Patterns.
- people
- pinpoint
- place.
- Plea
- PM
- post
- power
- predominant.
- Preface
- prerequisite
- presented
- pressure
- pretty
- primary
- probably
- problems
- programmers
- programming
- proper
- quantity becomes
- rapidly
- reacted
- reason
- Recently
- reduce
- Reducing
- reflect
- related
- release?
- remember
- remove
- rendered
- required
- requires
- resonated
- Resources
- responses
- responsibility
- return
- root.
- run
- saw
- seem
- sell."
- sensitive
- should
- significant
- similar
- simple
- simpler
- single
- size
- slower
- small
- software
- Solution
- some
- something
- sophistication
- sparked
- specification
- standard
- started
- state
- step
- Still
- streamline
- streamlined
- Strongly
- structures
- suggested
- sure
- suspicion
- system
- systems.
- take
- taking
- teach
- team
- teams
- than
- than quality. Every
- that
- that's
- the
- their
- them.
- there
- these
- things
- this
- three
- time.
- to
- Today
- toll
- too.
- tools
- topic
- touch
- 'true'
- two
- typed
- understood
- unrecognized.
- us
- usage?
- use
- user
- versions
- very
- was
- way
- we
- were
- what
- when
- which
- while
- with
- write
- wrong.
- years
---




## ![animalli.com-animals-herbal-gazelle-jump-animal-background-picture-960x540 (1)](https://priyankvex.files.wordpress.com/2018/09/animalli-com-animals-herbal-gazelle-jump-animal-background-picture-960x540-1.jpg)





## **Preface**


Recently, I was browsing the codebase of my company and saw that it has three versions of dashboards for an analytics page in it. I am pretty sure that customers don't need that. This sparked something in my naive brain and I started exploring the internet for related ideas. That's when I found this age-old paper, [A Plea for Lean Software](https://cr.yp.to/bib/1995/wirth.pdf).

This post is largely influenced by ideas presented in the paper that resonated with me.


## **Introduction**


Size of software that we write today has is huge. Memory and resources required to run any modern software are insanely higher than compared to a similar functional software of even 10 years ago. Enhanced user experience and functionality justify the increased size but there is more to it.

All modern design patterns, code architecture etc are designed to teach us how to live with this complexity, not at if it can be killed at its root.

Following two laws very accurately reflect the state of the software:



	  1. The software expands to fill the available memory.
	  2. The software is getting slower more rapidly than the hardware is getting faster.

The way to streamline software lies in disciplined methodologies and return to the essentials.


## **Causes for "FAT Software"**


A primary cause of complexity is that the software holds way too much functionality than what is essential for its proper usage. We keep on adding new features and extensions and any incompatibility with the original system is either ignored or passes unrecognized.

When a system's power is measured by the number of features, _quantity _becomes more important than _quality. _Every new release must add features, even if it doesn't add functionality.

**1. All features, all the time**

Monolithic design of the software is one of the main causes of making software complex. Each conceivable feature is part of the system design, and over time most of them are rendered irrelevant but continue to take their toll on the system.

**2. To some, complexity is power**

I remember how my PM reacted when I suggested I'll be taking away some needless flexibility and make things standard in order to reduce complexity and increase maintainability.

People seem to consider complexity as sophistication, which is baffling. Incomprehensibility should cause suspicion, not admiration.

**3. Never enough time**

Time pressure is the foremost reason for bulky software. We never have enough time to remove deprecated features from code and to improve what we consider an acceptable solution.


## **6 Lessons to help keep software "Lean"**


1. **Strongly typed languages**

Use of strongly typed languages aids in designing a complex system in a simpler way. It lets the compiler pinpoint the errors and interfaces and abstractions can be consumed and changed with more confidence.

**2. Finding appropriate decomposition**

Systems should be decomposed into modules, modules should be decomposed into components and components should have a single responsibility. The entire system should be decomposed in a hierarchy with minimizing complexity and no code duplication.

**3. Extensibility**

Extensibility is a prerequisite to keep the system streamlined from the outset. It also allows the system to be customized to accommodate new changes and deletion of deprecated extensions.

**4. Complex software should never be built**

The belief that a complex system requires armies of designers and programmers is not true. A system that cannot be understood in its entirety, at least to a significant degree of detail by a single individual should probably never be built in first place.

**5. Communication is the key**

As the time size grows, communication problems become predominant. Complex team structures make complex software.

**6. Reducing complexity should be the goal**

Reducing the complexity and size of the software should be the goal at every step of development. In the system specification, to designing, to detailed programming - each step must deliberately kill any needless complexity in the system.


## **Conclusion**


This topic does touch a sensitive nerve of software teams. When I discussed this with my team, the responses were like "I disagree. Features are needed to sell.", "There is no need to keep software small now. We have bigger machines and better tools." etc.

I get that. I disagree to some extent too. But not because keeping the software lean is wrong, but because it is hard. Still, I hope that keeping these ideas in mind while designing a system should curtail the complexity explosion in software.


# That’s all, folks!



