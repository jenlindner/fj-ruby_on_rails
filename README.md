For Journalism: Ruby on Rails
================

What is Ruby on Rails?
----------------------

It's kind of a funny name, but it refers to a toolset for quickly building web applications. Ruby is a general purpose scripting language and Rails is a framework written in Ruby, but Ruby on Rails generally implies a range of optional but quite preferable components. Some of them are used for tasks in your application, and some are used to make building your application easier. 


Some examples
-------------


What will be covered today
--------------------------

###Some prereqs 
 
+  Git
+  Text Editor (Sublime?)
+  Nice cup of coffee


Make an App
-----------

+ Rake, Bundler

The basic structure of a Rails app. What environments are, gems and managing them, starting the dev server. First commit.

+ Scaffold and MVC

We'll begin this section by scaffolding a model following the fields in the source data. We'll use the scaffolding to create a simple CRUD interface so we can talk about the roles and responsibilities of Models, Views, and Controllers. At the end of this section, we'll walk through the path a request makes through the app at a high level, and introduce rails concept of routing.


Rails gives you a lot of really great defaults, but we wont need a bunch of them. We'll start editing the CSS, JavaScipts and ERB Templates, so we can talk a bit about the asset pipeline. We'll also edit the routes file to lock down the app and remove unnecessary endpoints. We'll end up this section with a fully functioning election dashboard

+ Optimization
 
Rails can get pretty slow really quickly. In this section we'll walk back through out app and clean up our association calls and generally speed up database queries and view rendering. We'll look at how to profile rails actions as well. Also Rack::Cache.

+ Security and User Input
 
Rails is secure by default, but we need to be vigilant when making an app. We'll learn about common security gotchas, and how to protect against them using tools like Brakeman.

+ Testing 

+ Deploy

Finally we'll show how to deploy to an EC2 instance using Capistrano. (We should probably create a custom AMI so folks don't have to start from scratch).


Links to further reading
------------------------

[Ruby on Rails Tutorial](http://www.railstutorial.org/book)
