---
title: "Authentication Setup"
slug: preparing-for-authentication
---

1. Look at The Movie DB (TMDb) API
1. Get to know the current state of the project
1. Model the response
1. Work with Swift API Client
1. Handle network errors 
1. Create HTTP methods and routes
1. Configure the request
1. Implement Encoder 
1. Handle the response
1. Make the call 
1. Display the data 
1. Additional Starter Challenge
1. **Preparing for Authentication**
1. Updating Routes and Models for Authentication
1. Build out Authorization Flow
1. Final Touches


We are going to use the other tab bar to log in the user.


> [action]
> Create a new ViewController and call it `LoginViewController`.
>
> Make the changes needed in the storyboard to use that new class and add a button and a label to the view.

![LoginStoryboard](/assets/login-storyboard.png)

# Understanding the Process 

Great! Now that the UI is setup, we will move forward with setting up authentication for our users. 

> [action]
> Read about how TMDB authorizes uses in their documentation.
>
> [TMDB user authorization docs](https://developers.themoviedb.org/4/auth/user-authorization-1)

# Session Id 

You'll need a session id as well. Read how to get a session id in the [docs](https://developers.themoviedb.org/3/authentication/how-do-i-generate-a-session-id).

>[Info]
> **Session id**: is a piece of data that is used in network communications to identify a session, a series of related message exchanges. 
> Session identifiers become necessary in cases where the communications infrastructure uses a stateless protocol such as HTTP.  
> 


# Now Commit

```bash
$ git add .
$ git commit -m 'Setup Login UI'
$ git push
```
