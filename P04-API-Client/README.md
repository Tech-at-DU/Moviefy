---
# Working with the API Client
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
1. Additional Starter Challenge
1. Preparing for Authentication
1. Updating Routes and Models for Authentication
1. Build out Authorization Flow
1. Final Touches

# Setup Network File Structure 

> Create a new folder and call it `Networking`. Every new file from now on should be moved here.

> Create a new file and call it `APIClient.swift`. Your API Client will own the URLSession and will be created using a default `URLSessionConfiguration`.


```Swift
// APIClient.swift

struct APIClient{
    static let shared = APIClient()
    let session = URLSession(configuration: .default)
}
```

> **APIResponse**: are value types that will be created from the JSON response. 
> **APIClient**: will receive requests, send them to the server and then notify the caller via a callback.

Here are a few note-worthy key-terms to help you understand the parts of the networking proccess better: 

> **Client**: a computer in a network that uses the services provided by a server.

> **Server**: a piece of computer hardware or software (computer program) that provides functionality for other programs or devices (ie clients)

> **API**: part of the server that receives requests and sends responses.

> **Network Manager / Networking Layer**: a well-structured chunk of code used to make API requests and handle its responses from an external server.


What we'll be doing moving forward in this section is creating a custon networking layer that communicates with the API. In doing so, this is how we will be populating data in our UI instead of having it be empty or using mock data. 

That will be the basic structure of a reusable API client.

> Create a new file and call it `Request.swift`. Here you will create the complete request.


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

# Now Commit

```bash
$ git add .
$ git commit -m 'Began creating networking layer'
$ git push
```

