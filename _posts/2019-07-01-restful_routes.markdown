---
layout: post
title:      "RESTful Routes "
date:       2019-07-02 02:10:04 +0000
permalink:  restful_routes
---

## *A pattern convention designed for easy data handling.*

I was first introduced to the term 'RESTful routes' when learning about building web applications. The term *RESTful* did not hold a great deal of insight for me so I decided to do a little digging to see what it is all about. The 'REST' in restful stands for stands for **representational state transfer** and is in essence describing the relationship between a client and a server.

 A *state transition* occurs when you move from one page to another on a website as you click a link. You move it from the state you are in to the next state in in the web app. Restful routes is used as a  design pattern to follow when mapping between HTTP verbs (get, post, put , delete, & patch) to your controller CRUD actions (create, read, update, & delete) for these state transitions. 
 
This mapping allows for both the HTTP verb and the URL together to pinpoint which webpage to transition to, instead of just the URL. This arrangement allows the same URL, when used with another verb, to render a totally different page! This gives us tidy, precise URLs.

The mapping between HTTP verbs and the CRUD actions of the controller is explained using 7 (maybe 8) route patterns. Many of these actions are implemented on the same resource.  When you go to a website, the web application receives an HTTP request from your browser.  The web app then examines the request and takes a look at the verb and URL, then it identifies the matching controller action that has the same method and URL. Once this pattern is matched the web app executes any code in the controller and sends back the appropriate response.

Lets break down the possible patterns if we were building a website to share recipes:

1. HTTP verb: GET,  ROUTE: '/recipes', Action: index, Used for: index page to display all recipes.
2. HTTP verb: GET,  ROUTE: '/recipes/new', Action: new action, Used for: display create recipe form.
3. HTTP verb: POST,  ROUTE: '/recipes', Action: create action, Used for: creates one recipe.
4. HTTP verb: GET,  ROUTE: '/recipes/:id', Action: show, Used for: displays one article based on id in URL.
5. HTTP verb: GET,  ROUTE: '/recipes/:id/edit', Action: edit, Used for: 
displays edit form based on id in URL.
6. HTTP verb: PATCH,  ROUTE: '/recipes/:id', Action: update, Used for: modifies an existing recipe based on id in URL.
7. HTTP verb: PUT,  ROUTE: '/recipes/:id/', Action: update, Used for: replaces an existing recipe based on id in URL.
8. HTTP verb: DELETE,  ROUTE: '/recipes/:id', Action: delete, Used for: deletes one recipe based on id in URL.

Note: Using Patch or Put depends on architechture preference and philisophy - either way, they provide a similar result. Patch uses the existing recipe and makes changes. Put will wipe out the old recipe and replace it with the updated material.











