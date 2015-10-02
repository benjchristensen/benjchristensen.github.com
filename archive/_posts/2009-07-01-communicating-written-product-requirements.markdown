---
author: benjchristensen
comments: true
date: 2009-07-01 20:37:43+00:00
layout: post
slug: communicating-written-product-requirements
title: Communicating Product Requirements
wordpress_id: 123
categories:
- Management &amp; Leadership
---

I've spent the last day considering product and/or project requirements - in particular how to document and communicate them.

A draft of a requirements document numbering in excess of 100 pages has very thoroughly covered the technical definitions of all of the various 'features' - what the system needs to contain. However, it reads like a dictionary definition and does not in any way help me understand the following:



	
  * What is the business purpose of the product?

	
  * What is the business purpose of a particular requirement?

	
  * What are the use cases that requirement must serve?

	
  * Who will use the specific requirement and for what?

	
  * How does a given requirement fit into the overall system so I know its context?

	
  * How will the product implement the feature that address the given requirement?

	
  * Where in the system architecture should the developers implement the given feature?


I became aware while reading that most of the people for whom this document exists would not have a much better understanding of what needs to be built after reading the document than from before.

During my consideration I listened to a podcast on "[requirements engineering](http://www.se-radio.net/podcast/2008-10/episode-114-christof-ebert-requirements-engineering)" that interviewed Christof Ebert.

I think the recommendations and principles are valuable regardless of what process is followed -- whether they are done upfront or at the beginning of each iteration with waterfall, agile or a mixture of both.

A few notes from the podcast:

**What Requirements Should Define**



	
  * What the Customer Needs Are

	
  * What the Product Should Do

	
  * How the Product Should Do It


**Common Requirement Problems**



	
  * Missing Requirements: Incorrect effort or tactics to seek out (elicit) all of the requirements.

	
  * Wrong Requirements: Poor capture, communication or lack of validation with stakeholders.

	
  * Changing Requirements: Requirements are never static, they always change.


**3 Levels of Requirements That Need to be Addressed**

_Market (External)_



	
  * what user or client expects

	
  * the "problem space", defining the problem and what is desired to solve it

	
  * what will make the product successful


_Product (Internal)_



	
  * what the product will do

	
  * how the product will address the market requirements

	
  * the "solution space", defining the solution that will meet the user (market) requirements

	
  * define what functionality and requirements will be made into a product


_Component (Software)_



	
  * lower level details of how to implement the requirements in software

	
  * non-functional requirements such as quality, service levels, maintainability etc

	
  * context of requirement in overall system


**What is good enough?**

Reality must be paid attention to. Generally the economics of a project can not justify the "ivory tower" of solutions for all aspects of a project.

What is good enough to serve the user - in both functional and non-functional requirements?

**What is of high priority?**

Almost always there is more work to be done than resources, so what is of priority?

What can and will be committed to for development, with what resources and by when?

What can users live without, what must they have?

**My Final Thoughts**

As I prepare to attempt a revision of the requirements I'm working on, I must remember the primary reason for the documents existence: to communicate to developers, QA, analysts and business the reason for the product, what value it's creating and what use cases it will provide functionality for.

If it doesn't leave the reader with comprehension of what they'll end up with at the end of development - at least at a 10,000 foot level - and is just a list of features with no context or purpose, then it's a failure, no matter the length or level of detail.
