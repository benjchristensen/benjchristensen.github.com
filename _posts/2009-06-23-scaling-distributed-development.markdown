---
author: benjchristensen
comments: true
date: 2009-06-23 21:19:58+00:00
layout: post
slug: scaling-distributed-development
title: Scaling Distributed Development
---

Business demand as of late and future projects on my horizon are causing me to ponder and deeply consider the staffing requirements to deliver high quality, cost effective solutions in reasonable timelines.

Over the past 7 years I have had very hands on experience with distributed development - working from the US with over 100 people in development, QA, operations and other teams in Karachi, Pakistan. It has included two personal trips to Pakistan, thousands of hours of MSN or Skype chatting and many odd working hours in order to accommodate a 12 hour time zone difference.

[caption id="attachment_105" align="aligncenter" width="300" caption="June 2006 trip to Karachi, Pakistan"]![IMG_2348](http://benjchristensen.files.wordpress.com/2009/06/img_2348.jpg?w=300)[/caption]

All in all it has been a fruitful experience. It has definitely had its troubles, pains and inefficiencies, but products and services have been delivered cost effectively to our customers ranging from Fortune 100 on down. Applications have been built which support 10s of millions of dollars in revenue and millions of transactions per day.

In the past year however I have begun to see a different set of challenges emerge -- the ability to scale.

By scale I mean 2 types of scale:

1) Scaling the size of the team.

By this I simply mean adding more people to the team in Karachi to accommodate increasing work load.

2) Scaling the size and complexity of projects, code bases and system architecture.

This refers to the ever increasing amount of code, projects and modules to manage and develop as years of projects become legacy or enter "operational support" status, as increased business success and growth demands more from its systems and feature sets become increasingly larger and as architectures require more advanced models such as SOA, distributed computing, distributed infrastructures etc to handle scale, volume and global distribution of business.

In short, recent experience is leading me to believe that a ratio of approximately 1:5 is the maximum scale that can be achieved in a distributed development model. 1 "local" senior developer to 5 "remote" junior/intermediate developers.

**Successful Experience**

A team of 5-10 junior/intermediate developers and QA working with leadership from 12 time zones away proved to work well when the following conditions were met:

- The Karachi team worked their nights to accommodate the business and customer schedule which was US Pacific time zone.

- Daily interaction between myself and the Karachi team accounting to several hours a day of direct real-time communication on design, planning, business, and code related subjects.

- Micro-level involvement of myself at the code and task levels involving review of virtually every line of code written, every test, every deliverable.

Three successes came out of the 2+ years of this type of model:

1) Successful and cost effective delivery of the projects.

2) Mentoring, training and grooming of junior developers into what eventually became the best developer talent pool of the company in later years.

One member of that original team in particular, after 3+ years of 10-12 hour work days, all night shift, has immigrated to the US and works as one of our key resources in the role of Application Architect. He had the raw materials, personal drive and competency, but the opportunity to progress from a fresh graduate to "senior" level skills and roles in a matter of years was obviously accelerated greatly by the virtually non-stop direct contact with a senior developer, high-profile projects and US customers.

3) Proof that the distributed development model can work (under certain conditions at least).

**What a Junior Developer Needs**

I have come to the conclusion that a junior or intermediate developer needs quick and constant communication with their [lead](http://benjchristensen.wordpress.com/2009/06/23/definition-of-a-tech-lead/) -- whatever we call that person (senior developer, architect, development manager etc).

The lead must be capable of providing timely and thorough responses, training, mentoring and guidance.

Nothing can replace working in the code together, explaining why decisions are made, how to refactor something, how to add a feature to an existing codebase, how to profile, tune, optimize, debug, test and deploy.

Generally a young developer has little to no experience with "production" - what it really means to build and deliver a system that can be deployed and operate 24/7 -- by itself with little to no involvement from developers -- or even more difficult, be handed off to an operations team for deployment and operations with no direct involvement of the development team.

The concepts of logging, configuration, performance, multi-threading, system interaction, hardware and infrastructure are all simple in dev. Until one has experienced true production, and more importantly -- issues in production, it's difficult to understand why certain design decisions are made which seem to not be that important in dev, but make a significant impact in production, or to the teams maintaining production, or to the teams maintaining the code a year later.

Raw intelligence and capability exists in many people in many locations, but the proximity and availability of skilled, experienced senior personnel is key to maturing the raw skills of the young inexperienced developers into productive "seasoned" developers

No different than how a fresh graduate from a college in the US is of limited value until several years of grooming and experience under senior guidance, a developer working remotely has the same challenges -- but with some further hurdles:

- Language barriers: Educated in english does not equate to fluent or comfortable.

- Time differences: If 2 people are 12 hours apart, that means that unless they purposefully shift their schedules, they only have a short window of time early morning and late night to work together.

- Physical separation: Can't just walk around the corner to ask a quick question and can't easily judge the emotions of the person you're working with.

- Cultural separation: Many things in North America and Europe are taken for granted, such as purchasing a product on Amazon.com and having it show up at your door 2 days later. If someone has never experienced this it's much more difficult to relate to a US business requirement when they say "the user experience should be like Amazon.com".

The concept of "common sense" is not universal - it applies to experiences gained in relation to when, where and how one has lived.

**How I've Countered the Hurdles**

_Language_

I have found that rarely is verbal communication a good thing, even when it appears that it's going well.

"Yes, I understand" is not a trust worthy statement in many cases - written or verbal - but specifically in verbal with developers whose English is a 2nd or 3rd language primarily learned through school, textbooks and the internet.

Reading and writing on the other hand can generally have very high comprehension and actually be much faster.

Using something like a Skype chat (text not verbal) allows for a number of positive things:

- built in meeting notes that can be referred back to

- dialect and speed of talking do not impair comprehension, as everyone can read and re-read if necessary what has been written

- appropriate time to think (and translate thoughts to English if needed) is built in to the medium

- multiple conversations can be had in multiple windows at a time if needed

_Time Difference_

On the projects where I have been most successful, I eliminated the time difference barrier by having the Karachi team work US hours to align with our customers and US business.

This solved 2 critical issues:

- The team in Karachi could now participate in business and customer interaction and communicate directly with customers via phone calls, conference calls, Skype or MSN chats - instead of everything being done in emails with 12 hour intervals or routed back and forth through a single US contact

- The US team and Karachi team worked together as a true team with direct real-time communication all day. The Skype/MSN window became the office, talking almost as naturally via text as if we were next door.

_Physical Separation_

This is obviously the most difficult to solve, but handling the time difference by everyone working the same hours and having virtually permanent communication windows open at all times in many ways made this issue seem negligible. Yes whiteboarding is more challenging - and you all have to be fast typists, but it worked.

It did not work for all though. I had several senior US/Canadian people that didn't work out because they couldn't adjust to an environment where typing instead of talking face-to-face was the primary means of interaction and whiteboarding could not be done in an impromptu manner.

_Culture_

I have found no secret solution for this. I have had to learn to be extremely detailed in communication, take nothing for granted, think from their perspective and avoid colloquial use of the English language and all forms of sarcasm.

**Challenge to Scaling Distributed Development**

Growing a team from 5 to 15 or 20 developers, but still having a single senior developer leading them has not worked well.

Obviously the team of 20 is broken into smaller teams, and there are team leads.

The challenge is as follows:

If a "team lead" has 4-5 years of experience, and that experience itself is of only limited exposure to senior skillsets, then that person is being setup to fail as they do not yet have the skills, experience, maturity or understanding to do what they are being asked to do.

This person, who may be an excellent developer on a 5 person team led by 1 senior developer - when asked to lead the development of 5 others is now put in a position where they are struggling to deliver, they are not able to learn as they once did while working just as a developer with the senior developer and the 5 below them are learning even less and the quality of code and timelines of delivery fall thru the floor.

The solution on paper is simple: "Find senior developers in Karachi to lead the team in Karachi."

In practice however this is far more difficult. Even with restricted immigration policies to US, Canada, UK and other candidate countries in recent years, senior skilled technical people seek out opportunities wherever they may be and are not generally available in Karachi by the time their skills have matured to what would be a "senior [lead](http://benjchristensen.wordpress.com/2009/06/23/definition-of-a-tech-lead/)" or "architect".

Finding and retaining what is considered a "lead", "senior developer" or "application architect" in the US is not easy or cheap anywhere - and in "outsourcing" countries challenging to the point of "it's probably not going to happen". At least not in a way that can be counted on. When it does happen it's great, but it's not something one can plan for.

**Process Doesn't Replace Skill and Experience**

I believe process and documentation is needed and has its place, especially as projects increase in size and complexity.

However, no amount of documentation and process can replace competence (see comments by [James McGovern](http://duckdown.blogspot.com/2008/04/process-as-substitute-for-competence.html) on the subject).

Junior developers do not become competent and capable through documentation and process - it comes through mentoring and experience, being groomed by those ahead of them and by applying their raw skills to educate and improve themselves.

I can be particularly verbose in writing when I want or need to be. I have written thousands of pages of documentation including hundreds of pages of visual wireframe mockups, use cases, requirements, workflow diagrams etc. The end result? Most of the people they were intended for don't understand how it all fits together, how the business use cases apply, or how the user interfaces accomplish the use cases.

It has been a frustration for that to be the base -- and I've attempted making documentation ever more detailed, having thorough review and feedback sessions and even getting to the point of spelling out exact implementation details of given requirements right down to where the code should be done in a given codebase.

Looking back over these experiences, the documentation worked very well for the few people on the team who had already worked with me for a few years and were more advanced in their skillsets and understanding. They would read the documents and question them very specifically. They would find mistakes, or complete design errors. They would find inconsistencies in use cases or workflows.

It was obvious they understood it - and contributed to improving and enabling the delivery. The other 80% of the team however had very little if anything to say.

Thus, documentation and process is important - they are tools to organize and enable large and complex systems to be built and maintained by skilled and competent people. They do not however enable just anybody with a degree in computer science to deliver.

**Conclusion**

Successful development depends on skilled, competent, experienced people taking ownership and delivering a project, product or system.

Ideally all people involved would be equally skilled and senior - but that's a rare scenario that I've never experienced.

Thus, the mixture of senior and junior needs to be right so as to enable the senior members to still be productive in accomplishing business objectives while grooming and mentoring the next generation and increasing productivity on tasks that can be done by those with less experience with guidance.

It seems that the ratio can't be much higher than about 1-to-5. The amount of time a senior developer must spend in mentoring, communicating, teaching, reviewing, and designing with the junior members, and then performing their own development, architecture and other roles limits the number of junior people a senior resource can effectively work with.

Regardless of location, whether a team be all physically together, distributed in cities across the US or distributed across 12 time zones like I've been, I believe this principle applies. Perhaps the ratio differs for different geographic placements, but in a distributed environment where one can't walk around the corner to communicate for 5 minutes on a white-board there is a definite effort and time commitment to communication that limits the scale of a development team to a ratio of senior and junior developers that if surpassed dramatically deteriorates code quality, morale and timelines.
