---
title: "Make the Call"
slug: make-the-call
---

1. Look at The Movie DB (TMDb) API
1. Get to know the current state of the project
1. Model the response
1. Work with Swift API Client
1. Handle network errors
1. Create HTTP methods and routes**
1. Configure the request
1. Implement Encoder
1. Handle the response
1. **Make the call**
1. Display the data 

We can now go back to APIClient and finish making the call.

Inside the struct add:

```Swift
let parameters = [
       "sort_by": "popularity.desc"
]
func getPopularMovies(_ completion: @escaping (Result<[Movie]>) -> ()) {
    do{
      // Creating the request
        let request = try Request.configureRequest(from: .movies, with: parameters, and: .get, contains: nil)
            session.dataTask(with: request) { (data, response, error) in

            if let response = response as? HTTPURLResponse, let data = data {

                let result = Response.handleResponse(for: response)
                switch result {
                case .success:
                    //Decode if successful
                    let result = try? JSONDecoder().decode(MovieApiResponse.self, from: data)
                    completion(Result.success(result!.movies))

                case .failure:
                    completion(Result.failure(NetworkError.decodingFailed))
                }
            }
        }.resume()
    }catch{
        completion(Result.failure(NetworkError.badRequest))
    }
}
```

You are ready to get the popular movies with this code (place it inside the method fetchPopular in the main View Controller)

```Swift
APIClient.shared.getPopularMovies { (result) in
      switch result{
      case let .success(movies):
          DispatchQueue.main.async {
              self.movies = movies
              var basicSection = MovieSection()
              basicSection.numberOfItems = movies.count
              basicSection.items = movies
              self.sections.append(TitleSection(title: "Popular Movies"))
              self.sections.append(basicSection)
              self.setupCollectionView()
          }
      case let .failure(error):
          print(error)
      }
  }
```