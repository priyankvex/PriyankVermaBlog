---
author: priyankvex
date: 2017-05-12 17:48:56+00:00
draft: false
title: 'Skiffle : Android App To Discover, Search and Explore Music - The Making'
type: post
url: /2017/05/12/skiffle-android-app-to-discover-search-and-explore-music-the-making/
---

[gallery ids="557,559,558" type="rectangular"]

This is just a log of contemplate on the challenges and learning I encountered while creating **Skiffle : Discover tracks, albums and artists.**

[Skiffle on GitHub](https://github.com/priyankvex/Skiffle-2.0)

**Skiffle **was designed with one simple motive , provide fastest way to search for music powered by the best source available. It uses Spotify API as backend.

**How this log is structured?**

The log is structured under headings. Each heading represents a certain facet of project or technology. Under each heading is the list of challenges or solution.

**Overview : **

Skiffle is an app to provide the fastest way to search for music. Powered by Spotify API, it is a great little tool to keep track of your favourite artists and tracks.

While creating it I had some clear motives:



	  1. Use RxJava
	  2. Use dependency Injection
	  3. Use Http Request Caching
	  4. Follow Clean Architecture

Thus at some places it might seem as if the implementation is an overkill, but that was the main motivation behind creating  the app.


## **Software Engineering Items : **





	  1. **Reading [Software Engineering Stackexchange](https://softwareengineering.stackexchange.com/)  : It **is a goldmine of knowledge for SE related principles like architecture and coding styles.
	  2. **Start creating your app from the data layer : **Model the data layer first. Build your app from the data layer and then upwards. It would have saved me a ton of extra work.
	  3. **Very important to keep the naming conventions and interface consistent :**
It can get confusing other wise. Keep the naming strategy of everything consistent.
Ex. AlbumList module, getAlbumList() as getter.
	  4. **Making sure that the names follow a conceptual model :**
ex. A recycler view showing a list of AlbumItem s.
It uses a callback for click named onAlbumItemClicked().
Though this is a small thing but gives a great peace of mind when coding and you expect the interface methods to be likle this.
	  5. **Local Variables are a bliss :**
Use variables in the smallest scope possible.
This will allow garbage collector to reclaim objects faster and will save your from debugging nightmares.
	  6. **Think about all the edge cases before you go coding :**
Once you start coding your brain tricks you into being lazy.
	  7. **Writing effective git commit message :**
Here you can find useful list of emojis for commit messages
[https://gist.github.com/jhermann/0206ed09b3bbcefdd691](https://gist.github.com/jhermann/0206ed09b3bbcefdd691)



## **RxJava Items : **


As they say,


<blockquote>With a hammer in hand, everything looks like a nail.</blockquote>


Same goes when you use RxJava. You want to use it for everything. It's more fun that way! :D

**1. Using for background thread offloading : **

The most trivial use of RxJava is to have it manage threads for you. I have used it extensively to offload tasks to background threads.

**2. Observable.fromCallable() for simple usages : **

I wanted to use RxJava to offload the database reading and writing to a separate thread. For this I have used Observable.fromCallable. According to the docs it said that .create() is for advanced usage. That’s why I went with this approach.

**3. RxJava 2.xx doesn’t allow nulls to be stream elements : **

You can't emit null elements in the stream. I used pseudo objects that represent null elements as a work around.

**4. Never leave the onError() method empty :**

Always put a log statement in the onError method to get the error message


## OkHttp Caching Items :


**1. Using interceptors : **

Logging interceptors are handy to monitor requests your app is making.

Caching interceptors allows adding request caching.


## Dependency Injection Items :


**1. Inject or not to inject, that is the question?**

For instance I decided not to inject Picasso instance as it already manages a singleton internally.

**2. Using Qualifiers to inject multiple instances of same type : **

I used @Qualifiers to inject multiple instances of same type. An use case I encountered was to inject two WebService clients.

**3. Regarding Singleton Scope : **

I found somewhere that dont use the @Singleton scope. Instead of that create your own custom application scope. It gives the scoping more clarity.


## MVP Items :


**1. Be ready for a class explosion : **

One thing i noticed is that, when you try to implement MVP or clean architecture in general, what you get is a class explosion. This is necessarily not a bad thing. Heard this in a fragmented podcast clean architecture episode.

**2. How to deal with MVP when using view pager?**

I ended up using fragments as views. Activity interacts with the presenter and just updates the fragments as required. And also receives callbacks from fragment events and forwards them to presenter.** **


## Android Items :


**1. Use of onAttach() in fragments : **

It is used to check the state of the container. Example when fragment is using the activity as the container then onAttach() can be used to set the communicator listener.

**2. Preventing multiple button clicks when favourite button was clicked for a track :**

I disabled it when clicked instantly, then on onNext() and onCompleted() enabled it.

**3. Creating SearchView is real pain in some part of anatomy  :**

I found that support search view and search view are having different behaviours. I ended up using support search view as it was more like it.
In future, and production apps, best approach i think would be to create your own custom search view that caters to all your needs.

**4. Search suggestions using provider :**

Use fully qualified name if using packages. Which you should be using, for search activity names that you specify in android manifest.

**5. Issue with showing data in fragments when it arrives asynchronously : **

Some times fragment was not finished inflating the views and binding when data was finished with loading. To deal with this I used callbacks and loading data completely before I set view pager.
When fragments finished inflating, they give a callback to the activity to give them the data. And as we have already loaded the data, it should not be a problem.

**6. Use StringBuilder instead of String when strings have to be altered	: **

String is immutable and each alteration creates new objects.

**7. The monster called as state management :**

Managing life cycle of fragments and activities is real pain in the ass. They are very non deterministic.
I, almost towards the completion of the development found crashes due to state issues.
To test apps, enable the don't keep activities option in development options.


## Conclusion :


Main motivation was to create something useful and learn in the process.


<blockquote>Best way to learn alchemy is to go and try - "The Alchemist"</blockquote>


In fact, follows for learning anything.

You can find the project on GitHub :

[Skiffle on GitHub](https://github.com/priyankvex/Skiffle-2.0)
