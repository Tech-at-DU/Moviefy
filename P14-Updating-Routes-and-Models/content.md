---
title: "Updating Routes and Models for Authentication"
slug: routes-and-models
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
1. **Updating Routes and Models for Authentication**
1. Build out Authorization Flow
1. Final Touches


Now that you have a better understanding of the process, let's move forward with updating our existing code to handle authentication implementation. 

Our first stop is updating the routes. We'll be using several of them such as token, session, and account. 

## Check out the Documentation here: 
1. [authentication/token/new](https://developers.themoviedb.org/3/authentication/create-request-token)
1. [authentication/session/new](https://developers.themoviedb.org/3/authentication/create-session)
1. [account](https://developers.themoviedb.org/3/account/get-account-details)

> [action]
> Update your enum to include the following endpoints:

```Swift
public enum Route: String{
    ...
    case token = "authentication/token/new"
    case session = "authentication/session/new"
    case account = "account"
}
```

# New Models 

Since we will hit new endpoints, we are going to get new JSON structures back. We should create models to decode them. 

> [action]
> Add the following classes to new files.
>

```Swift
struct AuthenticationTokenResponse: Codable {
    let success: Bool
    let expires_at: String
    let request_token: String
}
```

```Swift
struct CreateSessionResponse: Codable {
    let success: Bool
    let session_id: String
}
```

```Swift
struct Account : Codable {
    let id: Int
    let name: String?
    let username: String?

    var displayName: String {
        if let name = name, !name.isEmpty {
            return name
        }
        return username ?? "(uknown)"
    }
}
```

At this point, your folder structure for models might now look like this:

![ModelFolder](/assets/models.png)


# Now Commit

```bash
$ git add .
$ git commit -m 'setup endpoints and models'
$ git push
```
