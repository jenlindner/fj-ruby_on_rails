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

What is a framework?

A framework is collection of tools and settings that help you build all kinds of web applications. It is not one piece of software like Microsoft Word. Generally speaking, Word creates one thing - documents. It lets you do all kinds of things to a document, but it doesn't let you build anything but documents. You can't make games or videos or song files with Word. But A framework is like a factory for building more than one kind of thing. Your web application could serve videos or build games or let multiple people make music files together. It takes the common things you'd need to do for any kind of web application and provides simple structures for them, which you can then customize for each specific one.

Rails is an open source framework - every bit of the code that makes it 100% free - and Ruby is the language you use to customize it. Rails comes with tools for all the main jobs of creating and hosting and maintaining a database-backed web application.

There are programs written for writing software, called IDEs. You can interact with Rails through one of them, but the easiest way to get to know the basics of Rails and Ruby is to use much simpler tools. There are two main simple ways you interact with Rails: through the command line, and through the text files containing the code that makes your application do the voodoo it does. There are text applications that are built to create code documents - they can recognize code written in different languages and tell you if your code has certain kinds of errors when you save a document. 

[show what a command line looks like.] [show what sublime linter looks like.]

 There's something called Rake which is a command line tool used for administrative tasks like creating and updating your database, for example. To create a database, you type rake db:create at the command line. But Rails itself also has a set of commands to let you run your application. Rails comes with a web server, and the command to run it is simply rails serve.  

 There's another command line tool called Bundler. This is used for managing specific pieces of your application, like uploading photos or paginating content that won't fit onto one simple page. We call these specific pieces gems (loosely following the idea that Ruby is gem), and the specific ones your web application needs your gemset. Since Rails is open source, there are many people developing new and great gems all the time, and fixing whatever might be broken about them, and you really do need a tool to manage which ones belong, and even which versions get along well with each other.

 The main workflow you'll follow is to work on your own machine, and then to test it with everything it will need in the real world, and finally to publish it to the real world. But each stage has different needs. For example when you work locally, other people can't interact with your code. When you need users to test your application, you need it to be hosted where they can reach it, but you might have sensitive information you don't want shared with anyone else. You might not need the kind of power for user testing you'd need in the real world, and so your web servers and database might be less complicated and powerful. Rails manages this with  environments. You can keep all the settings that best fit each type of need in specific environment settings files - dev for local, stage for real world testing, and production for real world use.

 Next, the basic structure of a Rails app. What are all these directories?



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
