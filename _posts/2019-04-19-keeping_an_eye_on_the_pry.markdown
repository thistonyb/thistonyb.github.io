---
layout: post
title:      "Keeping an Eye on the Pry!"
date:       2019-04-20 00:13:00 +0000
permalink:  keeping_an_eye_on_the_pry
---

## ( And your return values.)
This is post is a bit geared towards students using the Learn.co curriculum but has some good info for any beginning Rubyist.
I thought I would write a quick blog about something that I was struggling with at the very start as a student developer. Return values and their importance. It became clear very quickly that I was getting most of my errors because I was not identifying the correct return values while writing my code. Sometimes it was something as simple as using the method .find as an iterator instead of .select. While similar in functionality, .find returns the first item for which the block is not false, and .select will return all of them as an array. A big difference…So how do I keep myself from having errors and return what I want? The best answer I found was to use Pry. Pry is a gem that will help you see your values. It was introduced early on in our curriculum, but I was feeling overwhelmed and pushed it aside for a while. What a big mistake! Use it. It will make building your Ruby code so much easier. Here is a basic tutorial.
Most Learn.co labs already have the Pry gem installed for you. You can take a peek in your Gemfile listed with the folders and files on the left of your IDE and see if it is there. If not, you can type: gem ‘pry’ in the Gemfile and then in your terminal type: bundle install.

```
# A sample Gemfile
source "https://rubygems.org"

gem 'pry'
gem 'nokogiri', '1.6'
gem 'rspec'

```
 
First type: require ‘pry’ at the top of your file.

```
require 'pry'
class Student
  attr_accessor :name, :location, :twitter, :linkedin, :github, :blog, :profile_quote, :bio, :profile_url
  @@all = []

```
 
Then type: binding.pry in the method, right beneath the code you want to evaluate (Don’t forget to save!). Everything above the binding.pry will execute (if not broken) and anything below will not. Here I placed it right in the middle of my initialize method of my Student Class.

```
#Takes in a hash argument and sets the student's attributes
#using key/value pairs. Adds student instance to Class @@all array.
  def initialize(student_hash)
    self.name = student_hash[:name]
    binding.pry
    self.location = student_hash[:location]
    self.profile_url = student_hash[:profile_url]

```
 
Now type: learn in your terminal.

```
[00:02:24] (master) oo-student-scraper-online-web-pt-031119
// ♥ learn
```
 
You will now see the colorful Pry output in our terminal, an => pointing to where we put our binding.pry, and the pry terminal prompt. So, what can we do with this?  We just need to type in a variable after the Pry prompt and Pry will show us its value! Let’s see.

```
   8: def initialize(student_hash)
     9:   self.name = student_hash[:name]
 => 10:   binding.pry
    11:   self.location = student_hash[:location]
    12:   self.profile_url = student_hash[:profile_url]
    13:   @@all.push(self)
    14: end
[1] pry(#<Student>)>
```
 
Here I typed in student_hash to see what my initialize method was taking in as an argument. And sure enough, it is a hash with student info in it! Exactly, what I wanted.

```
[1] pry(#<Student>)> student_hash
=> {:name=>"Alex Patriquin", :location=>"New York, NY"}
[2] pry(#<Student>)>
```
 
Type: exit! to get back to your regular terminal and comment out or delete the binding.pry before you continue on...  
Now you got a taste of the power of Pry, you can see how it can make your life easier by giving you values to avoid and solve errors. Happy coding!



