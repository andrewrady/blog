+++
title = 'Code Smells'
date = 2025-01-17T13:24:12-07:00
+++

## Introduction

After coding for a while and making more mistakes then anyone wants to admit we as programmers tend to create a spiddy-sense of potential issues when doing code reviews. This is one of the primary reason we as an industry do code reviews.
It's commonly called "code smell" - when we see a pattern or code usage that seems off. A few months ago I ran into one of these and wanted to highlight the usage, because I see even experienced software engineers fall into this common practice. I would like to highlight
that while good practice in theory is commonly agreed upon, people get lost in the details. That's ok as long 

## Setup

Below is some example code I've see in different variations before. It's fairly simple, all it does is gets a results of clients from a service and returns them. In this situation the method of the service takes in an optional parameter for a name...yes I've seen this before.
Once we get the results we'll grab the first result and perform our business logic.


*Please note: I'm making some of the common mistakes on purpose - I'm sure many of you can easily spot the mistakes before the next section :)
```c#
var results = await _clientService.GetClients("josh"); //returns an IList<Client> models

if (results != null && results.Any() == true)
{
    var client = results.First();

    //logic for client actions
}

```

## Concerns

For those who work to keep their functions and methods simple there is one very glaring issue here. You have a method that is named one thing "GetClients" but has a parameter to get a single client. An important principle in code design is to have your methods or function
do one thing, and this method is doing two things. Additionally, the naming convention implies that it's doing one thing... getting a list of clients because it's plural. The issue is by having an optional parameter to get a single client the method is now doing two things. This is a classic 
code smell that a bare minimum that it's time for a new method to get a single client.

## Improvements

Let's take the code from above and make some small changes. There is three main things we can change based on creating a new method that just returns a single Client record. 
1) Improve the variable name as it reflects we're getting a single client record.
2) We can simplify our conditional to check if the results from the service is null.
3) Since it's a single record we don't have to put it in a list.
4) Anyone using the method doesn't need to know about an optional parameter to get s specific record.

### Single Record
```c#
var client = await _clientService.GetClient("josh");

if (client == null)
{
    //Error Handling
}

//logic for client record

```
### Multiple Records
```c#
var clients = await _clientService.GetClients();

if (client.Any() != true)
{
    //Error Handling
}

//logic for client records

```

## Conclusion

It's a valid concern when creating software not to bloat our application. I think that is the main system to this issue, but in our effort we make more work for ourselves. Situations like this is a common when trying to 
take our existing code base and make small changes to accomplish our goals. Keeping in mind basic principals like this will keep our code easier to understand and maintain over the life cycle.

