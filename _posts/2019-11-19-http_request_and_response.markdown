---
layout: post
title:      "HTTP request and response"
date:       2019-11-19 14:19:17 -0500
permalink:  http_request_and_response
---


Shotgun is run and the first GET request is the App Root get "/" . This GET route tells the server if a user is logged_in? then redirect the user to "crochet-patterns" GET route in crochet_pattern_controller.rb. Otherwise the response sent back is :sessions/login'  If a user is already signed up then the user can login with a username and password. when the user hits the login button.  A POST login request is sent to the server, the server then matches the request to the route in the sessions_controller.rb.  A response is send back from the server, in this case the login response is to redirect the user to "crochet-patterns" GET route.

```
  get '/login' do
    erb :"sessions/login"
  end
```

Below the login button there is another button called Sign Up with a href="/signup" when a new user hits the signup button a get request is sent to the server, the server then matches the request to the route "/signup"  in the sessions_controller.rb this is called controller action.  The response sent back to the user is :'/sessions/signup'. This form allow the user to input a username, email, and password.  After the user inputs the data and clicks the sign up button. Another POST sign up request is sent to the server, the server then matches the request to the route in the sessions_controller.rb.  The user's data is saved in the app the response send back is to redirect the user to "crochet-patterns" GET route
  ```
get '/signup' do
    erb :'/sessions/signup'
  end
```

After a user signs up, the user is directed to "crochet-patterns" route in the crochet_patterns_controller.rb  The GET request "/crochet-patterns" is matched to the route in the crochet_patterns_controller.rb.  A HTML (erb:"crochet_patterns/index") response is send back to the user.  The user can create a new pattern in their application by clicking the create button in the upper right hand corner of the display page. The user sends a GET request "/crochet-patterns/new" to the server, the server again mathes the request to the route in the crochet_patters_controller.rb.  A form (erb :"crochet_patterns/new") response is send back to the user.  This form allows the user to input a title, size, description and link to the pattern. 

```
  get '/crochet-patterns/new' do
    if logged_in?
      erb :"crochet_patterns/new"
    else
      redirect "/login"
    end
  end
```

