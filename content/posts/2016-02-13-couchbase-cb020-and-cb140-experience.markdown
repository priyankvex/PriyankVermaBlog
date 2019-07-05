---
author: priyankvex
date: 2016-02-13 17:31:02+00:00
draft: false
title: 'Couchbase : CB020 and CB140 Experience'
type: post
url: /2016/02/13/couchbase-cb020-and-cb140-experience/
---

![](https://www.drupal.org/files/project-images/couchbasecicularlogoformarketing.gif)


Last week in one of my project I wanted to store data of a form having more than 100 fields. I knew storing this much scattered info on relational DBs would be tough. Platform being mobile, just made things more complicated. Indications were to use a NoSql DB.

For  what I found, Couchbase lite is the best NoSql database for mobile. It is available for both Android and ios platform and thus creating apps for both platforms becomes easy.

The usage of DB was pretty advance and thus I decided to take the courses offered by Couchbase. I took 2 courses :



	  1. **CB020 : Fundamentals of NoSql data management**
	  2. **CB140 : Couchbase lite for mobile **

**CB020 : Fundamentals of NoSql data managment**

This course was pretty basic. It covered what is big data, why scattered data can not be stored in RDBs and how NoSql is a life savior in these situations.

Most interesting concept was CAP theorem.

**C : Consistency , **

**A : Availability **

**P : Partition Tolerance**

It says that in a database you can achieve any two.

**C and P : MongoDB and Couchbase**

**C and A : MySql and Oracle**

**A and P : Apache,  HBase**



**CB140 :** **Couchbase Mobile**

This one covered basics of couchbase lite, a mobile NoSql database. Pretty simple to use.

On Android projects it can be added as gradle dependency and the APIs are also well equipped and easy to use.

Couchbase being a document based database provides a document based storage which are used to store data as JSON.

Course covered reading documents, updating and deleting documents. What is couchbase server and what is sync gateway. With code samples being presented and explained, you'll get good hold of couchbase in short period of time.

Both the ** **courses took me around 6 hours to complete and the time I'll save by not writing buggy code will be much more than this.
