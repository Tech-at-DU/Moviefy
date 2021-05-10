---
title: "Configuring the Request"
slug: configure-request
---

1. Look at The Movie DB (TMDb) API
1. Get to know the current state of the project
1. Model the response
1. Work with Swift API Client
1. Handle network errors 
1. Create HTTP methods and routes
1. **Configure the request**
1. Implement Encoder
1. Handle the response
1. Make the call
1. Display the data 
1. Additional Starter Challenge
1. Preparing for Authentication
1. Updating Routes and Models for Authentication
1. Build out Authorization Flow
1. Final Touches

# Configure Request

Inside the `Request` struct in `Request.swift`, create a new method that will configure the request with the endpoint, parameters, method and body if applicable.

```Swift
static func configureRequest(from route: Route, with parameters: [String: Any], and method: HTTPMethod, contains body: Data?) throws -> URLRequest {

    // safely unwrap URL or return error 
    guard let url = URL(string: "https://api.themoviedb.org/3/\(route.rawValue)") else { fatalError("Error while unwrapping url")}
    var request = URLRequest(url: url, cachePolicy: .reloadIgnoringLocalCacheData, timeoutInterval: 10.0)
    request.httpMethod = method.rawValue
    request.httpBody = body
    try configureParametersAndHeaders(parameters: parameters, headers: headers, request: &request)
    return request
}
```

Do you see already how are you using the error enum?

You are calling the method `configureParametersAndHeaders` that you didn't have yet. Add the following:

```Swift
static func configureParametersAndHeaders(parameters: [String: Any]?,
                                              headers: [String: String]?,
                                              request: inout URLRequest) throws {
    do {
        if let headers = headers, let parameters = parameters {
            try Encoder.encodeParameters(for: &request, with: parameters)
            try Encoder.setHeaders(for: &request, with: headers)
        }
    } catch {
        throw NetworkError.encodingFailed
    }
}
```

Here you try to encode both the parameters and headers, before making the call.

Notice again how you are using the error enum.

But you don't have an encoder yet, let's take care of that in the next section.

# Now Commit

```bash
$ git add .
$ git commit -m 'Configure the Request'
$ git push
```