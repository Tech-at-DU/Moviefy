---
title: "Display the Data"
slug: Data-Display
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
1. **Display the data**
1. Additional Starter Challenge
1. Preparing for Authentication
1. Updating Routes and Models for Authentication
1. Build out Authorization Flow
1. Final Touches

If you run the app now you'll see the names and dates of the movies in the simulator. But no images so far.

There is a special endpoint to fetch the images, you can add it to the Request file.

```Swift
public static let baseImageURL = URL(string: "https://image.tmdb.org/t/p/w500")!
```

and then in the method that configures the cell:

```Swift
let imageURL : URL?
let imageBase = Request.baseImageURL
imageURL = imageBase.appendingPathComponent(movie.posterPath)
coverImg.kf.setImage(with: imageURL)
```

The app is using the library [Kingfisher](https://github.com/onevcat/Kingfisher). Check out their github and documentation, you can use it in your future projects, it works great and is maintained regularly.

If you run the app again. Now you should see the following: