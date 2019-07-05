---
author: priyankvex
date: 2018-12-30 16:50:55+00:00
draft: false
title: Basics of Database Partitioning and Partition Strategies
type: post
url: /2018/12/30/basics-of-database-partitioning-and-partition-strategies/
categories:
- Software Engineering
tags:
- database
- db
- design
- partitioning
- scale.
- sharding
---




![](https://nails.newsela.com/s3/newsela-media/article_media/2017/09/lib-what-is-river-delta-f5e48458.jpg)








  
You are a part of a startup which has recently scaled to reach a huge number of users. This means that the increased number of users are going to generate a huge amount of data that you have to store and manage.  
  
It soon becomes evident that managing a huge dataset is a major hurdle to achieve query efficiency and it might make sense to break the database down into smaller and much more manageable chunks, just like good old low scale days. This is what database partitioning does.  
  
For very large datasets or to get very high query throughput, we often need to break the database into multiple parts. This is called **partitioning** or **sharding**.  
  








### **How partitioning works?**







Normally partitions are defined in such a way that each piece of data (record or document) belongs to exactly one partition.  
  
The criteria by which a partition is selected for a piece of data is determined by the partition strategy that is being followed. We'll go through the most common partitioning strategies that are used in the next section.  
  
In effect, each partition acts like a small database of its own, which can even be and generally is hosted on a different node. Although, the database may support queries that touch multiple partitions.  








###   
  
**Advantages of Partitioning**







The main reason for wanting to do database partitioning is **_scalability._**  
Different partitions not only provide better query performance but can also be placed on different nodes in a shared-nothing cluster.  
  
A shared nothing cluster means a cluster of nodes having a separate disk, CPU etc. This is essential in **_scaling out_** the database.







###   
**Partition Strategies**







####   
**1. Partition by key range: **  








One way to partition is to assign a continuous range of keys (from minimum to maximum) to a given node.  








For example, user events for user ids 1 to 10,000 goes to partition 1, user events of user ids 10, 001 to 20,000 goes to partition 2 and so on.  
  
**Advantage:**  
We can easily do range queries on partitions.   
As we can see, querying events for all the users from id 10 to 1000 becomes easier with key range partitioning.  
  
**Disadvantage:**  
A major disadvantage of this partitioning approach is that it can easily lead to _hot-spots,_ i.e some partitions receiving more load than others.  
Ex, if the new users generate more events, than partitions handling newer ranges of user ids will experience more load.  








####   
**2. Partition by Hash of Key **







The idea behind hash based partitioning is to partition on the hash values of the keys rather than the keys themselves.  
A good hash function will uniformly distribute the keys among all the buckets and each hash bucket can be assigned to one of the partition.  
  
**Advantage:**  
We can prevent skew and hot-spot partitions as even very similar keys now generate very different hashes which helps in uniformly distributing the load among all the partitions.  
  
**Disadvantage:**  
With hash based partitioning, we lose a very nice property of key-range partitioning: the ability to do range queries efficiently.  
As now even the adjacent keys can be placed in different partitions, range queries have to be scattered to all the partitions.  
  








###   
  
How queries are performed over partitions?







With partitions in place, the entire data-set is distributed among multiple nodes, thus there is no single database that contains all the data to serve all the queries.  
  
Systems that have partitioning in place often also host a routing tier. All the client requests go through this routing tier which determines which node should be handling this request (based on hash or key-range).  
  
For a request that cannot be served by a single partition, a scatter and gather approach is used, where the request is sent to all the partitions and the results are then merged.  
  
Request routing has many other nuances and it'll be better if we'll cover this in detail in a future post.  
  








###   
Conclusion    








As dataset starts to grow, we genreally consider splitting them into multiple parts, this is called as sharding or partitioing.  
Main advantage behind partitioning is achieve scalability.  
Majorly we rely on key-range based or hash based partitioning strategies and both have their advantages and disadvantages.  
  










