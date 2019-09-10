---
layout: post
title:      "Validations in Rails"
date:       2019-09-10 18:12:06 -0400
permalink:  validations_in_rails
---


Through ActiveRecord, Rails has bult in methods that can help us make sure that our database ends up with less erroneous data.  If you want to take a look at all the helpers provided, you can check them out [here.](https://guides.rubyonrails.org/active_record_validations.html#validation-helpers) So, why use ActiveRecord validations when many databases have validation features of their own.  The answer is simple, Rails doesn't use them. Plus, when you use ActiveRecord's data validation, it won't matter what database you choose or may move to later because your validations will still be in place.

### Relevant Info About Validations

Let's say we are have a Users model and we set up a validation to make sure a user enters their name when creating a profile.  It would look something like this:
```
class User < ActiveRecord::Base
validates :name, presence: true

end
```
We can see #validates takes in two arguements.  First is :name, as the attribute we are going to validate and the second is a hash of options. In this case, we are making sure that the attribute cannot be saved if it is empty.

Okay, so what about something a little more interesting.  How about we make sure that the name also cannot be duplicated and has to be 2 characters or longer.  We would add in...

```
class User < ActiveRecord::Base
validates :name, presence: true
validates :name, length { minimum: 2 }
validates :name, uniqueness :true
```
Pretty simple right?! The name must be present in the field when created, it has to be 2 characters long at least, and there cannot be another name exactly like it in the database.

Generally, it takes database activity to trigger a validation, like using User.new then save after or User.create because create attempts to save on its own.  There is a way to validate without any attempt at writing to the database and that is with the #valid? method.  Let's look at a way to use this method in our Users controller:

```
class UsersController < ApplicationController
     
		 def create
		   @user = User.new(user_params)
		    if @user.valid? && @user.save
				session[:user_id = @user.id
				redirect_to home_path(@user)
			else
				render :new
			end
		 end
```

Here we used a conditional to see if the new User we made is valid based on the validations we put in our User model. 
If truthy, it goes on and saves and performs the rest of the lines of code. Validations are an easy way to circumvent bad data from getting into your database. They also work hand in hand with error.messages that can be utilized to tell your user why they could not create a new user. You can check those out [here.](htthttps://guides.rubyonrails.org/active_record_validations.html#working-with-validation-errorsp://)






