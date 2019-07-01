---
layout: post
title:      "Sessions and Cookies.  No, not the chocolate chip kind.."
date:       2019-07-01 20:20:43 +0000
permalink:  sessions_and_cookies_no_not_the_chocolate_chip_kind
---


![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS3Xb6ApVwhpKLjpnRNDIbLlUXt9BQFMUk7yjwK5uw_PNGP_RAb)

Sure, at first glance we both want the kind of cookie we see in this picture but let me tell you about a very useful kind that you will appreciate more (okay, almost more) when developing a web application. Have you ever wondered how a website keeps you logged in or why when you go back to your online cart all your items you previously put in there are still waiting for you? That is all thanks to sessions and cookies. When you go to any website and enter an http address, that transaction of dialing up a specific route to a webpage is independent with no way of knowing what web page you were on before it. That is because HTTP (hyper-text-transfer-protocol) is a stateless protocol with no data persistence. So in order to track any information between the you the user, and the server hosting the web application you are interacting with, there needs to be a semi-persistant agent doing the work of keeping you logged in or your cart from losing its inventory of goods.

That is where** sessions and cookies** comes in to help when there is an exchange with your browser and the website server. Here is the break down:
* You decide to go to Amazon and find a recipe book.
* Amazon's web application receives a request when you travel to the web page and creates a cookie with info about you and sends it to your browser.
* Your browser (Chrome, Bing, Firefox, ect.) stores that session cookie.
* After that, everytime you make an http request to Amazon as you move around the site, your browser sends that cookie back the Amazon server where their web application for buying products accesses it, takes that info and updates it if need be.

So what info does that cookie contain? Well, in a hash it would persist the date it was created, the date it was set to expire, your log in info or user id, maybe some user preferences and the url of the website that created it.  This is how a website can keep track of you, your movements through it's pages, and also why you don't have to relogin every subsequent page you visit! 

Session type cookies are temporary and are stored in your browser. They expire when you leave the web applications domain or when you log out. So essentially it is there to help authenticate you as the correct user from web page to web page and access a web applications features. It also helps you get that recipe book you want to purchase from its description page into your cart. Basically, any info you want to persist inside the domain from one page to the next. 

Sessions work in concert with persistant cookies. Persistant cookies are stored on your computer, not the browser, and are generated when you create a user account for a web application. So once you signup, a cookie is made and generally persist for a  while and are only visible to that web app. Think of *sessions* as temporary cookies that allow you to move around a web site with ease and and *persistant cookies* as the means that allows you to automatically log in to a website and authenticate you as the right user (along with a few other things). That makes your time shopping for the recipe book  so much easier and a nicer experience!





