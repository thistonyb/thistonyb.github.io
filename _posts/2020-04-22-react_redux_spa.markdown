---
layout: post
title:      "React Redux SPA"
date:       2020-04-23 02:34:07 +0000
permalink:  react_redux_spa
---


I was challenged with building a React-Redux SPA for a project. The first trial of every project for me, and I doubt I am alone, is to find a suitable idea to wrap my coding around. I began with the thought that I did not want to have an app that just took in input. I wanted something that had a little meat built into the database. So I quested for a free JSON data-set that I could seed my database with. There are a number of data catalog sites like https://cadatacatalog.state.gov/ for instance out there. Which is great, but so many of the topics are serious, like car related deaths in a given country. I did entertain the idea of making a SPA that helped the user see where Covid-19 hotspots were, but it was a little too serious for my taste and the data was rapidly changing. Luckly, I found a dataset elsewhere that was a catalogue of recipes - right up my alley, I love to cook. You might be reading this with the thought of creating your own React-Redux-Rails SPA for fun or practice. If so, I encourage you to create it around something you enjoy, it will keep you more excited about what you are building.

Off we go... I began with setting up my repository through GitKraken and up and running in Visual Studio Code. This SPA needed a front and back-end, so separate folders were created for the client and server. In the client folder you will want to create a front end pipeline and the way I did that is with the create-react-app generator. It seems like one of the best ways to get started building a SPA, and uses webpack and Babel under the hood. Also don't forget to install react-redux and add it to our dependencies for our store! For the back-end server side I used Rails to take care of my database needs. Note: I had to put a file inside my server folder because GitKraken didn't understand it was a folder for some reason...I just removed it once it figured things out. In the server terminal I got the server going by using the Rails api build: rails new server --api. This api only build is perfect for my SPA because it omits things we will never use like views. With redux we are going to render bits of components on the same page - no http requests to different views. 

Now that we have our basic structure we can set up a little bit of middleware in the back end that we will need to get things going smoothly. For instance enabling the rack-cors gem (already provided with the api build), its  just commented out in the Rails Gemfile... and adding a bit of code in config > application.rb so we won’t have any problems with cross-origin sharing between our servers.
```
config.middleware.insert_before 0, Rack::Cors do
  allow do
      origins '*'
      resource '*', headers: :any, methods: [:get, :post, :delete]
  end
end
```

Another middleware, this time in the front end, to get in place is Redux Thunk or similar, like Saga or Axios. Essentially, this middleware looks at the actions that come through your code and if it happens to be a function (not a standard action object) it will call that function. This is something we need if we are going to fetch data from a database instead of holding all of it in a Redux store’s state. You can make it part of your package.json dependencies by typing install --save thunk in your front end terminal. Oh, and just to make things easier pop into your puma.rb file in the back-end and change the port to 3001 - and make sure you subsequently fetch from that port. That way when you go to run your server with rails s, you do not have to write out rails s -p 3001. A small change, but nice when developing.

With this setup you can go do all the normal bits like set up your resources. I have a recipe and a review resource. Each recipe has many reviews and each review belongs to a recipe. I used the resource generator which will create a new Model, corresponding db table, controller and empty view folders you won’t actually use in this instance. When creating my Review resource I used recipe:resource to set up the relationship and let it automatically add a recipe id. This only sets up half the relationship, you have to go in and make sure both are showing the right relationship in the models. 
A few more bits for the front end. I did some client side routing which makes it possible for people to save URLs, send them to friends or hide components depending on what URL is used. So I installed the React Router library and put them in my dependencies using npm install --save react-router-dom.  

Okay! That was the basic setup and hopefully it can get you off and running for your own SPA. There are a few things to think about when building it out. Here are a few points I learned after building a React-Redux-Rails SPA:
Pay attention to the reducer. This is where you are going to make sure you use your handy relationships between your resources. For instance I don’t actually want my store’s state to keep the reviews. I should be getting those from the recipe - review relationship.
Use the modular capabilities of those components and keep in mind separation of concerns, they make life so much easier than jQuery methods. It is good to break things up using simple/functional components for rendering your presentational info. Keep that state usage in your containers if possible. Along the same lines, sometimes I found myself being overwhelmed by reading my Routing and following what is going to render. So for instance I can move that into its own RecipesRouter component instead of keeping it in a container if I need to.

I hope you give a React-Redux SPA a go, I am a fan!



