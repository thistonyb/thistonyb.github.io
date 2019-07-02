---
layout: post
title:      "Creating a Content Management System Using Sinatra"
date:       2019-07-02 20:06:00 +0000
permalink:  creating_a_content_management_system_using_sinatra
---


For my second portfolio project my cohort and I were tasked with creating a CMS in a basic web application. The app needed to use the Model-View-Controller paradigm. In our models we would have our basic logic. My model classes inherit a bunch of great CRUD functionality from ActiveRecord and set up my relationships in my Sqlite database. The views, or front end of the web application consist of HTML, a little bit of CSS, and some embedded Ruby logic. My controllers follow a simple RESTful routes design that take care of the back and forth between the users browser and the web app. And the framework I am using is Sinatra.

The instructions asked we created a content management system that tracked something important to us. It didn't take long for me to decide on what I was going to do. Ever since I was a little kid I always had a fascination with rocks and minerals. Often it was to my parent's chagrin, as their 7-year-old was walking around with loads of rocks stuffed in his pockets. So, I decided I would have my web application be a place for rock hounds to share their finds with each other. The functionality includes a way to create a new rock specimen to share, the ability to delete or edit the specimen, to view all their submitted finds, and view all the specimen submissions by all the rock hound members. The application can sign up and sign in securely with the help of a gem called *bcrypt* that salts passwords. And user is authenticated or validated for every transition so they cannot edit other members specimens.

There is a very handy gem called corneal that is a Sinatra app generator that will stub out the basic file structure and I used it to get started. In my app I used three controller classes: application controller with sessions enabled that inherits from Sinatra, and rocks and users controller that inherit from the application controller class. Each of these classes help me keep the separation of concerns design principle going by allowing each class take care of its own controller actions. (Note: In order to use multiple controller classes, make sure your config.ru file has 'use *Name*Controller' enabled along with your 'run ApplicationController'.) 

Which brings me to my models. There are two models: Rock and User with each class inheriting from ActiveRecord for CRUD functionality. The relationship I set up for my database is that Rock objects (child) will *belong to* a User and User (parent) *has many* Rocks. Then inside my db/migrate folder for the database there are two classes, CreateRocks and CreateUsers that have a table each. In the CreateUsers there is a *users* table that has the attributes of username, email, password, and password_digest (for bcrypt). In CreateRocks there is a *rocks* table, whose attributes are user_id, name, description, and location. 

The rest of the file structure includes my views folder with a couple folders inside - rocks and users. Each separating the views , whether it is to show a list of rock specimens or create a new user. And a layout file in the views folder that yields to the other views. What's left in the file structure - a config folder with my environment file; a public folder with stylesheets, any javascripts, and images; Gemfile, Rakefile, and README. 

That's about it! When thrown all together it creates a cool little web application with a CMS that creates RockHound members and allows them to create, edit, delete, and share their rock hunting finds with other rock hounds.





