---
author: benjchristensen
comments: true
date: 2011-10-23 07:44:30+00:00
layout: post
slug: junit-tests-as-inner-classes
title: 'JUnit Tests as Inner Classes '
---

For several years on multiple Java projects I have written my unit tests as inner classes of the class they are testing. I have never liked or bought into the idea of putting unit tests in a separate class in a separate source folder. I am fine with and like having functional and/or system tests off in that separate ./test/ source folder – just not the unit tests.

Following are my reasons why I find it so much more productive and beneficial to write the unit tests as inner classes.

_Note on terminology: I will use "concrete class" to represent the class that needs to be tested._

**Low Friction**

[![](http://benjchristensen.files.wordpress.com/2011/10/jsonutilityunittests.png)](https://gist.github.com/1198069)

Unit testing should not feel like a burden, if it does many will likely not do it. Sure, developers often agree on the surface that writing unit tests is "the right thing to do", but in practice most developers don't do it. There are many reasons, but I believe one of them is that the friction for doing it is too high in most cases. Partly this is because unit tests off in another source folder have no context to the concrete class being worked on and rely upon human memory and tedious process to find, manage and keep in sync with the concrete class through the development cycle - especially when it's someone other than the original developer of the class and tests.

Putting the unit tests in an inner class greatly reduces the friction of writing and maintaining unit tests for the following reasons:



	
  * I only have to deal with a single class in my file/package/class navigator instead of two

	
  * I don't have to open and manage 2 editor windows/tabs for every class I want to edit (this is a big deal, especially when most developers have dozens of classes open at any given time)

	
  * When I use keyboard shortcuts to open that single class file, the unit tests are right there with them, I don't have to do twice the work to open first the concrete file, then the second file

	
  * I don't have to try and maintain the naming convention of 2 separate files, especially through refactorings (more on this below)

	
  * I can immediately execute the unit tests for the class I'm viewing without going off and searching for another class

	
  * All developers see the unit tests when they open the class, they don't need to remember to go looking if there happens to be one (especially in code bases where most classes don't have tests so they will almost certainly never bother to go looking after failing to find any the first several times).

	
  * Maintainability is improved because the non-original developers who open a class see the tests and are thereby reminded and encouraged to use and add to them as they edit the class


In short, unit tests as inner classes are easy to find, run, work on and maintain. This in turn encourages adoption and maintenance of them.

**Context**

Another benefit is that the unit tests as an inner class are very contextual to what they are testing. Many of the points of the previous section related to "low friction" are due to the context an inner class has with the concrete class. The tests are "in your face" and can't be missed. They are obviously intended for testing the class currently being viewed and immediately prompt the developer to use them as part of their development process.

This in turn enforces them being "unit tests" and not becoming system tests by developers starting to test multiple concrete classes from a single test class just because it's easier to keep adding tests to an existing test class than to create a new test class for every concrete class. Tests in a separate source folder have a very loose relationship to the concrete class, thus it's very easy for the context to be lost and have it start testing interaction between classes, rather than only unit testing the class it was originally intended to test.

The mental model of unit tests in an inner class is very clear – these tests are for this class and only this class.

**Encapsulation**

Unit testing should not result in the weakening of encapsulation. This easily starts to happen when the tests are in a separate class and trying to gain full access to a non-trivial concrete class to setup mocks and perform assertions.

Methods and constructors start being made public or package accessible that should have remained private just so that hooks can be provided for the test class.

Arguments are plentiful about whether private methods and inner classes should be unit tested, and in many cases the arguments are valid that only public methods should need to be tested and they will internally exercise the private members.

Unfortunately there are plenty of use cases I have come across where this ideal is not a reality on non-trivial classes due to a desire to keep things encapsulate and hide implementation details.

Here are 2 examples:



	
  * Example of 'wanting' to test privates: lots of internal logic in private methods where building the class via test-driven-development (TDD) is easier by testing the private methods as you go (like building blocks with simple progressive tests), rather than trying to write all the code then test only the public methods at the end. _(Yes, it can theoretically all be done via TDD by only going via the public method, and yes I understand the theory of it. In practice however I have found it beneficial to have some types of private methods tested so they are covered as "building blocks" rather than relying on the top level public method test failing and digging into what internal private method failed.)_

	
  * Example of 'needing' to test privates: an inner class which runs a daemon thread to perform background cache refreshes. This is something I want fully encapsulated and not exposed in any way, but I need to test that it correctly runs, does what it's supposed to do and mock it out for other unit tests.


Specifically on the second example of an inner class and background thread, these could easily be made testable by an external class by exposing things via publics or package private methods or variables, or even by pulling the inner class for the thread into a separate class – but all of those break the encapsulation I was striving for. I do not want the package structure or javadocs to know anything about the implementation details. I want it all private, not package private and certainly not public.

Thus, the only way to get access without breaking encapsulation and good object design is to put the tests inside the concrete class.

Unit tests as inner classes allow for testing without opening member variables or methods to package or public access which then leak the implementation details.

**Refactoring**

If and when the the concrete class has its name or package refactored the unit tests as an inner class just go along for the ride.

No one needs to remember to go find the associated unit tests and also rename them.

This is particularly important in large codebases maintained by many developers where the person working on the code likely is not the one who originally wrote it.

Otherwise, the unit tests becomes an orphan, in the wrong package with the wrong name. Yes, the tests likely will still work (unless they depend on package access, in which case a compilation error would have flagged it) but they are now less maintainable than ever since the naming convention that was holding them together is gone and nobody will know to go looking for it in future edits to the concrete class.

In short, when unit tests are done as an inner class, everything is fully contained and goes along for the ride regardless of where the concrete class goes or how it's named.

**Self-documenting**

When a class has all of its tests as an inner class they act as built-in documentation of what the class is supposed to do, regardless of whether the person looking for the code knows or cares to go looking for unit tests.

They can't be missed – they are staring the developer in the face at the bottom of the class and in the outline as "UnitTest" with a bunch of methods declaring the functionality that is expected.

**Arguments Against This Approach**

Unfortunately the use of inner classes for unit testing is not more common so I sometimes get opposition when I work with new teams and they see my tests as inner classes.

Here are the common questions/concerns and my perspective on them:

**What About Shipping Test Code to Production?**

The small amount of byte code that will get shipped is negligible compared to the amount of 3rd party JARs in most deployments so it hardly dents the size of WAR files being shipped around, and since the classes are never referenced or invoked in production they are never loaded into the class loaders and thus never take up permgen space on the heap.

And if there is a philosophical or actual real reason to not ship test code they can simply be stripped by a build process since they all compile to $UnitTest.class (if that naming convention is used, which I follow and recommend) and can then be easily filtered before building the JAR files.

**Apache Doesn't Do It This Way**

Or otherwise said: 'Why would you put test classes there!?'.

Apache/Maven [advocates](http://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html) having a ./src/main and ./src/test folder and they have enough clout in the industry to have made it the most known place of putting test classes.

Just because it works for them doesn't mean it's the best way of doing it and in practice I have found it to be detrimental. I agree that in a theoretical "standard directory layout" it makes sense, but in practice the lack of context, increased friction, maintainability issues and impacts on encapsulation make it less-than-ideal for the developers writing the tests.

**Summary**

Inner classes are a great home for unit tests when writing Java.

This pattern reduces friction of both writing and maintaining unit tests which in turn increases code coverage, speeds up development, improves maintainability, increases velocity and enables adopting practices such as continuous deployment.



Update (Jan 17 2012):

One drawback of unit tests as inner classes is that they show up in Javadocs. The solution is to filter them out using a custom 'Doclet' implementation.

Example can be found here: [https://gist.github.com/1410681](https://gist.github.com/1410681)
