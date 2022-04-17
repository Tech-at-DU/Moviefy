---
# Working with Authorization Flow
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
1. **Build out Authorization Flow**
1. Final Touches


According to the flow, we should first request a temporary token.

# Expanding the APIClient class 

> Let's create the method for it.

```Swift
func createRequestToken(_ completion: @escaping (Result<AuthenticationTokenResponse>) -> ()){}
```

Notice how we are expecting a result of the type `AuthenticationTokenResponse`, which we added previously.

The body is very similar as the method you did to fetch popular and upcoming movies.

```Swift
do{
    let request = try Request.configureRequest(from: .token, with: [:], and: .get, contains: nil)
    session.dataTask(with: request) { (data, response, error) in

      if let response = response as? HTTPURLResponse, let data = data {
          let result = Response.handleResponse(for: response)
          switch result {
          case .success:
              let result = try? JSONDecoder().decode(AuthenticationTokenResponse.self, from: data)
              completion(Result.success(result!))
              print(result)

          case .failure:
              completion(Result.failure(NetworkError.decodingFailed))
          }
      }
    }.resume()
}catch{
    completion(Result.failure(NetworkError.badRequest))
}
```

# Calling createRequestToken 

We want to login the user when they tap the button.

> In that action, add the call to the API.


```Swift
APIClient.shared.createRequestToken { (result) in
    switch result{
    case let .success(token):
    DispatchQueue.main.async {
        print(token.request_token)
    }
    case let .failure(error):
        print(error)
    }
}
```

# Adding AuthenticationServices 

Now that we have our temporary token, we'll use it with TMDB authentication flow. There are a few ways of doing this. We'll take advantage of Apple's API that handles this process very easily.

> Add the import and delegate.


```Swift
import AuthenticationServices
```

```Swift
class LoginViewController: UIViewController, ASWebAuthenticationPresentationContextProviding {}
```

The delegate will need the following method, that's saying what view is going to be responsible of presenting the webview with the auth flow. 

> Add it at the end of the current class.


```Swift
func presentationAnchor(for session: ASWebAuthenticationSession) -> ASPresentationAnchor {
    return view.window!
}
```

# Calling the Auth Flow 

Right after we get back the token, let's call a method that will initiate the flow.

> Initiate the flow 

```Swift
self.authorizeRequestToken(from: self, requestToken: token.request_token)
```

> Add that method 
>

```Swift
func authorizeRequestToken(from viewController: UIViewController, requestToken: String) {}
```

The method takes in a view controller (from where we will show a web view) and the token needed.


> Add that method 


```Swift
let url = URL(string: "https://www.themoviedb.org/authenticate/\(requestToken)?redirect_to=moviefy://auth")!      
// Use the URL and callback scheme specified by the authorization provider.
guard let authURL = URL(string: "https://www.themoviedb.org/authenticate/\(requestToken)?redirect_to=moviefy://auth") else { return }
    let scheme = "auth"
    // Initialize the session using the class from AuthenticationServices
    let session = ASWebAuthenticationSession(url: authURL, callbackURLScheme: scheme)
    { callbackURL, error in
      // Handle the callback.
      guard error == nil, let callbackURL = callbackURL else { return }

      // The callback URL format depends on the provider.
      let queryItems = URLComponents(string: callbackURL.absoluteString)?.queryItems
      print(queryItems)
      guard let requestToken = queryItems?.first(where: { $0.name == "request_token" })?.value else { return }
      let approved = (queryItems?.first(where: { $0.name == "approved" })?.value == "true")

      print("Request token \(requestToken) \(approved ? "was" : "was NOT") approved")

      self.startSession(requestToken: requestToken) { success in
        print("Session started")
      }
    }
    session.presentationContextProvider = self
    session.start()
```

```Swift
func startSession(requestToken: String, completion: @escaping (Bool) -> Void) {
   APIClient.shared.createSession(requestToken: requestToken) { (result) in
      switch result{
      case let .success(session):
         DispatchQueue.main.async {
           print(session.session_id)
         }
      case let .failure(error):
            print(error)
     }
  }
```

> Create the required `createSession` method in the APIClient.

```Swift
func createSession(requestToken: String, _ completion: @escaping (Result<CreateSessionResponse>) -> Void){}
```

# Understanding the Process 

To understand everything going on here, is important to read how we can authenticate a user through a web service. 

Here's a short document that explains it, form Apple Docs:

[Authenticating a User Through a Web Service](https://developer.apple.com/documentation/authenticationservices/authenticating_a_user_through_a_web_service) 

The flow looks something like this:

![UIFlow](/assets/auth-flow.png)

# Now Commit

```bash
$ git add .
$ git commit -m 'create request token and setup authentication services'
$ git push
```
