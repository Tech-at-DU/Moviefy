---
title: "Create HTTP Methods and Routes"
slug: HTTP-Methods-and-Routes
---

1. Look at The Movie DB (TMDb) API
1. Get to know the current state of the project
1. Model the response
1. Work with Swift API Client
1. Handle network errors 
1. **Create HTTP methods and routes**
1. Configure the request
1. Implement Encoder
1. Handle the response
1. Make the call
1. Display the data 
1. Additional Starter Challenge
1. Preparing for Authentication
1. Updating Routes and Models for Authentication
1. Build out Authorization Flow
1. Final Touches

# HTTP Methods and Routes 

> [action]
> Go back to `Request.swift` and add the following enums before the existing struct:
>
```Swift
public enum HTTPMethod: String{  
    case get = "GET"
    case post = "POST"
    case put = "PUT"
    case patch = "PATCH"
    case delete = "DELETE"
}
```

This enum represents all the available HTTP methods you will be able to use.

```Swift
public enum Route: String{
    case movies = "discover/movie"
}
```

This enum represents all the available endpoints you will be able to use.

# Now Commit

```bash
$ git add .
$ git commit -m 'Create HTTP methods and routes'
$ git push
```