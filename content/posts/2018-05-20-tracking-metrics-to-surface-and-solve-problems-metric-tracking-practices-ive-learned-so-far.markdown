---
author: priyankvex
date: 2018-05-20 20:11:59+00:00
draft: false
title: 'Tracking Metrics to Surface and Solve Problems: Metric Tracking Practices
  I''ve Learned So Far'
type: post
url: /2018/05/21/tracking-metrics-to-surface-and-solve-problems-metric-tracking-practices-ive-learned-so-far/
categories:
- Software Engineering
tags:
- (or
- '1.'
- '2.'
- '3.'
- '4.'
- A
- A/B
- able
- activity
- adding
- affect
- all
- also
- an
- and
- any
- APIs
- Application
- approach
- are
- areas
- arise.
- as
- at
- automated
- available
- be
- been
- before
- built
- business
- But
- button.
- by
- can
- catch
- 'changes:'
- checklist
- checks
- citizen
- clients
- code
- coffee
- collected
- come
- communication
- Conclusion
- confidence
- configurability
- continually
- coverage
- creating
- customers
- data
- defines
- deploy
- deployment
- design
- designing
- DevOps
- directly
- disciplined
- do
- Don't
- ease
- either
- Enable
- engineer
- engineers
- enough
- equipments.
- errors
- etc.
- even
- evening
- everything.
- Examples
- extensibility
- eye
- fact
- feature
- final
- fire.
- first-class
- folks!
- following
- for
- from
- functioning
- gather
- Go
- handbook
- have
- having
- health
- Here
- high
- hit
- I
- I've
- idea.
- impacting
- impacts
- importance
- imported
- improve
- in
- include
- include CPU
- including
- industry
- infrastructure
- into
- intuitions.
- involve
- IOPS
- is
- It's
- it.
- items
- just
- keep
- key
- latency
- latent
- level
- levels.
- leverage
- life
- limited
- may
- me
- measure.
- measured.
- memory
- method
- metrics
- multiple
- must
- need
- needed?
- negatively
- nice
- Not
- number
- numbers
- occur
- of
- 'on'
- one
- ones
- only
- organization.
- our
- outages
- outcomes.
- over
- parts
- pipeline
- places.
- pleasant
- points
- problem
- problem-solving
- problems
- process
- processed
- product
- product-related
- Progress
- queries
- quickly.
- random
- rather
- realize
- really
- receiving
- relies
- rely
- remote
- resolve
- response
- result
- results
- reviewing
- right
- runs
- sales
- see
- sent
- sipping
- small
- So
- software
- solve
- spent
- spikes
- successful
- surface
- systems.
- task
- Telemetry
- test
- than
- that
- that's
- the
- these
- they
- things
- Thus
- time.
- to
- toggling
- too.
- total
- track
- tracked
- tracking
- transactions
- unexpected
- usage?
- useful
- validations
- we
- well
- what
- when
- which
- will
- with
- write
- wrong.
- you
- Your
---

It is a nice pleasant evening, you are sipping coffee and reviewing your code one final time, just so that you can gather enough confidence to hit the deploy button.

But a fact of life as a software engineer is that things can go wrong. Small changes may result in unexpected outcomes, including outages, errors or negatively impacting customers.

And when problems occur, either we can do random checks and validations that may or may not solve the problem or we can have a disciplined problem-solving approach that relies on data rather than intuitions.


# Metrics and Telemetry


To enable a disciplined problem-solving method, we need our software to track the right metrics and the right places. We need to design our systems so that they are continually creating _**telem****etry**_.


### What is Telemetry?


The DevOps handbook defines telemetry as,


<blockquote>An automated communication process by which metrics are collected at remote points and are sent over to receiving equipments.</blockquote>


When designing systems, it is a high leverage activity to include creating telemetry as a first-class citizen to enable and ease tracking metrics at all the levels needed, right from business level metrics to deployment pipeline level.


# 




# Levels Of Metrics Tracking


As engineers, the software we write impacts the organization at multiple levels, from infrastructure to the product, to business. Thus, to resolve problems quickly, we need to track metrics all these levels.

Following levels of metrics have been really useful for me to keep a checklist for adding the right metrics in the software that I write.


#### 




#### 1. Business Level Metrics:


These metrics directly affect the business. Thus are really imported to keep an eye on.

Examples include sales transactions, numbers of items clients sent, total successful items processed, hourly processing rates, etc.


#### 2. Application Level Metrics:


These metrics track the functioning of the application.

Examples include latency of the APIs, response time of queries, number of errors etc.


#### **3. Infrastructure Level Metrics:**


These metrics track the infrastructure that runs our application.

Examples include CPU usage, available memory, IOPS spikes etc.


#### 4. Product Level Metrics:


These metrics track the product progress and results. As product engineers, it's a high leverage task to track product-related metrics too.

Examples include A/B test results, feature toggling results, product progress, product extensibility, and configurability etc

By having telemetry coverage in all these areas, we will be to see the health of everything that our software relies on or things that rely on our software.


# Conclusion


With the limited time that I've spent in the software industry, I've come to realize the importance of metrics. Even the parts that don't involve any software must be tracked and measured. The key idea here is that you can not improve what you don't measure.

With right telemetry built into the software that we write, we'll be able to not only solve the problems they arise but also surface the latent ones before they catch fire.


# 




# That’s all, folks!



