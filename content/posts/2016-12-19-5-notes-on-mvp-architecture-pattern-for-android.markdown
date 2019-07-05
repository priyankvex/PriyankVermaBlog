---
author: priyankvex
date: 2016-12-19 16:31:50+00:00
draft: false
title: 5 notes on MVP architecture pattern for Android
type: post
url: /2016/12/19/5-notes-on-mvp-architecture-pattern-for-android/
tags:
- android
- android studio
- Application
- architecture
- coding
- development
- fun
- how
- Internet
- introduction
- java
- learning
- libraries
- Linux
- mobile
- MVC
- MVP
- pattern
- programming
- technology
- to
- web
---







![](https://cdn-images-1.medium.com/max/800/1*R1x_nwQcYY4GRClC1q2ehA@2x.png)






							    Image credits Macoscope





MVP (Model View and Presenter) is an architectural pattern inspired by the popular MVC pattern.




MVP addresses two main points :






	  1. Make views as dumb as possible. The dumber the better.
	  2. Make each layer loosely coupled and easily testable in isolation.



I am using MVP in one of my production project and have used in some dem0 apps. Here are my 5 notes on using MVP for android.






	  1. **Package Structure :**



Android project contains lots of code and files even for application of medium complexity. Even when not following MVP I have found that arranging the project files in such a way that files that are accessed together are put in same package is more efficient and intuitive than any other approach.




What I prefer doing is create separate package for separate verticals of the app and put all related files like activities, fragments, views, presenters, adapters etc in that package.




ex. packages like add task, view task, list task for a To-Do app.




2. **Libraries that are useful for MVP :**




In MVP you want your model and presenter to be independent of the life cycle of view. For this, you can use dependency injector library like Dagger2.




Other than that, using RxJava and reactive programming principles for creating presenter is also becoming increasingly popular.




Libraries you can use for this purpose are : RxAndroid and EventBus.




3. **Managing Remote and local data sources in the Model :**




Android apps have to fetch data from the server. At the same time fetched data must be cached to make the app usable offline and increase the speed.




What I prefer doing is to create three model classes :




1. Remote Data Source




2. Local Data Source




3. Data Repository




All presenters talk to Data Repository class. Data repository model contains references to Local and Remote data repository and calls data from either according to situation.




As the name suggests Local Data Source deals with cached data and disk storage whereas Remote Data Source deals with API calls and responses.




4. **User Experience is the top priority :**




One thing that we all have to keep in mind that the real test of application is, if it is able to provide user a nice experience.




At the end of the day, user only notices the user experience of the application and not the architecture used. So if you have to make some design sacrifices to make the UX better, do it.




The real test of the machine is the satisfaction it provides to the mind. There is no other bigger test.




**5. Testing Advantages :**




Main motive behind MVP pattern was to make the testing of layers easy.




Basic idea is to keep the presenter and model android free, so that they can be tested without Android instrumentation by the JVM itself.




Views can then be tested by Android Instrumentation tests.




Mockito and Espresso can come handy for testing purposes.




**Conclusion :**




MVP, in my opinion is so far the best way to architect your android application project. It simplifies many issues like testing and making views lighter. Combine it it RxJava and dependency injection and you’ve got a nice recipe for android projects.




I am learning more about RxJava and testing frameworks will share my views on that soon.




Thanks.
