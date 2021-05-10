---
title: "Encoder"
slug: encoder
---

1. Look at The Movie DB (TMDb) API
1. Get to know the current state of the project
1. Model the response
1. Work with Swift API Client
1. Handle network errors 
1. Create HTTP methods and routes
1. Configure the request
1. **Implement Encoder**
1. Handle the response
1. Make the call
1. Display the data 
1. Additional Starter Challenge
1. Preparing for Authentication
1. Updating Routes and Models for Authentication
1. Build out Authorization Flow
1. Final Touches

>[action]
> Create a new file and call it `Encoder.swift`
>
```Swift
public struct Encoder {

    static func encodeParameters(for urlRequest: inout URLRequest, with parameters: [String: Any]) throws {
        guard let url = urlRequest.url else { throw NetworkError.missingURL }

        if var urlComponents = URLComponents(url: url, resolvingAgainstBaseURL: false), !parameters.isEmpty {
            urlComponents.queryItems = [URLQueryItem]()
            for (key,value) in parameters {
                let queryItem = URLQueryItem(name: key, value: "\(value)")
                urlComponents.queryItems?.append(queryItem)
            }
            urlRequest.url = urlComponents.url
        }
    }

    static func setHeaders(for urlRequest: inout URLRequest, with headers: [String: String]) throws {        
        for (key, value) in headers{
            urlRequest.setValue(value, forHTTPHeaderField: key)
        }
    }
}
```

Can you figure out why we use inout parameters?

# Now Commit

```bash
$ git add .
$ git commit -m 'Create Encoder'
$ git push
```