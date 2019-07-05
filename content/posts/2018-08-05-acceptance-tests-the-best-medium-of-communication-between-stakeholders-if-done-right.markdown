---
author: priyankvex
date: 2018-08-05 18:41:18+00:00
draft: false
title: 'Acceptance Tests: The Best Medium of Communication Between Stakeholders (if
  done right)'
type: post
url: /2018/08/06/acceptance-tests-the-best-medium-of-communication-between-stakeholders-if-done-right/
categories:
- Software Engineering
tags:
- (or
- '1.'
- '12'
- '15.'
- '7.'
- A
- able
- about
- above
- acceptance
- access
- accordance
- add
- adopt
- after
- agile
- aiming
- all
- also
- always
- ambiguity.
- an
- and
- Another
- any
- appear
- Application
- are
- argument
- around
- as
- ask
- assigned
- associated
- assume
- at
- automated
- AWS
- back.
- backed
- backup
- be
- before
- begins.
- best
- between
- biggest
- Both
- brings
- built
- business
- business_name_date_backup.log
- But
- by
- call
- can
- Can't
- cannot
- case
- change
- check
- clear
- clearer
- code
- coding
- coffee
- Collaboration
- collaboratively.
- common
- communicate
- Communicating
- communication
- Conclusion
- confirmation
- consider
- conversation
- cool!)
- cost-effective
- could've
- course
- create
- created
- creating
- cup
- customer
- customers
- daily
- day.
- days
- decide
- define
- defining
- definition
- deliver
- details
- detected
- didn't
- different
- disagree
- disaster.
- do
- doc.
- document
- documented.
- doesn't
- Don't
- done
- drive
- drives
- each
- easy
- effective
- effectively
- effort
- eliminate
- email
- End
- ended
- engineer
- engineers
- English
- enormous
- entered
- errors
- etc.
- even
- exactly
- fairly
- fall
- feature
- few
- file
- files.
- find
- finite
- focus
- folks!
- follow
- for
- forth
- framework
- friends
- from
- fun
- funny.
- GB
- get
- Glacier.
- Go
- going
- good
- got
- grab
- great
- greet
- had
- hands
- happen
- hard
- has
- have
- having
- help
- helps
- Hey
- Hi!
- high-level
- Hmm.
- how
- I
- I'll
- I've
- idea.
- if
- Implementation
- implemented.
- important
- in
- inclination
- innocent
- inorder
- insist.
- into
- is
- issues
- It'll
- It's
- it.
- job
- just
- know
- language
- last
- late
- later?
- lead
- leads
- least
- leaves
- Let's
- like
- log
- logs
- long
- look
- looking
- lose
- lost
- Make
- 'malady:'
- manager.
- managers
- manifesto
- many
- me
- mean
- meaning.
- meant
- mid-night
- midnight
- mocking
- more
- morning
- Morty
- most
- move
- much
- my
- name
- named
- need
- needs.
- new
- nice
- night's
- 'No'
- Not
- now
- number
- objectively
- of
- off.
- office
- often.”
- Ok.
- Okay.
- older
- 'on'
- Once
- one
- only
- other
- our
- out
- overloaded
- paper
- party
- pass.
- past
- per
- perfect
- persist
- pleasant
- point
- precise
- precision
- Premature
- problem
- product
- properly.
- put
- QAs
- question
- rarely
- ready
- real
- recipe
- release?
- removed.
- request
- requirement
- Requirements
- Rick
- Robot
- room
- rule
- Running
- scale.
- see
- seeing.
- Seems
- seen
- should
- Simplest
- since
- single
- skills
- So
- Solution
- sounds
- stakeholders.
- standard
- statement.
- states
- storage
- story
- suggest?
- suite
- suits
- support.
- sure
- survive
- sync
- system
- systems.
- team
- teams
- tempted
- tend
- term
- test
- tested
- tests
- tests(or
- than
- that
- that's
- the
- their
- them.
- then
- there
- they
- things
- think
- thinking
- this
- Though
- threats
- through
- thumb
- time.
- timezone?
- to
- tone
- too.
- tools
- touch
- towards
- trap
- 'true'
- two
- unambiguous
- understands.
- until
- up
- usage?
- used
- user
- users
- UTC.
- vague
- validations
- very
- want
- wants
- was
- wastage
- wave
- way
- we
- well
- what
- what's
- when
- where
- which
- will
- with
- wordsmith
- work
- working
- works.
- worse
- worst
- worth
- would
- write
- written
- 'yes'
- you
- Your
---

![meditation-nature-sounds](https://priyankvex.files.wordpress.com/2018/08/meditation-nature-sounds.jpg)




It's a nice pleasant morning, and you have just entered the office. You greet your friends and grab a cup of coffee. You check your email and there is a new story assigned to you.

**"As a customer, I get my usage logs backed up"**

This is where is fun begins.


## Communicating Requirements


A product engineer's job is to have effective and clear communication as much as it is to write code. And one of the most common communication issues between engineers and business is communicating requirements.

You go through the requirements document and it states a vague statement.

_"Few customers want to access their last night's usage logs, our system should support that. It should backup logs daily"._

**Premature precision**

Two of the biggest threats to effective communication of requirements is aiming for premature precision and even worse having late ambiguity.

Both business and engineers are tempted to fall into the trap of premature precision. Business wants to know exactly what they want before the system is built, engineers want to know exactly what they have to deliver.

The problem is that things appear different on paper than they do on the working systems. Once the product managers see the requirements running. they have a clearer idea of what they want, and it's often not what they are seeing.

**Late Ambiguity**

Solution to premature precision is to focus on the idea validations and not on the precise details, which can lead to another malady: late ambiguity.

Often stakeholders disagree, and they tend to wordsmith their way around and no one has a precise idea about what exactly is going to be built until it is built.

Of course, it doesn't need an argument to create ambiguity. Let's look at the conversation you ended up having with your product manager.


Rick (product manager): Hey, we want the usage logs to be backed up.




Morty (engineer): Ok. how often?




Rick: Daily!




Morty: Ok, what time?




Rick: End of day works.




Morty: Got it.


Though sounds innocent, the conversation above is a recipe for disaster.

It leaves room for too much ambiguity:



	  1. We have only 1 GB of storage per customer. For how long should we persist the logs?
	  2. End of day is not a precise time, if it meant mid-night then in which timezone?
	  3. Customers will not be able to access logs until they are backed up, the time of backup needs to be in accordance to what suits customers.
	  4. How will the customers access logs?
	  5. What should the log files be named?

etc

I assume we have detected the ambiguity now. Paper requirements often don't survive the touch of the real system. As product engineers. it is our job to make sure that all the ambiguity from the requirements is removed.

It is hard, and there only one way I know how to do it.


## 




## Acceptance Tests


The term acceptance test is overloaded and since the time agile manifesto was written, it has lost its true meaning. The definition I find the best is:


<blockquote>Acceptance tests are tests written by collaboration of the stakeholders, engineers and QAs inorder to define when a requirement is done.</blockquote>


**The Definition of "DONE"**

The most important term associated with acceptance tests is the "definition of done". When do we consider a feature request to be done?

When the engineer is done coding it?

When the stakeholders have tested it?

When the user has used it?

There should be a single definition of done, _**the feature is done when the acceptance tests written for it pass.**_

That brings another very important point that teams should adopt as they scale. Acceptance tests should always be automated. There are many tools like The Robot Framework etc that helps you write acceptance tests in fairly high-level English like language.

But rarely product managers have the skills or the inclination to put so much effort into creating acceptance tests. Worst case, acceptance tests should be at least properly and objectively documented.

As effective engineers, it is our job to drive the definition of the requirements all the way to a suite of automated acceptance tests(or worst case, documented).

Let's look at a more effective communication that you could've had with your product manager.


Rick (product manager): Hi! we want the usage logs to be backed up?




Morty (engineer): Ok, how often?




Rick: Daily!




Morty: Ok. At what time?




Rick: End of day works.




Morty: That's too vague. Do you mean midnight? If yes then in which timezone?




Rick: Hmm. I didn't think of this. What do you suggest?




Morty: Simplest and the most standard way would be UTC.




Rick: Sounds good to me.




Morty: Great. Let's add a test that a new daily backup should be created at 12 midnight UTC. Also, we'll have to communicate this time to the user.




Rick: Okay.




Morty: What should be the name of the files?




Rick: I don't know. You decide that.




Morty: Okay. I'll name it business_name_date_backup.log




Rick: Okay. Let's add an acceptance test that a log file should be created daily at UTC midnight named business_name_date_backup.log too (in a tone mocking you.)




Morty: That's funny. Also, for how many past days we want to persist the logs?




Rick: What do you mean?




Morty: We have 1 GB storage per customer, we can only persist a finite number of days worth of logs.




Rick: Can't we decide this later?




Morty: No. This can change the way how the system is implemented. Let's get on a call with a few users and ask them what's the number that they are looking at.




AFTER THE CALL




Rick: Seems like they at most want the logs of past 7 days.




Morty: Okay. Let's make it 15. The system will persist logs past 15 days worth of logs.




Let's add an acceptance test that the system should be able to persist logs of past 15 days.




Rick: Okay, if you insist. What will happen to the logs older than that?




Morty: Great question. Let's move it AWS Glacier. It'll be cost-effective for the business and we'll also not lose any logs.




Rick: Okay. (Thinking what is AWS Glacier? Sounds cool!)




Morty: Great!


The above confirmation drives the vague requirements towards the clear definition of done. Acceptance tests help in defining this definition of done.




## When To Write Acceptance Tests


Implementation of a feature begins when the acceptance tests for it are ready. That should be the thumb rule for all the teams.  I've seen my team at work not follow this and it leads to enormous wastage and back and forth with each release.




## Conclusion


Communication about details is hard. It is too easy for each party to wave their hands off and assume that the other party understands. The only way I know of to effectively eliminate communication errors between engineers and stakeholders is to write acceptance tests collaboratively. They are unambiguous, and they cannot go out of sync with the application. They are the perfect requirements doc.




# That’s all, folks!



