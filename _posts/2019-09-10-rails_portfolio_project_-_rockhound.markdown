---
layout: post
title:      "Rails Portfolio Project - RockHound"
date:       2019-09-11 01:35:04 +0000
permalink:  rails_portfolio_project_-_rockhound
---


For my portfolio, I was tasked with creating a web application using Rails. Previously, I had created a web app using Sinatra, aka Rails lite. Now with Rails as the framework, I had access to more "magic" or increased abstraction. I decided to keep with my Sinatra project's RockHound theme and see how my project could be more DRY and fundamentally improved.

The idea behind RockHound is to provide a place for mineral hunters to log and tell others with the same interest about their specimen finds. With that it mind, I started by taking some time think about my relationships between my database objects. I will note, as a beginner that is one of the hardest parts. It is so easy to overthink them!  The reason was because I was worried that if I didn't do it correctly, it would a catastrophe later, and that isn't so far fetched. So, my advice to anyone new at creating model relationships is to try to think of how those model obects are to be used later, in as many scenarios as you can think up. I am certain figuring out relationships gets easier with practice.

I settled on having three models: a User that has many Rocks and has many Comments through Rocks; a Rock that belongs to a User and has many Comments; and Comments that belongs to Rocks and Users. Having those models figured out, I started up VS Code and installed the Rails gem and generated a new application with 'rails new rock-hound'. This set me up with my basic file structure. 

Rails is defintely a step up from Sinatra in that it has a built in server and console using the Rails CLI which is quick and easy to use. Which was helpful to get up and going fast. The first thing I tackled was setting up my database with my models and their corresponding attributes. I used the model generator to do this. It is really easy and you can even set up part of your relationships this way by typing  `rails g model Comment content:string belongs_to:user belongs_to:rock  ` which will make sure you have foreign keys. I didn't bother using the controller or resource generator. I thought drawing the routes, and setting up controllers by hand would allow me to process what I was trying to accomplish better. I think it was a good call, especially for my first Rails project.

I jumped into creating my Users and Sessions controllers to set up the basic log in process. I found this part pretty enjoyable and straightforward. My Sessions controller has login, create, facebook_create, and destroy actions. All of these revolved around logging in. Which, pretty much equates to the session[:user_id] being set with the user.id. There is one exception, I will note that using OmniAuth to log in via FaceBook was a can of worms - and based on other dev comments about it, I am not the only one who thinks so. Without having experience to compare the process to other third parties like Google, I really can't say why, but I did have to get some assistance to get FaceBook login to work properly.

The rest of the controllers were not too complicated with the exception of the Rocks controller. Since, I was using a relationship to access the comments on a particular rock, it took some figuring out. Also, in my Rock show view I nested a fields_for inside a form_for. The form_for was to create a new comment through rocks and the field_for was to create a new User if a person wanted to comment on a specimen and wasn't already signed up. This had me boggled for a bit, but in the end was a good learning experience.

Once the views were settled with their corresponding controllers, it was just about tweaking things around to get them how I wanted for the most part. I will say doing something as large as a full web app front to back is overwhelming at first. There are so many moving parts that it can flood your brain and make it a trying experience. I found that focusing on one thing - in as logical an order as I could - was necessary for me. Also, design is a must. It helped to sketch things out. Even on notepad just design your models, relationships, needed attributes, and what they need to display how you want.  I am glad I did this project. Putting all the pieces together is way different than learning about individual parts. 








