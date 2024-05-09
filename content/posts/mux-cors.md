+++
title = "Mux Cors"
date = 2019-05-04T09:00:50-06:00
tags = ["golang", "api", "cors"]
draft = false
+++

## Handling CORS with Gorilla Mux

In an earlier post I talked about create an API with golang using a few packages. One of the main ones packages many people use is mux for routes. This makes it easier handles routes within our application. Now we need setup our application to allow certain sites to talk with our api. Luckily Gorilla has another package that integrates seamlessly with Mux.

## Setting up our routes

Let's make a function in our `main.go` that handles the routes and then call it in our `main` function

```
import (
  "fmt"
  "log"
  "net/http"

  "github.com/gorilla/mux"
)

func routes() {
  myRouter := mux.NewRouter().StrictSlash(true)
  myRouter.Handle("/records", RecordsHandler).Methods("GET)
  log.Fatal(http:ListenAndServe(":8080", myRouter))
}

func main() {
  fmt.Println("Server is running on port 8080" )
  routes()
}
```

Here we have a basic implantation with one route, `/records` which refers to the function `RecordsHandler`. I didn't have that in the code snippet, but that function handles the logic of getting the records and returning the json. This works great if the application, is on the domain. If not then this is where we need to add some cors policies. 

## Gorilla Handlers
Lucky gorilla has the handlers package that plays really nicely with mux. All we need to do is import it and add a few more lines. First lets import `github.com/gorilla/handlers`, then we need to add some variables to configure for headers, methods, and origins.
```
headers := handlers.AllowedHeaders([]string{"X-Requested-With:", "Content-Type"})
methods := handlers.AllowedMethods([]string{"GET", "POST", "PUT", "DELETE"})
origins := handlers.AllowedOrigins([]string{"www.somewebsite.com"})
```
This allows the headers to be set with content-type so allow for json, the standard crud actions in the methods, and the origin sets where the api is allowed to give this information too. Now we need to alter the listen and server to passes these in.

```
log.Fatal(http.ListenAndServe("8080", handlers.CORS(headers, methods, origins)(myRouter)))
```

This will allow our api to be able to communication with our applications on different domains. This is great if we only want certain sites to be able to access our data. If we want to open the api and be public we can update the string in the `origin` variable to a wildcard,
```
origins := handlers.AllowedOrigins([]string{"*"})
```

## Wrap up
Below is the full program from above with the cors configuration as well,
```
import (
  "fmt"
  "log"
  "net/http"

  "github.com/gorilla/mux"
  "github.com/gorilla/handlers"
)

func routes() {
  myRouter := mux.NewRouter().StrictSlash(true)
  headers := handlers.AllowedHeaders([]string{"X-Requested-With:", "Content-Type"})
  methods := handlers.AllowedMethods([]string{"GET", "POST", "PUT", "DELETE"})
  origins := handlers.AllowedOrigins([]string{"www.somewebsite.com"})
  myRouter.Handle("/records", RecordsHandler).Methods("GET)
  log.Fatal(http.ListenAndServe("8080", handlers.CORS(headers, methods, origins)(myRouter)))
}

func main() {
  fmt.Println("Server is running on port 8080" )
  routes()
}
```
