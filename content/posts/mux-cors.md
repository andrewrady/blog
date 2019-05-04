---
title: "Mux Cors"
date: 2019-05-04T09:00:50-06:00
tags: ["golang", "api", "cors"]
draft: false
---

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