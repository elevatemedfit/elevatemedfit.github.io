---
layout: post
title:      "Sinatra Final Project – Under the Hood "
date:       2019-10-12 11:57:55 -0400
permalink:  sinatra_final_project_under_the_hood
---


What one quickly realizes while working on their Sinatra project, is the intricate framework needed to support your working application, one that is no longer limited to your desktop, but can begin to engage with the entire world! To help better understand the different components and their relation to one another, I thought I would provide a quick review as they relate to my own project. 

	First, we need to understand what Rack is and its roll in providing a key interface between our Ruby application and the real world.  Rack provides us with an interface structure found between web servers and our web application.  As a middleware, Rack handles HTTP(hypertext transfer protocol) requests from users and returns our application’s responses to the server. Rack acts as a translator allowing us to work in Ruby and successfully communicate with an HTTP server or servers. With Rack, our application isn’t required to speak HTTP!  

	Rack is critical to the proper functioning of our web application framework.  Middleware, are small components that assist with the execution of a task. 

use Rack::MethodOverride #allows us to send delete and patch requests.
use UsersController
use PostsController
use SessionsController
use Rack::Flash
run ApplicationController

Above, we see a “middleware stack” that I have included in my Sinatra project. Every incoming request will pass through each middleware from top to bottom. Requests will pass through the stack where Sinatra takes over. 

	Sinatra can be found on top of Rack within our Rack-based application stack as middleware.  It provides us with a library of methods that enhance the users ability to move about our application.  More specifically, Sinatra stores routes and specific actions to be taken when these routes are hit. When our application receives a request, Sinatra matches the requested route to the stored routes and takes action - if there is a match.

	To understand how Sinatra is engaged, we need to understand three key components that will allow us to utilize the power of Sinatra:

	First, once Sinatra has been installed, our require `./app/`…requires the application file named application_controller.rb in my project. 
	Second, to utilize all that Sinatra has to offer, we need to have our AC class inherit from the Sinatra::Base all of Sinatra’s functionality. Our Ruby-based ApplicationController class, through inheretence, is transformed into a web application “by giving it a Rack-compatible interface through inheriting from the “base” of the Sinatra framework.”
	Finally, the `run ApplicationController` starts our application, which is found in the `application_controller.rb` file. The AC will handle all incoming requests to our application and will send our responses back to the client.  In essence, when our AC inherits from Sinatra, the AC becomes a Sinatra controller. We mount the ApplicationController using the mounting method “run”. 

	These three components are at the heart of our framework that allows us to include the power of Sinatra and provide a usable and functioning interface.
	
require './app/controllers/application_controller'
class ApplicationController < Sinatra::Base
run ApplicationController

The content of your blog post goes here.
