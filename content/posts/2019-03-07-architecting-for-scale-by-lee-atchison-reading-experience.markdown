---
author: priyankvex
date: 2019-03-07 15:54:40+00:00
draft: false
title: 'Architecting for Scale by Lee Atchison: Reading Experience'
type: post
url: /2019/03/07/architecting-for-scale-by-lee-atchison-reading-experience/
categories:
- Software Engineering
tags:
- architecture
- Atchison
- Book
- design
- distributed systems
- engineering
- lee
- microservices
- scale
- services
- soa
- software
- summary
---




I recently read the book **Architecting for Scale by Lee Atchison.** The book contains a high-level overview of the major concepts that revolve around the topic of building highly-available and scalable apps.  
I felt the book to be more suited as a light read for people already familiar with these concepts rather than being an informative book for the new readers.  








![](https://www.safaribooksonline.com/library/cover/9781491943380/360h/)








The book divided into 5 parts mainly:  
1. Availability  
2. Risk Management  
3. Services and Microservices  
4. Scaling Applications  
5. Cloud Services  
  
Let's quickly summarise each part along with some good points mentioned in the book.







## **Part 1: Availability**







This part introduces to the notion of "availability" and related aspects like what causes an application to loose availability and what are the major focus areas related to availability of an application.  
  
**Availability vs Reliability:**  
Availability of a system is its ability to stay operational when it's needed to perform operations.  
Reliability of a system is its ability to perform operations has they are intended without making mistakes.  
  
**What causes poor availability?**  
The book lists some of the most common reasons which generally compromise the availability of a system:  
1. Resource exhaustion  
2. Unplanned load changes  
3. Increased number of moving parts  
4. Outside dependencies  
5. Technical debt  
  
**5 focuses on improving availability**  
The book also lists 5 best practices that we can focus on to improve the availability of a system.  
  
1. Build with failure in mind:  
Your applications will fail. Design the systems in such a way that they handle errors and are robust. A similar idea was discussed in one of my previous posts.  
  
2. Always think about scaling:  
While designing the systems always keep an eye on parts of the system that can become bottleneck with scale. Ex, will the DB be able to keep simultaneous connections, can the static content be served via a CDN to reduce the load on app servers.  
  
3. Mitigate the risk:  
There is always a risk that your system will fail in one way or the other. There is a risk of system fault, bug, corruption etc. Systems should be designed in a way that the risk is mitigated.  
A brilliant example was, say the search service of an online store  is down, one way to mitigate the damage will be to show the most popular items and a coupon code for the inconvenience rather than showing an error page to the customer.  
  
4. Monitor availability:  
Keep alerts and tracking in place to surface the problems with the app.  
  
5. Respond to availability issues in predictable ways:  
Have standard procedures (hopefully automated) , to respond to the known availability issues.  
  
The book also stresses on the point that we should always automate all the processes that touch our production systems. Manual errors are bound to happen and humans pressing the wrong button should not be the reason for your app being down.







##    
Part 2: Risk Management







This part was geared towards risks that are present in a system and ways to handle and mitigate them.  
  
**What's a risk?**  
All systems have risk in them and it's impossible to eradicate every possible risk out there.  
There is a risk that a server will crash, or database will be corrupted or the newly deployed service fail.







**Managing risk**  
1. Identify the risk:  
Identify and list all the risks and prioritise them.  
2. Remove worst offenders:  
Find the biggest risks and remove them.  
3. Mitigate:  
For the majority of the risks that you cannot remove, have a mitigation plan in place.  
4. Review regularly:  
Keep reviewing this periodically.  
  
**Classifying the risks:**  
The book suggests that the risks can be classified into following 4 groups and can be dealt with accordingly:  
1. Low likelihood, low severity.  
These can be safely ignored.  
  
2. Low likelihood, high-severity.  
Though we might never need this, but we must have a mitigation plan in place. Example, what happens if the message broker that we use crashes?  
  
3. High likelihood, low severity:  
We generally need to work on improving the likelihood of the risk here. Example, of the custom font service is down frequently, we might consider switching the CDN.  
  
4. High likelihood, high severity:  
These are the ones that must be removed from the system.   
  
**Building systems with reduces risk:**  
The book mentions few techniques that we can employ to reduce the risks in our systems.  
  
1. Redundancy:  
Design the application in such a way that we have redundancy and tasks can be retired asynchronously. Having idempotent interfaces helps in a big way here.  
  
2. Independence:  
Make sure that the components are independent from each other and there is not mutual point of failure.  
  
3. Security:  
Keep an eye on bad actors that might try to cause harm to the system. Example, DoS attack or database corruption.  
  
4. Simple:  
The more complex the system becomes, the more hidden risks it'll develop. A similar idea is discusses in one of my previous posts.  
  
5. Self-repair:  
Design systems in such a way that it can self-heal itself in case of errors. It can be as complex as having a kubernetes cluster that respwans missing pods to something as simple as a queue that keeps track of failed tasks so that they can retried automatically after some time.













## Part 3: Services and Microservices







A service is a distinct enclosed system that provides business functionality is support of building one or more larger products.  
We all start with a monolith app architecture as it's easier to get started with and also faster to move with, but with scale we might want to venture into the world of a "service based architecture"   








The book states the following **benefits that come with a "service-based architecture"**:  
  
1. Scaling decisions:  
Scaling decision for each service can be made at a more granular level.  
  
2. Team assignment and focus:  
Teams can focus on particular services and have confidence over how their changes will impact the larger system.  
  
3. Complexity localisation:   
Services can be think of as black boxes and thus complexities can be contained within them. Compartmentalising the complexity within teams that have the expertise with that service helps us manage them effectively.  
  
4. Testing:  
Each service can be effectively testing in isolation.  
  
**What should be a service?**  
Services can be slightly large units or they can be very tiny components of the system , AKA _**microservices**._  








The book points to the following guidelines for dividing the services:  
  
1. Specific business requirements  
In some cases there are very specific business requirements that dictate the service boundary. Example, compliance, payment processing, restricting access.  
  
2. Distinct and separable team ownership:  
Services can be divided to give separable, distinct and smaller ownership to specialised teams.  
  
3. Naturally separable data:  
Can a service and it's data and state be separated out from the rest of the system?    
  
4. Shared capabilities:  
Is the service being used by two or more other services?   
  
As we try to live with a service-based architecture, we also face different type of failures. The book also mentions handling service failures.  
  
**Best practices of service failures:**  
1. Have predictable response to failures:  
Instead of returning garbage responses, always return proper failure codes from the services in case of a failure.  
  
2. Fail as early as possible:  
If a service encounters an error, then we should try to fail as early as possible.  
  
3. Graceful degradation:  
If a service that we depend on fails, we should try to gracefully degrade only the part of the functionalities that depend on that failed service.  














## Part 4: Scaling Applications







**Service Tiers**  
A service tier is basically just a label that's attached to a service to indicate how critical the service is to the business operations.  
  
1. Tier 1 services:  
These are the most critical services and their failure will directly cause damage to the company.  
Example, login service, order accepting service, payment processing service.  
  
2. Tier 2 services:  
Failures of these services will degrade the user experience considerably but are less critical than the tier 1 services.  
Example, search service, live reporting service.  
  
3. Tier 3 services:  
Failures of these will cause minor or unnoticeable  impact.  
Example, recommendations service, daily newsletter service  
  
4. Tier 4 services:  
Failure of these services for a short time is often tolerable.  
Example, weekly reporting service, email marketing service.  
  
Using the service tier that we are working with we should design the responsiveness and liveliness of the service. We should also set-up and measure appropriate service level agreements for the same.  














##  Part 5: Cloud Services







This part was a very light read for someone who already has some experience working with any cloud provider.  
It gives an overview over the architecture AWS and different cloud computing options available these days like managed cloud and micro-computing like AWS Lambda.  
  








## Conclusion







Overall this was a rather light read that might help you breeze through the major concepts that are involved when designing applications for scale and will also add some terms to your vocabulary.  
This book is not a definitive guide on any of the topics and thus cannot be used for guidance on any particular implementation.







  
  




