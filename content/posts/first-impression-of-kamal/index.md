+++
title = 'First Impression of Kamal'
date = 2025-06-06T17:34:28-06:00
draft = true
+++

I've been writing dotnet code for the last five years, before that I was a front end developer. I've always built different things with Rails apps, but it's been years. Lately, I decided to build a production app that's being used by my martial arts school. My goal was to see what has changed, and thought it would be cool to look at the process now that I have multiple professional years. Before I just followed the convention of how to setup an MVC without truly understanding how the stack works. Now I have a much better understanding

What was the biggest takeaway from this project? Not Rails itself, but Kamal...and the control it gives developers.

## Cloud Computing

A while ago DHH wrote about leaving the cloud and his company's experience. I tend to agree with his opinion that cloud computing is overkill for most companies and is a huge cost. I've worked directly in Azure and I've seen the cost of enterprise software - and it's huge. I don't think people outside of this scale of apps know just how much they can get. 

Does this mean I run everything on bare metal...nope! Most of my side projects are in the cloud, but on much cheaper hosts than Azure. There are some clear advantages to cloud computing...this is not a black and white conversation. There's a lot of nuance. 

Why do I bring this up in relation to Kamal?

Well...with Kamal you can configure either way. Want to run in Digital Ocean, Linode, or AWS? Easy. Have a physical server, also not an issue. This flexibility is great! The up front cost of learning how Kamal works and setup is a little more, but once you get the workflow down you have way more opportunity.

Compared that to a standard dotnet project. Hosting? Probably Github or Gitlab. Hosting? Let's be real...most likely Azure - download a Github workflow the deploys to Azure. It's super easy and get your application in the cloud within an hour. 

What's the big point?

It gives more control to the developer and doesn't lock you into the cloud ecosystem. Of course you can take your dotnet application and deploy to other cloud providers or on-prem, but not on the same level Kamal does for Rails applications. 

## Conclusion

> "It gives more control to the developer and doesn't lock you into the cloud ecosystem."

I've setup a handful of CI/CD for dotnet applications, and while they're pretty easy it's always based on third-party services. With a little more research I'm sure there is some fairly easy CI/CD workflows that will handle building and deploying to either those or a local server. Although I haven't seen any packages with the traction that Kamal has for Rails. I think it's important as a developer to look outside our own bubbles and see how others are handling process. The cloud push has been huge in the 2010s and is still continuing...but I think we'll see more companies push back to on-prem servers again. As dotnet developers we could learn a trick or two from Kamal.
