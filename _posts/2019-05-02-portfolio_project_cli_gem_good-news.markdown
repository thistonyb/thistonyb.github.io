---
layout: post
title:      "Portfolio Project: CLI Gem Good-News"
date:       2019-05-02 21:09:05 +0000
permalink:  portfolio_project_cli_gem_good-news
---


For our first portfolio project, my cohort and I were tasked with building  a Ruby Gem that provided a command line interface to an external data source. In this case, we were going to scrape some data from a web page and present it to the user. One requirement was to allow the user at least one choice about the data they were going to see. So at least one "level" deep.

I decided to make my Ruby gem around the user being able to access good news. When I was thinking about what I would want in a gem, I landed on the thought that if I was in the middle of a long development project and wanted a brief break, that I would want something uplifting. I searched for a news site that could provide that and found [http://goodnewsnetwork.org].  

With the website picked out it was time to begin. I took some time to inspect the webpages to get an understanding of how it was laid out.  You can do this easily on any web page by right clicking and selecting inspect or (Ctrl + Shift + I). From there you use the select element tool in the top left corner and run your cursor over the parts of the page you want to inspect.  I found that I was going to need to get topics and articles. Great! Now I knew I needed at least two objects to store that info.

With a basic idea in mind I looked up how to create a gem. Now if you have Ruby installed and it is version 1.9 or later it will have a Ruby Gems package manager included. So in my Visual Studio Code editor I created a new project and in my terminal I typed: `bundle gem good-news`. And the package manager stubbed out all the necessary folders and files for the gem.

Brilliant! Now we a place to put all our bits and pieces that will come together to make this gem. Inside gems are basically three things. The lib file where you will put the code you will write to make your gem function. Documentation on how the gem works like the ReadMe. And your Gemspec which provides info about the gem all in one spot; like who wrote it, what version, where you can find it on the web and things like that. You can find more about this at: [https://guides.rubygems.org].

My gem needed a few classes so I created files for them in the lib folder. I decided on Article, Topic, Scrapper, and CLI Classes.  The Topic Class would have the ability to store Article objects inside it, save all Topics in an array, access all Topics, and know its name and its web address. The Article Class was bare bones.  It just needed some attributes for storing its title and a web address for where it resided on the internet. Scrapper Class does just what it sounds like. It scrapes the Good News website using methods like #get_topic and #get_article that loop and save them to their corresponding objects. The CLI Class is for handling all of the user interface and calling the other classes to provide data to output to the user.

The gem bundler provides an irb and I required pry to help with testing my classes. Once they were built and working properly I moved onto filling out my ReadMe and gemspec file. Two of the most important lines in the gemspec are the executables and files: 

`spec.executables << 'good-news'

  spec.files         = ["lib/good_news.rb", "lib/good_news/version.rb", "lib/good_news/cli.rb", "lib/good_news/scraper.rb", "lib/good_news/article.rb", "lib/good_news/topic.rb", "config/environment.rb"]
`

This is because when you get everything wrapped up and it is time to create your gem the Ruby Gems package manager is going to look in your spec file to see what it needs to include. Without these properly filled out, your gem will not work...I found out the hard way!

Now we build our gem. In the terminal you type: `gem build good-news.gemspec`. 

Prior to this you must create an account at [http://rubygems.org], because it will ask for a username and password to associate your gem with its creator.

Voila! My gem was built. Now we just push it to RubyGems `gem push good-news.0.1.0.gem` and it can be used by anyone who wants to install it.

To utilize it we have a couple options. Put it in a gemfile and bundle or install and run the gem from terminal.  I just decided to install and you do that by typing: `gem install good-news`.  Once installed just type: `good-news` to get it running.

This is what you will see:
```
Welcome, it looks like you are looking for some Good News!
To see Good News topics, type 'topics'.
To quit, type 'exit'.
Please enter your choice now.
```

When you type in topics it will give you a list of 20 or so topics. You enter the number of the topic you like and it will give you a long list of articles related to that topic.  This means my program went a couple "levels" deep in allowing the user to make choices.  Now here is where there is a cool bit of functionality I incorporated thanks to a gem I found called 'launchy'. Launcy will open up your browser and send you to the webpage you tell it to go to. So, once you choose an article my gem will send you to that webpage to read it!  Much nicer than reading it in the terminal. Just type exit to stop using the gem or select another article to launch.

That is my GoodNews gem in a nutshell. I hope you go install it and try it out. 
You can also find it on GitHub at: [https://github.com/thistonyb/good-news-cli-gem.git]
























