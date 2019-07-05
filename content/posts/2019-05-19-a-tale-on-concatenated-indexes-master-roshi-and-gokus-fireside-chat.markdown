---
author: priyankvex
date: 2019-05-19 08:46:06+00:00
draft: false
title: 'A Tale on Concatenated Indexes: Master Roshi and Goku''s fireside chat'
type: post
url: /2019/05/19/a-tale-on-concatenated-indexes-master-roshi-and-gokus-fireside-chat/
categories:
- Software Engineering
tags:
- btree
- concatenated
- databses
- db
- index
- multiu-column
- postgres
- query
---


![](https://priyankvex.files.wordpress.com/2019/05/cheetah-running.ngsversion.1396530527499.jpg)
Indexes make our queries run as fast as a cheetah!









Right Practice. Right Results



  

This post is part of newsletter that I run ["Scamming the Coding Interview"](https://scammingthecodinginterview.com), which is geared towards continuous practice on concepts to ace the engineering interviews.




[
  

Subscribe



](https://scammingthecodinginterview.com)







  






Once upon a time there was a master named Roshi whose relational database used to work like a blowing wind.







Reads used to be so fast that it reminded people of thunder strike. One day his disciple Goku got hold of him and asked, my database is smaller than yours, then why my queries are slower. What's it that you know and I don't?  
  
_To which Master Roshi replied:_







<blockquote>Databases are really good to put data, not so much when it comes to reading it back. As database sizes start to grow, and queries start to take what seems like ages, you need to harness the power of "Concatenated Indexes".
> 
> </blockquote>







When queries are slow and you see a `"SEQSCAN"` in the explain analyze, you should know what needs to be done?







<blockquote>Use the index Goku!
> 
> </blockquote>







**Concatenated indexes** gives you the power to create indexes according to the access patterns of your application. Thus it's really important that we understand the data access patterns that our application will employ to create effective concatenated indexes.







Goku was amused! He knew he needed to understand all about concatenated indexes to leverage them to its fullest.  
Goku asked the master, how does concatenated indexes work and how can I leverage them too?







# What are concatenated indexes?







_Master Roshi started sharing his wisdom acquired by maintaining large scale production databases:_







The indexes that the database automatically creates consist of single key-value pair. This is not sufficient if we need to query multiple-columns. The most common type of multi-column index is called a "Concatenated Index", which combines several keys into one by simply appending columns to one another. 







This also means that the **order of columns** in a multi-column index is really important to ensure that they are used to their fullest.







A concatenated index is just a **B-Tree index** which keeps the data in a sorted list. The database considers each column according to its position in the index definition to sort the index entries. The first column is the primary sort criteria, and only if the first column as the same value the second column is used to sort the entries and so on.







_Seeing that Goku was listening closely, Master Roshi gave an easy example:_  
  
It's same as we search for an entry in a phone book by last name and then first name.  
It should be noted that first name alone won't be useful in searching in the index, but last name alone can still give results using the index.







![](https://priyankvex.files.wordpress.com/2019/05/sketch1558208191992.png)
Manuscripts of Master Roshi: Names arranged using last name and first name index.







_Goku knew the master was on to something, so he followed up…_







# How do concatenated indexes work?







_Master Roshi continued…_







Concatenated indexes are generally implemented using a B-Tree, where key is made up of columns in order as define in the index.






    
    CREATE INDEX idx_people_names ON people (last_name, first_name);







Here's how a node in the B-Tree index looks like the postgres.





![](https://priyankvex.files.wordpress.com/2019/05/index-tuple-data1.png)
How a B-Tree index node looks like.





**IndexTupleData:** Contains pointer to either the next Node or to the data in the disk.  
**Bitmap:** Stores if any of the index attributes are Null to save sapce.  
**Value:** Contains the actual value of the column







Here's how a B-Tree index will look like for index made on last name and first name.







![](https://lh3.googleusercontent.com/0Nm1NFQovWqwQ6yvDfNQDtUYSibjcfVwCDImiiSQPNpmOjWxtqON_yDP3dfQLIN5xfmaYZfqueDQxKKaV93NuowI7eNi6LHn4E_xON_GwC1aXHkjMOiJ8pGNElApZRKdKLXUYrgX7YQ9IdzcluQOjqU7NoGw8Zs_ecX0QfWBwaYXWJEPdiaZJ2HBtDh2KYfx7A4BfDfG6Wcf30IBZ8vE_iC-8rFkEorc3vSsowRqAgqyCvRNKXK9K2nnhb0C2n2FK0OyR3uz61mXyb2Ep5vS3-qf-AQMD4vYZC5JQHTy8j11lhIeOiwy_XruRmKTR2K88WG3ByQiENPHgYsuxct7lH5xwMqmJ_h6FeiMpGyQhspSgsI7YmBf3D34A17wfdU5ywIhDLmAoAIqs1VBSRdAeERE0z2zsbHAYKzvfhEMBaAOCtdXzJxxtmGvnV6NTe4WMT1uz8_9nXENYGC9Q8FkFyStaMTqi0a2ASiYIs5jWyLyxRv5xMiC5CFl8or1zJaoUsJq2PKQJr70yXQ3DfZUuzKRKFfx_mPRVqhlTZRrMPUyOdMLx8oZ58-4kavdUUAGkQyUxFJN_nakmx-2XjqpkUL4uXcxvMXb9bNfywf1glLbvwL8whMILjD1dHfr9pCtr_o1LNwoxc8thzeVpJZdSeocl5z8D9ni=w1085-h640-no)
Master Roshi's manuscript showing the B-Tree for a last name and first name index.







_Seeing the most fruitful tree ever, Goku asked the master to help him with an example search query._







# How search queries are served using concatenated indexes:







Master Roshi continued:  
Suppose we want to search for the name John Wick in the concatenated B-Tree index, here's how the searching will proceed.





  1. We use the last name to get to the nodes that contain that last name.  2. After that first name is used to furthur find the target node.





It seems clear now, why the order of columns in the index definition is important.







# How to harness the power of concatenated indexes?







Master Roshi finally wanted to leave Goku with some more lessons to effectively employ concatenated indexes in his DB.





  1. Check which queries are frequent and take time in the database.  2. Use explain analyze to study the query plan.  3. This will help you understand the DB access patterns in your application.  4. Pay special attention to the column order when creating concatenated indexes so that they can be reused.  
In a concatenated index, the first column can be searched for using the same index, the first two columns can be searched for using the same index etc  





# Conclusion







Goku was enlightened with the new knowledge that was indexed on him. Master Roshi was happy seeing that Goku applied the principles he taught him to make his read queries blazing fast and IOPS in control.  
Goku knew that now he'll be able to handle large databases without pre-mature partitioning.





  







Right Practice. Right Results



  

This post is part of newsletter that I run ["Scamming the Coding Interview"](https://scammingthecodinginterview.com), which is geared towards continuous practice on concepts to ace the engineering interviews.




  [
  

Subscribe



](https://scammingthecodinginterview.com)





