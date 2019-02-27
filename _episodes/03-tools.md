---
title: "HTTP, Browser Extensions, and APIs"
teaching: 10
exercises: 0
questions:
- "How do I web scrape?"
objectives:
- "List common methods for web scraping."
keypoints:
- "APIs can be used to obtain data instead of web scraping"
- "Different ways to web scrape directly from a web page include cut/paste from a rendered page, 
using a browser extension, and using a programming language such as Python."
---
There are several methods to web scrape. Selecting the best method depends on your project and 
workflow, and of course what tools you have access to. Two ways to access the data are directly 
through the webpage or through a developer API.

## Application Programming Interface (API)
We kept mentioning APIs, so here is where we define them and provide a little more information.
  
API stands for application programming interface.  In general, they are used to develop software 
and applications.  For our purposes, they are used by organizations to allow programmers access to 
the data. The benefits to an developer API is the organization has already established the way 
programmers can access the data by defining protocols, functions, and (usually) clear guidelines to 
using the API.  The design of each developer API will be different depending on the organization, 
but many principles and communication protocols are based on web standards. 

As implied by its name, 
you need to use programming to use an API.  Also, you might have noticed that it is referred to as a 
_developer API_.  This is because APIs are also used internally within an organization, or only with 
their business partners.  And so, the public may not have access to all APIs an organization uses. 

## Scraping from a Web Page
If you access the data through the webpage or http URL, there are three ways to capture the data:  
old-fashioned cut and paste, 
using a browser extension such as Scraper in Chrome, 
or programmatically, using python or other programming language.  The advantage to 
using a programming language, as we have previously discussed, 
is you can automate the process to do a lot of repetitive work for you.

The remainder of this lesson will be a hands-on web scraping example.


{% include links.md %}

