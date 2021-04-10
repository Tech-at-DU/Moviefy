---
title: "Working with the API Client"
slug: API-Client
---

1. Look at The Movie DB (TMDb) API
1. Get to know the current state of the project
1. Model the response
1. **Work with Swift API Client**
1. Handle network errors 
1. Create HTTP methods and routes
1. Configure the request
1. Implement Encoder 
1. Handle the response
1. Make the call 
1. Display the data 

# Setup Network File Structure 

> [action]
> Create a new folder and call it `Networking.swift`. Every new file from now on should be moved here.
>
> Create a new file and call it `APIClient.swift`. Your API Client will own the URLSession and will be created using a default `URLSessionConfiguration`.
>
```Swift
// APIClient.swift

struct APIClient{
    static let shared = APIClient()
    let session = URLSession(configuration: .default)
}
```

That will be the basic structure of a reusable API client.

> [action]
> Create a new file and call it `Request.swift`. Here you will create the complete request.
>
```Swift
// Request.swift

struct Request {
    static let headers = [  
        "Accept": "application/json",
        "Content-Type": "application/json",
        "Authorization": "Bearer YOUR_API_KEY"
    ]
}
```

At this point we are only including the parameters that we want to send in the header of our requests. We will complete this file later, but first we need to deal with possible errors and different options for endpoints.
