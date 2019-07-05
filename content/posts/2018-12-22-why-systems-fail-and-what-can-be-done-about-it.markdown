---
author: priyankvex
date: 2018-12-22 15:49:35+00:00
draft: false
title: Why systems fail and what can be done about it?
type: post
url: /2018/12/22/why-systems-fail-and-what-can-be-done-about-it/
tags:
- designing
- engineering
---




![](https://priyankvex.files.wordpress.com/2018/12/69a12-stag-625B15D.jpg)








A recent team meeting at **[Squad](https://www.squadvoice.co)** touched the topic of **"system robustness"**. Clients and business operations want their systems to work, which is a very reasonable expectation. That's what we engineers are paid for after all.







Everybody gave their input over what a **_robust system_** means to them. The responses made two points very clear:  
1. There is an understanding gap in differentiating, robustness and availability of the system.  
2. People don't take the business domain into account when considering robustness and availability of the system.  
  
Out of all the responses, one response caught my attention. It was,






    
    "System should do, what it is expected to do"<br>







This sparked my interest in the topic and made me research and explore **_why systems fail and what can we do about it_**?







## **What are system failures?**







In simple language, a system failure occurs when it fails to do, what it was expected to do.







System failures are related to two properties of the system, "Availability" and "Reliability (Robustness)".







Reliability and availability are different: **Availability** is doing the right thing within the specified response time. **Reliability** is not doing the wrong thing.   







So whenever a system fault occurs, we either compromise on the availability (system didn't respond in the specified time) or robustness (system didn't do the correct thing).







The domain that the system is deployed to serve dictates how much availability and robustness is required.  
Numbers like **"99% up-time"** are often misleading.  








Availability of 99% means that the system can be **down for 1.7 hours** in any given week. How does this sound for a heart rate monitoring system in an ICU?  
Reliability of 99% means, 1 request can fail in every 100 requests. What if that 1 request is an update to a customers CRM that represented a deal size of 100000$ dollars?  
  
This shows that there must be a strong relationship between the domain in which the system is deployed and the system failures that we can afford.













## **How to design systems that are robust and available?**







Hardware failures also contribute to system failures but with managed cloud services, the mean time between failures is in decades, most of the system failures occur because of software faults. 







**Fault-tolerant execution** of the software is the key in designing systems that are robust and available.







Though I'm by no means an expert in this field, but few points that I have read and experienced may help in designing a more fault-tolerant software.  
  
**1.** **Software modularity through processes and messages:**







A key to making fault-tolerant software is to hierarchically decompose the software into modules, and modules into components. Each component is a unit of failure.   
A failure in a component should not be propagated to the other parts of the software.  
  
A design possibility is to use **_messaging_** to make components talk to each other via Kafka etc. These messages can be replayed if they are not successfully processed by the component.







**2. Design modules to be** **fail-fast and sandbox faults:**  
  
This relates to the idea of  "**[offensive programming](https://priyankvex.wordpress.com/2017/07/08/philosophy-behind-the-offensive-programming/)**".  
The modules and the components should be designed to fail-fast. Either they should function correctly or it should detect a fault and raise the signal.  
  
The key idea here is to keep the fault detection latency low.  
If a component detects a fault early, they faulty state is not shared with other components via messages etc and thus **faults are sandboxed**.  








**3. Do effective checkpointing and make actions easy to retry:**  
  
There is a hypothesis called as "**_[Heisenbug](https://en.wikipedia.org/wiki/Heisenbug)_**". It basically means that the fault-tolerance of the systems can be increased by simply retrying them one more time.  
  
Imagine a software action failed because of a rare race condition occurred or some assertion failed or out of memory error. This can also be extended to cases when a request to some external service failed because their server was busy.  
In such cases, the system can recover from the fault by simply retrying the action.  
Making software easy to retry helps deals with such "hesienbug" or and "[single event upsets](https://en.wikipedia.org/wiki/Single_event_upset)".   
  
Effective checkpointing helps in making the actions not to be retried with "amnesia".  
For example, if an action consists of two network calls and one of them failed, when the action is re-tried, we'll want the successful network request to not be repeated and be successfully checkpointed.







**4. Use transactions to maintain data integrity:**  
  
Transactions help to keep the system state stored in the database in a consistent state.   
Though transactions don't directly contribute towards system's availability or robustness, as a software fault can still occur from within a transaction and sometimes even due to a transaction.  
But they do know how to **UNDO **the changes in the state if a fault occurs.  
  
One more practical thing to do is to try coupling a DB write and a network call in a single transaction and this violates point 1, that's to keep the faults at the component level.  














## **Conclusion**







Software faults do occur and no amount of testing and QA can prevent software bugs in production environments.  
Following certain system designing techniques and proper understanding of the "availability" and  "robustness" guarantees can help us create software that is highly available and fault-tolerant and always **seem	"to do what it is expected to do"**.









