---
layout: post
title:      "HTTP request and response"
date:       2019-11-19 19:19:16 +0000
permalink:  http_request_and_response
---


Shotgun is run and the first GET request is the App Root get "/" . This GET route tells the server if a user is logged_in? then redirect the user to "crochet-patterns" GET route in crochet_pattern_controller.rb. Otherwise the response sent back is :sessions/login'  If a user is already signed up then the user can login with a username and password. when the user hits the login button.  A POST login request is sent to the server, the server then matches the request to the route then send back a response 

below the Login button there is another button called Sign Up with a href="/signup" when a new user hits the signup button a get request is sent to the server, the server then matches the request to the route "/signup"  in the sessions_controller.rb this is called controller action.  The response sent back to the user is :'/sessions/signup'. the user 

