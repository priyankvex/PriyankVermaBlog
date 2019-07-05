---
author: priyankvex
date: 2018-04-29 17:01:20+00:00
draft: false
title: Devops and The Principle Of Flow
type: post
url: /2018/04/29/devops-and-the-principle-of-lean/
tags:
- (or
- (WIP)
- '10'
- '310'
- '4.'
- '40'
- A
- above
- acceptance
- According
- achieving
- activities
- added
- affecting
- after
- agile
- all
- allow
- already
- amount
- an
- and
- Another
- any
- anything
- Application
- are
- areas
- as
- at
- batch
- batches.
- be
- become
- before
- being
- better
- between
- beyond
- bigger
- board
- bouncing
- brochures
- bugs.
- Building
- business
- But
- by
- by urgent
- bypassed
- can
- cards
- case
- categories
- causes
- centers.
- 'changes:'
- channel
- codifying
- column
- coming
- common
- communication
- complete
- completed only
- completes
- component
- Conclusion
- consisting
- control
- creating
- customer
- customers
- daily
- decrease
- defects
- defining
- delay
- demands
- deploy
- deserves
- developed
- development
- DevOps
- difference
- do
- doesn't
- dominated
- done
- downstream
- dramatically
- dynamic
- each
- easy
- eliminating
- encounter
- enforcing
- ensures
- entire
- envelope
- envelopes.
- essential
- every
- example
- Explaining
- external
- Extra
- far
- fast
- fast-flow
- features
- find
- first
- flow
- flows
- fold
- folded
- folks!
- following
- for
- from
- fulfill
- functional
- furthur
- get
- gets
- given
- goal
- hardships
- have
- help
- how
- However
- I
- Ideally
- if
- implementing
- Improving
- in
- increase
- increasing
- insert
- internal
- intervals
- into
- invisible.
- is
- It's
- it.
- just
- kanban
- Kanban board.
- keep
- key
- Knaban
- large
- lead
- lean
- Let's
- levels.
- like
- Limit
- limiting
- limits
- mail
- mailing
- Make
- Making
- manual
- manufacture
- manufacturing
- material
- may
- more
- multi-tasking
- multiple
- needed?
- new
- next
- 'No'
- Non-standard
- Not
- now
- of
- off.
- 'on'
- one
- one-piece
- only
- Operations
- optimize
- other
- our
- our work
- out
- outcomes.
- over
- own
- paper
- Partially
- passed
- pay
- perform
- performing
- piece
- piled
- pioneer
- point
- possible.
- post
- Practice
- Prefer
- prevent
- preventing
- principles
- Prior
- processes.
- processing
- production
- Progress
- QA
- quality
- reaches
- reduce
- Reducing
- releases.
- reliability.
- requests
- required
- requires
- resource
- result
- revolution
- right
- Running
- same
- satisfy
- seal
- sealed.
- seconds.
- sequentially
- services
- set
- Shiego
- Shingo
- should
- side
- significant
- single
- single-piece
- size
- sizes
- skyrocketing
- small
- smooth
- So
- software
- some
- something
- soon.
- span
- speeding
- stakeholders.
- stamp
- starting
- stated
- step
- steps
- stream
- streams
- successfully
- such
- suppose
- switching
- system
- take
- takes
- task
- teams
- technology
- ten
- testing.
- than
- that
- that's
- the
- the ideal
- them.
- there
- this
- those
- three
- through
- time.
- times
- to
- toyota
- traditional
- Trello
- trouble?
- typically
- up
- us
- use
- using
- value
- visible
- visual
- waiting
- was
- 'waste:'
- wastes
- way
- we
- well
- what
- when
- where
- which
- while
- why
- will
- willing
- with
- without
- words
- work
- worst
- Yet
---

![lean-software-development-1-728](https://priyankvex.files.wordpress.com/2018/04/lean-software-development-1-728.jpg)


In the technology value stream, work typically flows from Development to Operations, steps consisting of functional areas between our business and our customers.

As stated in the lean principles developed by Toyota, we should optimize to get a single-piece fast and smooth flow for our releases.

We increase flow by:



	  1. Making work visible,
	  2. Reducing batch sizes and intervals of work
	  3. Building in the quality, preventing defects from being passed to downstream work centers.



## Why a fast flow is needed?


By speeding up the flow through the technology value stream, we reduce the lead time required to fulfill internal and external customer requests, further increasing the quality of the work while making us more agile.

Our goal is to decrease the amount of time required to deploy the changes into production and increase the reliability of those services.


## Make our work visible


![agile-pm-kanban-board](https://priyankvex.files.wordpress.com/2018/04/agile-pm-kanban-board.png)


A significant difference between manufacturing and technology value streams is that our work is invisible.

It's so easy for work to keep bouncing off between teams and yet have no visual control over it.

To prevent this and make out work more visible, we can use something like a Kanban board. (I prefer Trello for this).

Ideally, our Kanban board will span the entire value stream, defining work as completed only when it reaches the right side of the board.

Work is not done when development completes, but only when our application is running successfully in production.


## Limit Work In Progress (WIP)


In technology, our work is far more dynamic than manufacturing. Teams have to satisfy demands of multiple stakeholders. As a result daily work gets dominated by urgent requests for work coming through every communication channel possible.

We can limit multi-tasking by using Kanban board, such as by codifying and enforcing WIP limits for each column on the board.

For example, we may set a WIP limit of three cards of testing. When there are already three cards in the testing column, no new cards can be added.

Using Kanban ensures that work is visible and WIP doesn't get piled up.


## Reduce Batch Sizes


![one-piece-flow](https://priyankvex.files.wordpress.com/2018/04/one-piece-flow.png)


Another key component to creating smooth and fast-flow is performing work in small batch sizes. Prior to the lean manufacturing revolution, it was common practice to manufacture work in large batches.

However, large batch sizes result in skyrocketing levels of WIP. According to lean principles, the ideal is a single piece flow, where each batch size is of just one.

Let's take an example:

Suppose we have ten brochures to mail and mailing each one of them requires 4 steps:



	  1. fold the paper
	  2. insert the paper into the envelope
	  3. seal the envelope
	  4. stamp the envelope

Now in the traditional batch processing flow, we will perform each step sequentially for all ten envelopes.

In the lean one-piece flow, only one envelope can be at any given step. In other words, we fold the paper, insert it into the envelope, seal the envelope and stamp it before starting the next one.


## How is one-piece flow dramatically better?


In the above example, suppose each step takes 10 seconds. In batch processing, we get our first complete envelope after 310 seconds, but with the one-piece flow we get it just after 40 seconds.

Worst, what if we find that the way we have folded the paper, doesn't allow the envelope to be sealed. In which case we'll be in a bigger trouble?


## Eliminating hardships and wastes in the value stream


According to the **Toyota Production System** pioneer **Shiego Shingo**, a waste is:


<blockquote>The use of any material or resource beyond what the customer required or is willing to pay for</blockquote>


In software development value stream, a waste is anything that causes a delay for the customer, such as activities that can be bypassed without affecting the result.

The following are some common categories of waste that we encounter when implementing lean in software value stream.



	  1. Partially done work
	  2. Extra processes
	  3. Extra features
	  4. Task switching
	  5. Waiting on QA or testing or acceptance testing
	  6. Defects and bugs
	  7. Non-standard or manual work

Explaining each of the above point deserves a post of its own. Will do that soon.


## Conclusion


Improving flow through the technology value stream is essential to achieving DevOps outcomes. We do this by making work visible, limiting WIP, reducing batch sizes and eliminating wastes from our processes.

All of this will allow us to become more agile and will help in reducing lead times dramatically, and at the same time increasing the quality of releases.


# That’s all, folks!



