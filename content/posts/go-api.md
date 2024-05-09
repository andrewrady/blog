+++
title = "Go Api"
date = 2019-03-11T17:57:45-06:00
tags = [ "golang", "api"]
draft = false
+++


## Golang First API

I have been following Golang for a little but. It seemed interesting to me for a few reasons. One major one was the speed of it. Another was it's syntax is similar to python. I am no python developer, but I have made a few side project with it. SO I decided to update and an aging Rails application. It's just a simple crud application that displays martial arts rings at tournaments. While I could write the entire website with Go I opted in to make an api. The reason is I want to make a React site and mobile apps made with React Native. It's a pretty simple rest API that needed to connect to a database. I used a few packages to make development practical

- [Mux](https://github.com/gorilla/mux) (for route handling)
- [gorm](https://github.com/jinzhu/gorm) (an orm for golang to interface with databases)
- [jwt-go](https://github.com/dgrijalva/jwt-go) [to help create jwt for Auth]
- [bcrypt](golang.org/x/crypto/bcrypt) (to hash passwords)

## Things I have learned

importing packages are fairly similar to other languages as python. In Golang we can import a package like,
```
import("os")
```
or for multiple imports,
```
import(
  "os"
  "fmt"
  "net/http"
)
```
These are packages that come with Go, but we cna  an import other people's packages with an import path to their github.
```
import(
  "os"
  "fmt"
  "net/http"
  "github.com/gorilla/mux
)
```
So importing packages are pretty simple. While there seems to be a few different dependency managers in Golang there is no standard at this time like NPM for node. For this project I ended up using [dep](https://github.com/golang/dep) More on this in another post.

Another thing I learned from this project is export functions and how to use them in different files. This project is pretty small so the `main.go` handles all of the routing, and the functions that handle all of the logic is broken into different files. For example the `/ring` route returns all of the active rings. The function that handles communication to the database and return the values in json is in the `rings.go` file. For the `main.go` to be able to use the `AllRings` function all we need to do is capitalize the function. Any function in that file that isn't capitalized can only be used within that file. Personally I like this simple practice. I have forgot to export a function in larger files and took sime valuable time debugging to figure out I forgot this.

## Wrap up
The project is hosted in github and still needs some work. This is a side project that gets used only a few times a year so I continue to work on it from time to time. If you want to check it out head over and have a [look at my github](https://github.com/andrewrady/ring-api)
