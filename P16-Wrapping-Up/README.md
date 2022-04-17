---
# Final Touches
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
1. Preparing for Authentication
1. Updating Routes and Models for Authentication
1. Build out Authorization Flow
1. **Final Touches**

Final stretch!

As of now, if you try running the code above, you'll get an error saying the url can't be opened.

```Swift
redirect_to=moviefy: //auth
```

Right now you are saying to safari, that the phone should open the app moviefy.

This happens from an external source and your app needs a way of knowing when an external party wants to open it.

You need to set up a URL Scheme.

![UIFlow](/assets/scheme.png)

[source](https://developer.apple.com/documentation/xcode/defining-a-custom-url-scheme-for-your-app)

This should get you a working session now.

Make sure you get the message on the console:

```Swift
Request token YOUR_TOKEN was approved
```

# Getting the Username

Now it's your turn to find the way of getting the username and displaying it in the `LoginViewController`.


**Hint** check out the documentation [here](https://developers.themoviedb.org/3/account/get-account-details) to get started.

# Stretches

> Give the user the option to logout 😉 (this should clear the username).



# Now Commit

```bash
$ git add .
$ git commit -m 'create URLScheme'
$ git push
```
