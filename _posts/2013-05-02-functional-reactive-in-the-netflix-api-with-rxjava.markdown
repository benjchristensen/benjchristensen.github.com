---
author: benjchristensen
comments: false
date: 2013-05-02 04:08:24+00:00
layout: post
slug: functional-reactive-in-the-netflix-api-with-rxjava
title: Functional Reactive in the Netflix API with RxJava
---

Originally written for and posted on the [Netflix Tech Blog](http://techblog.netflix.com/2013/02/rxjava-netflix-api.html).
  
  





by [Ben Christensen](https://twitter.com/benjchristensen/) and [Jafar Husain](https://twitter.com/jhusain)
  




Our recent post on [optimizing the Netflix API](http://techblog.netflix.com/2013/01/optimizing-netflix-api.html)  introduced how our web service endpoints are implemented using a "functional reactive programming" (FRP) model for composition of asynchronous callbacks from our service layer. 





This post takes a closer look at how and why we use the FRP model and introduces our open source project RxJava – a Java implementation of [Rx (Reactive Extensions)](https://rx.codeplex.com).






## Embrace Concurrency






Server-side concurrency is needed to effectively reduce network chattiness. Without concurrent execution on the server, a single "heavy" client request might not be much better than many "light" requests because each network request from a device naturally executes in parallel with other network requests.  If the server-side execution of a collapsed "heavy" request does not achieve a similar level of parallel execution it may be slower than the multiple "light" requests even accounting for saved network latency.







## Futures are Expensive to Compose






[Futures](http://docs.oracle.com/javase/7/docs/api/java/util/concurrent/Future.html) are straight-forward to use for a [single level](https://gist.github.com/4670979) of asynchronous execution but they start to add non-trivial complexity when they're [nested](https://gist.github.com/4671081).







Conditional asynchronous execution flows become [difficult](https://gist.github.com/4671081#file-futuresb-java-L163) to optimally compose (particularly as latencies of each request vary at runtime) using Futures. It [can be done](http://www.amazon.com/gp/product/0321349601?ie=UTF8&tag=none0b69&linkCode=as2&camp=1789&creative=9325&creativeASIN=0321349601) of course, but it quickly becomes complicated (and thus error prone) or prematurely blocks on 'Future.get()', eliminating the benefit of asynchronous execution.









## Callbacks Have Their Own Problems






Callbacks offer a solution to the tendency to block on Future.get() by not allowing anything to block. They are naturally efficient because they execute when the response is ready.






Similar to Futures though, they are easy to use with a single level of asynchronous execution but become [unwieldy](https://gist.github.com/4677544) with nested composition.







## Reactive






Functional reactive offers efficient execution and composition by providing a collection of operators capable of filtering, selecting, transforming, combining and composing Observable's.






The Observable data type can be thought of as a "push" equivalent to [Iterable](http://docs.oracle.com/javase/7/docs/api/java/lang/Iterable.html) which is "pull". With an Iterable, the consumer pulls values from the producer and the thread blocks until those values arrive. By contrast with the Observable type, the producer pushes values to the consumer whenever values are available.  This approach is more flexible, because values can arrive synchronously or asynchronously.






The Observable type adds two missing semantics to the Gang of Four's [Observer](http://en.wikipedia.org/wiki/Observer_pattern) pattern, which are available in the Iterable type:  







  1. The ability for the producer to signal to the consumer that there is no more data available.


  2. The ability for the producer to signal to the consumer that an error has occurred.





With these two simple additions, we have unified the Iterable and Observable types. The only difference between them is the direction in which the data flows. This is very important because now any operation we perform on an Iterable, can also be performed on an Observable. Let's take a look at an example ...



[gist https://gist.github.com/4676544 /]



## Observable Service Layer






The Netflix API takes advantage of Rx by making the entire service layer asynchronous (or at least appear so) - all "service" methods return an Observable<T>.






Making all return types Observable combined with a functional programming model frees up the service layer implementation to safely use concurrency. It also enables the service layer implementation to:







  * conditionally return immediately from a cache


  * block instead of using threads if resources are constrained


  * use multiple threads


  * use non-blocking IO


  * migrate an underlying implementation from network based to in-memory cache








This can all happen without ever changing how client code interacts with or composes responses.






In short, client code treats all interactions with the API as asynchronous but the implementation chooses if something is blocking or non-blocking.






This next example code demonstrates how a service layer method can choose whether to synchronously return data from an in-memory cache or asynchronously retrieve data from a remote service and callback with the data once retrieved. In both cases the client code consumes it the same way.



[gist https://gist.github.com/4675568 /]



Retaining this level of control in the service layer is a major architectural advantage particularly for maintaining and optimizing functionality over time. Many different endpoint implementations can be coded against an Observable API and they work efficiently and correctly with the current thread or one or more worker threads backing their execution.






The following code demonstrates the consumption of an Observable API with a common Netflix use case – a grid of movies:



[gist https://gist.github.com/4679253 /]



That code is declarative and [lazy](http://en.wikipedia.org/wiki/Lazy_evaluation) as well as functionally "pure" in that no mutation of state is occurring that would cause thread-safety issues.






The API Service Layer is now free to change the behavior of the methods 'getListOfLists', 'getVideos', 'getMetadata', 'getBookmark' and 'getRating' – some blocking others non-blocking but all consumed the same way.






In the example, 'getListOfLists' pushes each 'VideoList' object via 'onNext()' and then 'getVideos()' operates on that same parent thread. The implementation of that method could however change from blocking to non-blocking and the code would not need to change.






## RxJava






RxJava is our implementation of Rx for the JVM and is available in the [Netflix repository in Github](https://github.com/Netflix/RxJava).






It is not yet feature complete with the .Net version of Rx, but what is implemented has been in use for the past year in production within the Netflix API. 






We are open sourcing the code as version 0.5 as a way to acknowledgement that it's not yet feature complete. The outstanding work is logged in the [RxJava Issues](https://github.com/Netflix/RxJava/issues?milestone=1&state=open).






Documentation is available on the [RxJava Wiki](https://github.com/Netflix/RxJava/wiki) including links to material available on the internet.






Some of the goals of RxJava are:







  * Stay close to the original Rx.Net implementation while adjusting naming conventions and idioms to Java


  * All contracts of Rx should be the same


  * Target the JVM not a language. The first languages supported (beyond Java itself) are [Groovy](https://github.com/Netflix/RxJava/tree/master/language-adaptors/rxjava-groovy), [Clojure](https://github.com/Netflix/RxJava/tree/master/language-adaptors/rxjava-clojure), [Scala](https://github.com/Netflix/RxJava/tree/master/language-adaptors/rxjava-scala) and [JRuby](https://github.com/Netflix/RxJava/tree/master/language-adaptors/rxjava-jruby). New language adapters can be [contributed](https://github.com/Netflix/RxJava/wiki/How-to-Contribute).


  * Support Java 5 (to include Android support) and higher with an eventual goal to target a build for Java 8 with its lambda support.




Here is an implementation of one of the examples above but using Clojure instead of Groovy:



[gist https://gist.github.com/4676533 /]



# Summary






Functional reactive programming with RxJava has enabled Netflix developers to leverage server-side conconcurrency without the typical thread-safety and synchronization concerns. The API service layer implementation has control over concurrency primitives, which enables us to pursue system performance improvements without fear of breaking client code.






RxJava is effective on the server for us and it spreads deeper into our code the more we use it.






We hope you find the RxJava project as useful as we have and look forward to your contributions.




