---
author: benjchristensen
comments: true
date: 2008-05-28 22:57:22+00:00
layout: post
slug: agile-versus-fixed
title: Agile versus Fixed
wordpress_id: 60
categories:
- Management &amp; Leadership
---


http://martinfowler.com/bliki/FixedPrice.html



FixedPrice agile 29 July 2003



Many people belive that you can't do a fixed price contract in an agile project. Since the whole point of an agile process is that you cannot predict the future, this isn't an unreasonable supposition. However this doesn't mean you can't come up with a fixed price agile contract, what it means is that you can't come up with a fixed price and fixed scope contract.



Usually when people say fixed price, they mean fixing price, time, and scope. This requires detailed, stable, and accurate requirements. The whole point of agile development is that it works with more fuzzy requirements. To handle this with a fixed price contract you essentially come up with a plan that says "we have $x to spend and we need a release on 1 Dec. We'll collaborate together to come up with the best set of features to go live with on that date."



The initial plan



The initial plan for this kind of arrangement is not really any different to a predictive project. The essential difference is that we don't expect things to go according to plan. Instead we expect to deliver a better product that we can currently envision, because we'll learn more about the project as the project proceeds.



Or if we find things are much tougher, we'll find that out too. In which case we'll modify the plan. If the customer doesn't like the resulting plan they can cancel. While this isn't good, they'll usually cancel earlier than they would under a predictive project, becuase predictive plans tend to discourage change, and thus make it easier to not realize when things are going off course.











http://martinfowler.com/bliki/FixedScopeMirage.html



FixedScopeMirage agile 30 September 2004



Many companies like the idea of writing a contract that fixes scope and price because they think it lowers their risk. The mirage says that their financial obligation is fixed at the price of the deal. If they don't get satisfactory software, then it won't cost them.



In my independent days, I always advised clients to avoid this mirage, it works fine in theory - but practice bites a big chunk out of its strengths.



For a start focusing only on the cost is short-changing the financial issues. You get software written because it has a business value to you - one that's greater than the cost. Otherwise why do it? If the software isn't satisfactory the financial damage isn't just limited to the what you paid for it. There is also the opportunity cost because you didn't get the business value you were expecting. The cost is also higher than people think, it's not just the money paid to contracting company, it's also the cost of people's time on the project. I remember seeing one project that went badly belly-up - the costs there were large, while the client tried to sue the contracting company for the money they'd already paid I suspect only lawyers saw any benefit.



The other thing that ruins the pretty mirage is well-known by contracting companies. A fixed scope contract only is fixed is the contractor really understands the requirements. But such knowledge is so rare that you can win by banking on its absence. Such contracting companies deliberately low-bid the fixed price, with the explicit plan of making a profit on change requests. Indeed some firms actually incentivize their sales and account managers based on how many change requests a project receives.



These are the reasons why I think fixed scope and price contracts are bad for the customer. It's why we at ThoughtWorks avoid this model as much as we can. It is possible to do a FixedPrice contract in an agile manner, but it's not wise to fix the scope.










http://martinfowler.com/bliki/ScopeLimbering.html



ScopeLimbering agile 27 October 2004



One of the basic tenets of agile development is that requirements changes aren't just expected, they are welcomed. This poses a particular challenge when an external company, like ThoughtWorks, is doing work for client. Many clients want a FixedPrice arrangement, which is really fixing scope because they see the FixedScopeMirage. But a fixed scope contract is totally at odds with agile development, so what is a company like us to do?



Over the last year or so we've been pretty successful at what I call Scope Limbering - starting with a fixed scope contract but working with the client to help them understand the way agile development works to overcome the FixedScopeMirage.



To illustrate, here's a specific example with a client that I'll call Nebbiolo. As is often the case with our work, we came in because another delivery company had failed (you'd recognize their name, but I'll spare their blushes). They'd spent a long time gathering requirements but got nowhere with development. So the client had detailed requirements which had cost a lot of time and money, and were feeling rather sore from the other firms inability to get things done. So they insisted on a fixed scope arrangement, based of course on those detailed requirements.



We took a look at those requirements and estimated it would take us about half a million dollars to build it. Like most people tackling a fixed scope project, we added a buffer - in this case quite a large buffer doubling it to a full million. This was still less than the original contracting company's estimate. (We charge much higher daily rates for our people, but since we have better and more productive people, we can actually do the job for less.)



We weren't at all shocked to discover that despite the detailed and heavily reviewed requirements, the requirements changes still came thick and fast. For each one we estimated the scope of the change and figured out how much it would cost, but didn't charge the client for the change. Slowly but steadily the changes ate up the buffer. After about six months or so the changes had used up the buffer completely. We'd been quite open with Nebbiolo during this whole time, so they weren't surprised when we told them that we couldn't afford to eat the cost of the changes any more. During that time we'd collaborated closely with Nebbiolo and they'd grown to trust us. We had no problem finding more money, indeed it took another half million to cover the requirements changes that were needed before we delivered.



At the end of all this Nebbiolo agreed that the fixed scope approach was a mirage, and we would do future projects together using a more flexible charging scheme.



I think the key to this story (and we have half a dozen similar examples) is that from the beginning we sought to put the relationship between our companies on a collaborative note rather than a confrontational note. The biggest problem with the fixed scope contract is it immediately pits the client and contractor on opposite sides where they are fighting each other about whether something is a change and who should pay for the change. An agile approach hinges upon replacing that confrontation with collaboration (customer collaboration over contract negotiation).



A tripling of actuals over initial estimates isn't unusual in our industry. Mostly I believe this isn't because we are so bad at estimating (although we aren't exactly stellar at it), but it's mainly because it's so hard to get a decent set of requirements. Many delivery companies take advantage of that by low-balling the initial bid and making profit on scope changes. But this approach sours the ongoing relationship with the client - which leads to the whole industry gaining a bad reputation. The story of Nebbiolo is one way to arrange things to keep the relationship in good shape, and I think we need more that for our whole industry.









http://martinfowler.com/bliki/SpreadingIncrementalism.html



SpreadingIncrementalism agile 5 January 2005



From time to time people question whether a particular specialty can be used incremental way: "You can't do (security | user interface design | databases | internationalization | * ) with an agile project because this aspect has to be done up front."



When a question like that's put to me, I'm immediately on a sticky wicket because I'm not that knowledgeable on that specialty. Application design is something I think I can talk about, but security (for instance) isn't - and my questioner may well be a well regarded leader in that field.



Despite my acknowledged limitations in that field, I'm not about to say that you can only use planned design in that area. What I can say is that we don't really know whether you can do incremental design in that area. I've seen enough cases where people have said "you can't use incremental design for x" only to find you can. Application design is one, database design is another. So until people try incremental design out in a serious way, I'm very reluctant to rule it out.



Part of the difficulty of assessing this question is that it's too easy to do incremental design poorly. If you do incremental design in an uncontrolled way, you are most likely to end up with a design that is a mess - to make incremental design work you need something that makes the design converge into order. In Is Design Dead I referred to these as enabling practices. For software design I labeled testing, continuous integration, and refactoring as key enabling practices to get software design to converge and avoid software entropy. When we talk about something else, like UI design, the issue is finding what those enabling practices are. They may be similar or inspired by those in software design, or they may be something different. In database design, for instance, incremental data migration is a key enabling practice. Until you find a good set of enabling practices, incremental design is thin ice.



Despite that thinness, I do think that an incremental approach is so worthwhile, that it's worth experimenting to find the right way. Phased up-front design approaches fail far too frequently - furthermore they do a poor job in the chance of volatile requirements - which I see as a unavoidable factor, at least in enterprise software development.



The biggest reason, however, that I favor incrementalism is the oldest one - risk management. Without trying out your designs, you are too vulnerable to things not working out the way you think they would, too vulnerable to schedule slippages late in development. These risks are reason enough to look for ways to introduce incrementalism into more aspects of software development.

