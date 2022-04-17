---
# Handling the Response
---

1. Look at The Movie DB (TMDb) API
1. Get to know the current state of the project
1. Model the response
1. Work with Swift API Client
1. Handle network errors 
1. Create HTTP methods and routes
1. Configure the request
1. Implement Encoder 
1. **Handle the response**
1. Make the call
1. Display the data 
1. Additional Starter Challenge
1. Preparing for Authentication
1. Updating Routes and Models for Authentication
1. Build out Authorization Flow
1. Final Touches

Create a new file and call it Response

```Swift
enum Result<T> {
    case success(T)
    case failure(Error)
}

struct Response {

    static func handleResponse(for response: HTTPURLResponse?) -> Result<String>{

        guard let res = response else { return Result.failure(NetworkError.noResponse)}

        switch res.statusCode {
        case 200...299: return .success(NetworkError.success.rawValue)
        case 401: return .failure(NetworkError.authenticationError)
        case 400...499: return .failure(NetworkError.badRequest)
        case 500...599: return .failure(NetworkError.serverError)
        default: return .failure(NetworkError.failed)
        }
    }

}
```

It will have a functions to check for the status code and return error or success.
