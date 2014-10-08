For Journalism: Ruby on Rails

Slides: http://slides.com/jenniferlindner/ruby_on_rails#/
Speaker Notes: My Notes for each Section of Class

this class is aimed at beginnners, with lots of additional resources for more serious learning. we’re not going to cover every aspect of ruby and rails, because they are huge topics, but we will go over the main important parts, and there will be exercises for getting some real world practice in. there’s a demo app you can look at for reference, too.


i’m Jennifer, i learned ruby and rails in 2007. for a year i was the sole developer maintaining a video sitelet for channel 13 in new york. i want you to introduce yourselves to each other, because we’re going to do some pair programming

get hooked up with nitrous https://www.nitrous.io/

Framework

Like the kitchen of an expert chef - it not only has every kind of tool they’d need like blenders and knives and cooking pans, and not only exactly where they expect them to be -- Julia Child’s husband had their home’s kitchen built to suit her 6’ 2” height, and it’s where they filmed the French Chef and is now part of the Smithsonian -- but also all the assistants, sous chefs and pastry chefs and preppers, with all of their well-honed craft. The chef can focus on the uniquely wonderful aspects of each dish he makes because everything that needs to be in place first is taken care of. Or surgery, with the surgeon saying clamp and getting a clamp exactly when he needs it. The framework is all of the expertise that surrounds that surgeon at that moment: anesthesiologists, nurses, heart monitors.

With Rails it’s the structure of all the directories and configuration files, and also command line tools that function like sous chefs - they do things to get your environment in place for your app to do its work. Rake for example, can create, update and destroy a database for you on command. Bundler manages your gems, which are all of your specialized assistants - things like uploading photos or paginating lists - and makes sure they get along with each other.

Tests
To continue the chef analogy, how do you know what you’ve created tastes good? And like what you intend it to? You have to taste it yourself, and have others taste it. Incidentally this is what I like best about the intent behind data journalism, both of these things are basically the scientific method in action. You need to know some things, not just believe what you’d like to about them. Your code is one of those things. 

So, here’s a definition of BDD.

"BDD is a second-generation, outside-in, pull-based, multiple-stakeholder, multiple-scale, high-automation, agile methodology. It describes a cycle of interactions with well-defined outputs, resulting in the delivery of working, tested software that matters."
--Dan North, who created the first ever BDD frameworks, including one in Ruby called RBehave, which was later integrated into the RSpec project. RSpec has been the standard for writing Ruby tests.
“That matters” is the crucial aspect of this. Your code can work, and can pass tests that confirm it works, but it needs to do what it is supposed to. A map that’s supposed to show New York sea levels can’t display a map of the Sahara. There’s a long history of miscommunication in software development, among all of the people in the process - project managers, the funders, the designers, the coders, the testers. And so BDD makes sure your code serves its purpose besides just plain working, and in the process that makes writing code a much cleaner, clearer, more focused process.

It does this in Ruby through RSpec, a framework that contains its own mocking framework that is fully integrated into the framework based upon JMock. 

Cucumber


Rails, Rake, Bundler 
These are all command line assistants to help you do specialized tasks. Rails is arguably the most powerful, because with the Rails commands you can create an entirely functional new application, and serve it. If you type `rails new meal` into a terminal where Rails is installed, Rails will build you an app named meal. If you ran the command rails generate scaffold meal ingredient:string step:text, you’d get everything the kitchen needs to create, update, and show meals. 

You can use Rails generators to create all the pieces of your app, too. We’ll get to them in detail in a bit, but you could type `rails generate model meal ingredients: string steps: text`, and now you’ve got the basic structure of your app ready to build a database around. 

What is rake? Kind of like the manager of the kitchen, making sure everything is in the state it needs to be in for your apps. You could type rake db:migrate and your kitchen will make your database with the meal table in it, and columns in that for ingredients and steps. Rails commands manage your app code, but Rake is a little more like a tool for you the developer for keeping things the way you like them. Because you can write your own rake tasks, and that’s really powerful. You could say get my kitchen ready to make tres leches cakes, or get it ready for thanksgiving for 20 people, very different types of work.


You could type rails server at this point, use a browser to go to the url localhost:3000/meals, and see a page that says Listing meals. 

And now you need some specific things for your app. Things you won’t want for every app, only this one. Rails uses Gems for this, which is a cute name but in practise managing these used to create huge amounts of pain and suffering for developers.  Now the industry standard for this is a tool called Bundler, exactly like it sounds - it bundles together the exact gems you want for this app. But it does an awful lot more than just that. It tracks and installs the exact gems that are needed. Far and away, the vast majority of problems with gems is not how they interact with your own app code, but how they interact with other gems. This is because the world of open source software can move extremely fast, and a gem you use could get updated and contain new methods at any time. Now let’s say someone likes those new methods and calls them in their gem. Let’s say you like this gem too, but when you use it, it can’t find the methods it uses in the first gem. Your version of that gem doesn’t have them yet, and now your app is just plain broken. 

You could be using hundreds of gems in your application, quite easily. So imagine the complexity of their inter-dependency. It does this with a gemfile, that lists all of your required gems and their version numbers. When it installs a required gem, it also installs all of its required gems - these are called dependencies. Your app depends on them. When it’s done installing, it creates a gemfile.lock - a snapshot of everything. When good developers confirm it’s working correctly for everything their app needs to do, they check this lockfile into their version control system -- because then they have a record of what’s required for each stage of their development. When other developers run the bundle command on this app, bundle will install whatever is in the gemfile.lock version. In this way stability is maintained for all.


MVC
So how does an app work? Model View Controller is a software paradigm that’s been around for a very long time, long before Rails. It’s a simple and powerful way of separating out the logical responsibilities of each part of an application.”Model” refers to your data, usually stored in a database, “View” handles what your users will see, and “Controllers” are the roads that connect the two. There can be lot of complexity in every main function here - databases can be millions of rows, views may need to update dynamically, controllers might need to call all kinds of other functions to help them massage the data into a format the view can work with - and it’s extremely helpful to have this structure to keep things organized.

Let’s look at Rails controllers and views first, because it’s an area where Rails really shines.

Controllers are made of actions, that Rails maps to routes and views. A meals controller can be sent the request `index` for chocolate_mousse, and it will search its actions for `index`. Finding it, it passes along the id that maps to chocolate_mousse to the action, that uses routes and views mapped to meal and index, finds what it needs, and send everything back to the browser via its render method. The render method is what Rails controllers use by default, you don’t even have to type it, so that with only a few lines of code you can interact with your meal data through your controllers. And if you want to do anything fancy, you have a great foundation in place from which to get fancier. Controller actions can call other actions, and even other actions in other controllers. You can place code that needs to be run for every action in your entire application - the kind of thing you need for security, or to control the main look and feel of the entire application - in your base controller file. And now you can update critical aspects of your entire application from one simple place. 

A Rails View is a little different from a Controller in that even though there’s a file containing view code in the same way there’s a file containing controller code, it’s not quite as simple as that. View files are wrappers around templates, and in fact their file extensions shows you this: app/views/meals/index.html.erb. The .erb is what tells Rails it can act upon the Ruby in this file, and essentially use it to manipulate the .html inside it. If view code mirrored controller code, the view file would contain only ruby and would call a template to work on and hand back to the controller, the way a controller can hand back either json or html by calling those format methods.
 
 A Rails View receives objects from a controller and contains code that decides presentation issues for those objects. For example one of the most common uses of a view is to call a partial view to handle something small and repetitive, like a list. Let’s say you have a list of meals, and you want the title of each one bolded and linked to its file. Your view might contain a loop that says for each meal, call the meal_list_item partial, and pass it the meal object that contains its title. 


ORM
Databases and applications are different beasts, and they each have their own ways of doing things, different languages and idiomatic ways of referring to what they do. Even if you knew the specific idiomatic ways of communicating complicated things to your database, writing it out in your application would be really foreign and separate from the rest of it. It would be like coming across Latin in something you’re reading, or Shakespearean English, where you can recognize words and have some idea of what phrases mean, but you have to work pretty hard for that understanding and it’s not really adding anything you couldn’t get with modern English. So we have ways of mapping that distance between them, basically phrases in modern English you can use in your application that have been translated into Latin or Shakespearean on the database side. It’s called ORM.

Object-Relational Mapping is a technique that connects the rich objects of an application to tables in a relational database management system. Using ORM, the properties and relationships of the objects in an application can be easily stored and retrieved from a database without writing SQL statements directly and with less overall database access code.

Rails Active Record contains easy ways of performing the most common tasks you’ll need to with your data. A class called meal will map to a table called meals. You’ll get optional methods for things like created_at, which you’ll need for any sorting. There’s a great API for accessing your data. So you can get things you are likely to need (like all of your meals, or the last one you used) and things in ways you are likely to need them. Find_by any column name is extremely useful when you need it. 

More powerfully, Active Record handles relationships in your data through associations. A cookbook has many meals, and meals belong to a cookbook. Both of these are associations in Rails that will handle joining your database tables together, and provide simple ways of performing operations that affect both of them. Rails has 6 main types of associations: belongs_to, has_one, has_many, has_many :through, has_one :through, and has_and_belongs_to_many.
 
If you’re going to build interesting applications in Rails, you’re quite likely going to need to know which associations will best suit your purposes. It’s really difficult to disentangle poorly associated models, and the rest of the application often has to work really hard, containing more code that subsequent developers will have to learn, to make up for the shortcoming. 

Rails provides a domain-specific language for managing a database schema called migrations. Migrations are stored in files which are executed against any database that Active Record supports using rake. Rails keeps track of which files have been committed to the database and provides rollback features. To actually create the table, you'd run rake db:migrate and to roll it back, rake db:rollback. The really powerful thing is that code is database-agnostic: it will run in MySQL, PostgreSQL, Oracle and others. 



Security 
Security is constant issue in web application development, as might be obvious by now by the regularity with which things are hacked. It’s a continually evolving set of measures against a continually evolving set of attack methods, but the good news is that Rails has updated to prevent against kinds of attacks as they became known, and for others, with some key measures in place - measures that Rails makes very easy to employ - you can protect against the majority of them. And one final thought to leave people with: WHITELIST.


Generally speaking the ways to get access to an app is to use someone else’s credentials, to try and intercept traffic between logged in users and the web site in order to steal their credentials. SQL injection too.

One famous breach was in 2012, and didn’t require fancy technology to pull off, just some knowledge about basic Rails and and some logic. Most Rails apps used to create users like this: 

User.create(params[:user])

User.create({admin: true})

This will use all of the parameters of a user instance; someone figured out they could send a POST request that includes admin: true, and achieve admin rights just like that.

I simply added a <input value=USER_ID name=public_key[user_id]> field to Public key update form, where USER_ID = 4223 (from https://api.github.com/users/rails).

Backend didn't whitelist accessible attributes and had something like this:
@key = PublicKey.find(params[:id])
@key.update_attributes(params[:public_key]) #Oh no! We passed public_key[user_id] of our victim!

Now our victim (Rails) has our public key associated with their account. You can read/write in any public/private repo on github.

http://homakov.blogspot.com/2012/03/how-to.html
http://homakov.blogspot.com/2014/02/how-i-hacked-github-again.html

Rails uses something called sessions to maintain knowledge of the user throughout their actions in an app. The web uses HTTP for communication between browsers and servers, and HTTP will not store user information. Each time you make a request from a browser, you essentially are doing so as a new person. And this is for reasons of security. However, since applications need to keep knowledge of who you are from a request for an item you want to buy to the request to submit your financial information, they need to store identification for you themselves. Rails does this with sessions. The name itself tells you that a user’s interaction with the app is not considered in terms of pages requested, but in sets of pages requested, or the duration of time spent logged in, to be more precise. A session usually consists of a hash of values and a session id, usually a 32-character string, to identify the hash. It’s created with a few completely random numbers (the time and the unique identifier Ruby has on the web server are among them) and then encrypted with an algorithm called MD5, and then stored in a cookie. Every request the browser sends uses that cookie to authenticate its request. If someone can get that cookie, they will be authenticated as that user by the app. 

Rails makes it very easy to force all traffic over a secure connection with ssl, done in the Rails config file.  reset_session is a good countermeasure against session fixation (do not understand this well enough to discuss). 

CSRF - Forged requests

This attack method works by including malicious code or a link in a page that accesses a web application that the user is believed to have authenticated. If the session for that web application has not timed out, an attacker may execute unauthorized commands.

To protect against all other forged requests, we introduce a required security token that our site knows but other sites don't know. We include the security token in requests and verify it on the server. This is a one-liner in your application controller:

protect_from_forgery

redirection - if your site allows an action that routes to legacy actions to pass on whatever is in the url string (for example if you wanted to preserve whatever parameters were included), you’re opening the door for a url or code which can be used to steal the authentication in the request. One of the best safeguards is a whitelist of accepted parameters. In general prefer whitelists to blacklists (what is allowed, vs what is forbidden), because you can be completely explicit about what is allowed and how you handle it. A list of forbidden things is probably never complete enough.

User authentication plugins like devise and authlogic

Optimization
One of the side effects of code that makes it very easy and simple to do powerful things like database queries, is that it’s very easy to do something that will cause problems, because it doesn’t look like a problem at first glance. 


N + 1 queries can look harmless. Because Rails associations look like object properties - which is what they are intended to do - it can be very easy to forget that they actually represent your database, and need the kinds of structure database calls require.

Here’s an example of what look like two properties of one object in your view code.

Eager loading in controllers and models - now when you need something from the database you get everything you will need soon, too.


A database index is exactly what it sounds like. If you think of the index at the back of a reference book: a quickly searchable list of pointers to get to the actual data. Without an index, a database query might have to look at every row in your database table to find the correct result.
caching. we’re going back to the kitchen analogy one more time. Let’s say the cooks don’t know a certain conversion they need to make for an amount of an ingredient -  8TB of butter = half a cup, and have to go to the computer or the cookbook and look it up every time they need any butter, which is all the time. Caching is writing that conversion down and leaving it in plain sight. The kitchen runs much faster now.

two main types, page caching in your controllers and application level caching, with memcache.

memcache - This is the standard caching technique in rails and it is fairly easy to use. Simply set your cache_store to mem_cache_store and add memcache servers.


Deploying
Capistrano meals

Rails was one of the first frameworks to get widespread adoption, which meant early users felt a lot of the pain in its rough edges. Deploying means actually taking your code and copying it a place where it gets served to the real world. It means making sure that place is set up to do exactly what your application needs it to. Deploying was tough of them because so much of what the application needed was not actually in the application or provided by the framework - web servers, caching servers. Many things that require some unix skills and admin access. As Rails evolved, ways of managing the environments you deploy to and the process of moving your code to them evolved into something that today is very straightforward.

The main workflow developers follow is to work on their own machines, and then to test it with everything it will need in the real world, and finally to publish it to the real world. But each stage has different needs. For example when you work locally, other people can't interact with your code. When you need users to test your application, you need it to be hosted where they can reach it, but you might have sensitive information you don't want shared with anyone else. You might not need the kind of power for user testing you'd need in the real world, and so your web servers and database might be less complicated or have less memory available. Rails manages the different configurations you want for different needs with environments. You can keep all the settings that best fit each type of need in specific environment settings files - dev for local, stage for real world testing, and production for real world use.

Capistrano is a Ruby program that gives you a set of advanced tools to deploy web applications to your servers. In its simplest form, Capistrano allows you to copy code from your source control repository (SVN or Git) to your server via SSH, and perform pre and post-deploy functions like restarting a webserver, bust cache, rename files, run database migrations and so on. With Capistrano it’s also possible to deploy to many machines at once. And capistrano deployment instructions are called meals - you have one for each type of environment you wish to deploy to.

If you run the command `capify .` in your Rails root directory, it will create a special file called Capfile in your project, and add a template deployment meal at config/deploy.rb in your Rails project. The deploy.rb file is where all the magic happens! You can start by deleting everything in the template file, as this guide will help you fill it with the correct code for a successful deployment meal.

Capistrano needs access to the repository where your code lives as well as the servers it needs to be run on. It uses a gem called multistage to manage different environment deployment tasks, calling them “stages.” You’ll have one for staging and one for production. Then you’ll need to set up their config files, in a directory called deploy inside your config directory - staging.rb and production.rb. [slide] Inside them you also define roles, for different kinds of communication for different aspects in your application.


server "my_fancy_server.com", :app, :web, :db, :primary => true
set :deploy_to, "/var/www/meal"

You test your setup by running the command cap deploy:setup from within your rails root directory. This will make sure your app can connect to everything it needs to properly. And you can check your deployment environment with the command cap deploy: check. If anything’s wrong in your environment, this command will give you verbose error messages telling you what it is. 

To deploy, simply run the command cap deploy: production (or cap deploy: staging).
The command will display a lot of output about what it’s doing, which is very useful to debug and confirm things are working the way you intend them to.

There are a few capistrano settings where you’ll want to improve on the defaults. One is getting code from the repo. By default, capistrano will copy your entire your repo every time you deploy, but you really don’t need to do that. Once you’ve deployed it the first time, you’ll just want whatever has changed - a much quicker process. You do this by setting :deploy_via to :remote_cache in your deploy.rb file.

Capistrano is great at making everything you need to do when you create or update your app very easy, by executing tasks through what are called custom hooks. You can run database migrations, restart servers, send email notifications, all sorts of things. If you need these things to happen when you deploy, you can make your deploy command call them all, so that all you need to do is run the deploy command itself. You define a task and configure the hook :after_deploy to call it, and now it’s called after each time you run the deploy command.



[Ruby on Rails Tutorial](http://www.railstutorial.org/book)


 Git and Open Source
 
You get to a natural stopping point with your code and you want to commit it to the project, or just save a snapshot for yourself. open source projects contain a lot of moving parts, and version control tools like git are crucial to keeping them in good working order. open source means free, and anyone can contribute to public projects. your code may not be accepted into the project though, and at that point you could decide to move forward with your own version. And if more people end up liking your code than the original, you may supercede it in common use. This happens all the time with gems.





