---
author: priyankvex
date: 2018-10-20 11:40:19+00:00
draft: false
title: Tackling Lost Updates Problem In Database Using Stricter Transaction  Isolation
  Level
type: post
url: /2018/10/20/tackling-lost-updates-problem-in-database-using-better-isolation-level/
categories:
- Software Engineering
tags:
- committed
- concurrency
- database
- isolation
- mysql
- postgres
- read
- repeatable read
- serializable
- transaction
---

## ![elephant-picture-gallery-wc10011059](https://priyankvex.files.wordpress.com/2018/10/elephant-picture-gallery-wc10011059.jpg)





## **
Introduction**


Databases are made for scale and are a highly concurrent system. Thus it is normal for them to expect multiple concurrent connections.

Also, in most situations, we'll want our database to be the source of truth and always contain consistent data.

There are many concurrency related phenomena that can occur in a database when multiple transactions try to access/modify the same block of data. Ex dirty reads, dirty writes etc.

One such phenomenon is the _**lost update problem**_.

Before we jump in to discuss what the lost update problem is and how we can tackle it, let's quickly brush the different isolation levels that are supported in most databases.


### 




## **Database Transaction Isolation Level**


Most databases provide the following transaction isolation levels.

**Read Committed Isolation**

The most basic level of transaction isolation is _read committed._

It makes two promises:



	  1. You'll only read data that has been committed. (no dirty reads)
	  2. You'll only overwrite the data that has been already committed.

This is the default isolation level on most databases including postgres and mysql.

In postgres, we can check the transaction isolation level using the following command:




    
    <code><span class="pln">SHOW default_transaction_isolation;</span></code>











**Snapshot Isolation or Repeatable Reads**

Here the idea is that each transaction reads from a consistent snapshot of the database.

That is, the transaction sees all the data that was committed in the database at the time the transaction started.

Databases generally implement snapshot isolation using a technique called as [MVCC](https://en.wikipedia.org/wiki/Multiversion_concurrency_control).

**
Serializable Isolation Level**

Even though snapshot isolation looks like it should suffice in resolving our concurrency perils, it doesn't protect us from problems like Phantom reads (we'll cover this in another blog post).

This is the most strict isolation level that databases provide. These are logical equivalent of as if there was no concurrency in the database and all transactions were performed sequentially one after the other.

This is generally implemented using two-phase locking.


## 




## **The Lost Update Problem**


Lost update problem occurs when multiple transactions try to touch the same rows in the database.

The lost update problem can occur if an application reads a value, modifies it and writes it back to the database. If multiple transactions are trying to do the same thing on this same row, one or more updates will be lost.

This can have serious implications depending on the type of application.

Imagine, two transactions reading the account balance, modifying it (adding $100) and committing it back. What is one of the updates for lost?

![142d943e2b6b9dbcbadc39a72a4bbd68](https://priyankvex.files.wordpress.com/2018/10/142d943e2b6b9dbcbadc39a72a4bbd68.png)


In the above figure, the counter is incremented twice but the value gets incremented by just one. An update got lost!




## **Ways To Tackle The Lost Update Problem**


In my opinion for any application, having the lost update problem is unacceptable as it can compromise the durability (updates getting lost) and consistency (updates not causing the intended effect) for the database.

There are a few ways which can be used to tackle the problem:

**1. Using SELECT FOR UPDATE:**

In this method, transactions will have to take locks on the rows that they are trying to alter when reading them.

Other transactions will have to wait for the lock to be released to acquire the lock.

Though this solves the problem, the database won't throw an error or let the user know that something wrong has happened even if the application developer forgets to acquire the lock via code.




    
    <code><span class="pln">BEGIN;
    SELECT * FROM LOG WHERE ID = 4444 FOR UPDATE;</span>
    </code>














**2. Repeatable Read Isolation Level**

One way to ensure that the lost updates don't happen at the database level is to use stricter isolation level.




    
    <code><span class="pln">SET default_transaction_isolation = "repeatable read"</span></code>














This, in my opinion, puts us in a much safer state. We can still acquire the lock to make sure that transaction doesn't try to overwrite each other's updates, but if that ever happens, the database will fail the transaction that does so.

In most of the cases, retrying the failing transaction should suffice.

Please note that stricter isolation level like Serializable will also solve the issue.


## **Conclusion**


Lost updates can happen in the databases, and depending upon the severity of the application it can have calamitous effects.

Though acquiring lock can prevent this problem but a miss in the application code can harm database's ACID guarantees.

Thus it can be a better design choice to let the database throw an error and let the application know that it's trying to overwrite an update instead of silently doing the damage.




# That’s all, folks!



