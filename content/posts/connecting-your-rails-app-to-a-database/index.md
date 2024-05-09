+++
title = "Connecting Your Rails App to a Database"
tags = ["rails", "postgres"]
date = 2020-03-03T12:15:32-06:00
draft = false
+++

# Connecting your Rails application to a database
Rails default setup uses sqlite which is a great way to get starting building applications, but at some point we will need to connect to a real database. Whether you need functionality that is specific to a certain database, or you want to simulate your production environment more. Connecting to a database is pretty easy with Rails. The first thing you will need is a database installed on your computer. For my apps I primarily use Postgres and pgAdmin as my GUI.  

First we will also want to add a gem for Postgres in our  `Gemfile`

`gem ‘pg’`


Then run the command `bundle install`. Next in our Rails app we want to update the `database.yml` file in the `config` directory. There is four sections, default, development, test, and production. For a basic configuration set the default and any changes you may need in the different environments can be overridden.

```
default: &default
  adapter: postgresql
  encoding: unicode
  username: postgres
  password: postgres
  pool: 5
  timeout: 5000
  host: 127.0.0.1

development:
  <<: *default
  database: TestApp

test:
  <<: *default
  database: TestApp_test

production:
  <<: *default
  database: <%= ENV['POSTGRES_DB'] %>
```

Let’s break down this file a little. The default is where most of the key information is at. I have the username and password set to postgres, but for a real application you would want to put these into environment variables. The host is the IP address for your database. The other environments have a line `<<: *default` which pulls the config options from the default section. If you need to change anything for these environments do so after that line.
