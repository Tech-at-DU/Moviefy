---
# Model The Response
---

1. Look at The Movie DB (TMDb) API
1. Get to know the current state of the project
1. **Model the response**
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
1. Build out Authorization Flow
1. Final Touches


# Introducing Our Data

Before sending requests, you will model the response data for the endpoint that returns featured movies.

The response we are recieving looks like the following:

```JSON
{
    "page": 1,
    "total_pages": 12,
    "results": [
        {
            "id": ".........",
            "title": "Joker",
            "poster_path": "images/....../poster.jpg",
            "release_date": "2019-09-01"
        },
        { ... }
    ]
}
```

Looking at this snippet, we can gather that the data gives us paginated results with a total of 12 pages. We can also gather that the results are made up of movies with parameters that reflect our `Movie` struct.

# Using Codable 

We know that we want to use the **Codable** protocol.

> The **Codable** API enables us to leverage the compiler in order to generate much of the code needed to encode and decode data to/from a serialized format, like JSON (our data). **Codable** is actually a type alias that combines two protocols — Encodable and Decodable — into one.

With this newfound information, lets move forward with implementing Codable into the project. 

> Locate the file `Movie.swift` 

> Type in the missing content so that your file looks like the following:

```swift
struct Movie {
    let id: Int
    let title: String
    let posterPath: String
    let releaseDate: String
}

// properties within a Movie returned from the API that we want to extract the info from
extension Movie: Codable {

    enum MovieCodingKeys: String, CodingKey {
        case id
        case posterPath = "poster_path"
        case title
        case releaseDate = "release_date"
    }

    init(from decoder: Decoder) throws {
        // Decode each of the properties from the API into the appropriate type (string, etc.) for their associated struct variable
        let movieContainer = try decoder.container(keyedBy: MovieCodingKeys.self)
        id = try movieContainer.decode(Int.self, forKey: .id)
        posterPath = try movieContainer.decode(String.self, forKey: .posterPath)
        title = try movieContainer.decode(String.self, forKey: .title)
        releaseDate = try movieContainer.decode(String.self, forKey: .releaseDate)
    }
}
```

In the extension, we have _encoded_ a value into data and can now this information from the API in our Swift project!

# Coding Keys

We defined **coding keys** to tell Swift exactly where to find the information to fill the model's variables. However, we actually only need this because the API uses a different naming convention for it's properties.

Did you notice how `posterPath` and `releaseDate` needed to be reassigned to `"poster_path"` and  `"release_date"`. Why is that? 
 
It's because these two needed to be mapped since they're named differently on the API compared to our Movie struct in Xcode. Note how `"poster_path"` and  `"release_date"` are also the only variables that are set to a string. This is because in the JSON we receive from the request, these variables are named differently (using **snake_case**, rather than **camelCase** which is the recommended practice for Swift).


# Handle Paginated Results 

Remember the JSON structure from earlier? In case you forgot, here it is again: 

```JSON
{
    "page": 1,
    "total_pages": 12,
    "results": [
        {
            "id": ".........",
            "title": "Joker",
            "poster_path": "images/....../poster.jpg",
            "release_date": "2019-09-01"
        },
        { ... }
    ]
}
```

As you can see, we have paginated results. 

> So let's create a type to handle that. You can do it in the same `Movie.swift` file.
>
> Type in the missing content so that your file looks like the following:

```swift
struct MovieApiResponse {
    let page: Int
    let numberOfPages: Int
    let movies: [Movie]
}

extension MovieApiResponse: Codable {

    private enum MovieApiResponseCodingKeys: String, CodingKey {
        case page
        case numberOfPages = "total_pages"
        case movies = "results"
    }

    init(from decoder: Decoder) throws {
        let container = try decoder.container(keyedBy: MovieApiResponseCodingKeys.self)
        page = try container.decode(Int.self, forKey: .page)
        numberOfPages = try container.decode(Int.self, forKey: .numberOfPages)
        movies = try container.decode([Movie].self, forKey: .movies)
    }
}
```

We just went through a lot of important stuff! We learned **how to use codable with JSON in our Swift models**, and also learned a bit more on **how to work with APIs** in order to get data flowing into our app!

We can't get our data flowing just yet though, since we have don't have a way to interface with the API. To do so, we'll need a networking layer, so let's get to it!

# Now Commit

```bash
$ git add .
$ git commit -m 'Create codable model'
$ git push
```
