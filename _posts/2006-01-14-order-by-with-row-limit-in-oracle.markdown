---
author: benjchristensen
comments: true
date: 2006-01-14 02:17:00+00:00
layout: post
slug: order-by-with-row-limit-in-oracle
title: Order by with Row limit in Oracle
wordpress_id: 7
categories:
- Code
---

http://www.sleberknight.com:8080/roller/page/sleberkn/20050714

-----------

select * from person where last_name = 'Smith' and rownum
When you run that query, you find much different results than you expect. This is because Oracle performs the query and applies the rownum to each row in the results before applying the order by clause. So the question is how in the world do you use Oracle's rownum in concert with an order by clause and get the correct results. I cheated. I have been using Hibernate for a while on an Oracle database and know it is able to handle this exact situation - that is, limiting the number of results and applying an order by clause to a query. So I set the hibernate.show_sql property to true and looked at what it generated for a query. It turns out to be very simple and makes use of a subselect:

select * from (
select * from person where last_name = 'Smith' order by last_name, first_name
)
where rownum
