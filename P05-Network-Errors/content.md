---
title: "Handle network errors"
slug: Network-Errors
---

1. Look at The Movie DB (TMDb) API
1. Get to know the current state of the project
1. Model the response
1. Work with Swift API Client
1. **Handle network errors**
1. Create HTTP methods and routes
1. Configure the request
1. Implement Encoder 
1. Handle the response
1. Make the call 
1. Display the data 

# Error Handling

Whenever there's an error in any step of the network call, we should be able to identify where it happened and as much information as possible.

> [action]
> Create a new file and call it `NetworkError.swift`. Here you'll have an enum with all the possible errors.
>
```Swift
public enum NetworkError: String, Error {
    case parametersNil = "Parameters were nil"
    case encodingFailed = "Parameter Encoding failed"
    case decodingFailed = "Unable to Decode data"
    case missingURL = "The URL is nil"
    case couldNotParse = "Unable to parse the JSON response"
    case noData = "Data is nil"
    case fragmentResponse = "Response's body has fragments"
    case authenticationError = "You must be authenticated"
    case badRequest = "Bad request"
    case pageNotFound = "Page not found"
    case failed = "Request failed"
    case serverError = "Server error"
    case noResponse = "No response"
    case success = "Success"

}
```

# Now Commit

```bash
$ git add .
$ git commit -m 'Handle network errors'
$ git push
```