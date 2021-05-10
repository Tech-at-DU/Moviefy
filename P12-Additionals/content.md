---
title: "Your Turn to Try"
slug: Additionals
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
1. **Additional Starter Challenge**
1. Preparing for Authentication
1. Updating Routes and Models for Authentication
1. Build out Authorization Flow
1. Final Touches

Add a new section to the home page to display Upcoming Movies.

Endpoint here.

## Stretch Challenges 

We can get the base URL for images by calling the /configuration endpoint first. Create a new request to fetch those URLs. You will need the following type.

```Swift
struct MovieDBConfiguration : Model {
    struct Images : Model {
        let baseUrl: URL
        let secureBaseUrl: URL
        let backdropSizes: [String]
        let logoSizes: [String]
        let posterSizes: [String]
        let profileSizes: [String]
        let stillSizes: [String]
    }

    let images: Images
    static var current: MovieDBConfiguration?
}
```

