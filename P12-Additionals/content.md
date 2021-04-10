---
title: "Your Turn to Try"
slug: Additionals
---

Add a new section to the home page to display Upcoming Movies.

Endpoint here.

Stretch Challenges 

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

