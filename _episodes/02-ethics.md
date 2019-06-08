---
title: "Ethics of Web Scraping"
teaching: 10
exercises: 0
questions:
- "When is it okay to web scrape?"
objectives:
- "Identify key points to being an ethical web scraper"
keypoints:
- "Rule #1: Be Polite"
---
Before we get into the hows of web scraping, we really need to cover the ethics. Hopefully our 
opening exercise uncovered some of these topics. Ethics can be its own workshop, and this workshop 
in no part constitutes legal advice, but we’ll cover the basics of being an ethical web scraper with 
a good code of conduct, which really amounts to answering the question, _“just because you can, does 
it mean you should?”_ 

# What Does the Website Owner Say?
Before using a web scraper on a website, it’s important to know if you’re allowed to by the website 
owner.  This generally involves three things: (1) looking at the terms of service/use, (2) looking 
for developer information on the website, and (3) reading the robots.txt file.  

## Terms and Conditions Apply
A Terms of Use section will state copyright and licensing terms. Who owns the content of the website, 
how can it be accessed, and what can be done with the website content. 

Terms of service are often stated when the website owner provides some type of service. Sometimes 
this service is in the form of an API, the website owner has provided a Developer Section specifically 
to define and facilitate access to their content.


## Developer Section
If there is a developer section of the website, you’re in luck. This means the website owners 
understand that people want access to their content, and usually have developed simpler ways to 
access it.  Often, this involves developer APIs, which we will define later 
_(but the topic of using APIs is beyond the scope of this lesson)_. In addition to the developer APIs, 
the website owner will have have terms of use or service, faqs, and other useful information for 
developers.


## Robots.txt
The Robots Exclusion Protocol is a standard that allows website owners to define which robots - 
web crawler, spider, web scraper - can access what content on their website. It is found on the root 
level of the website, and will be ignored if in sub-directories. While it is a de facto standard 
_(there is no official standard)_ and advisory, it is best practice to follow the protocol listed in 
the robots.txt file.  

Here are examples of robots.txt files: [Medium.com][medium-robots], [Google][google-robots], and 
the [White House][whitehouse-robots]


## DoS Attack or Bad Programming?
Have you ever been in a class or 
workshop where everyone accesses a website or webpage at the same time, 
and suddenly the site/page is slow or unresponsive? 
When a web server receives many requests at the same time, especially to the same page, 
it puts strain on the server.  This strain can result in denial of service (DoS).  

Automating web scraping is really powerful, 
but when your script is accessing a website many times per second, 
and especially if the website has limited resources, you are doing harm to the website, 
and jeopardizing access to your source of data. For this reason, 
it’s important understand what your tools are doing. 

If you are writing a scraper that will go over many pages, 
you should throttle your access.  Do this by writing a delay between page accesses, 
and limiting the time that your scraper will access the website. 


{% include links.md %}

[medium-robots]: https://medium.com/robots.txt 
[google-robots]: https://www.google.com/robots.txt 
[whitehouse-robots]: https://www.whitehouse.gov/robots.txt
