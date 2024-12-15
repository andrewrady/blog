+++
title = 'Rails Experiance'
date = 2024-12-04T20:43:38-07:00
+++

# My Experience Building A Rails App As A Dotnet Developer

I use to write a lot of rails applications when I was newer as a developer. Fast forward almost a decade later with professional experience, I thought I would look into rails again.
I've slightly followed the progression of rails over the years and agree with some points of DDH's. Main about JavaScript and how it's become overly complex for web apps. Although, I personally love static type languages.
I know shocker - coming from a dotnet developer. 

## Goal
I wanted to create a basic crud application that mimicked an existing application I've built in dotnet. This way I didn't have to worry about _what_ I was making..and be able to focus more on ruby and rails.
It was a pretty simple mvc product that focused on three main points.

- Standard CRUD workflow for a handful on models
- Authentication
- Background jobs

Of course, there was more minor details on the architecture but I want to focus on more of my experience writing the application

## What I liked

The last time I wrote a Rails application in any real fashion has to be close to eight years. A lot has changed in the web world since then! The main point I really liked was just _how_ easy it was to get started.
I remembered many of the cli commands to generate models and controllers. That is a huge because anyone who works with these tools know how many there are! Just that alone I was able to scaffold out a large amount very quickly.
Another great thing was Rails documentation. When I didn't know how to setup something like nested forms for child models I was able to "easily" find how to do it directly on their documentation site.
I quotes because easy can be relative and while it was super convenient once I found it - it took me some research to get there. Seriously, Rails documentation is great and can easily be navigated to find great gems (see what I did there)!
Lastly, the plugin ecosystem is great. I was able to easily install the few gems I needed to get up and running. Since the app was pretty slim I really only need devise for authentication 
and sidekiq for sidejobs. I'm sure if this need to be put into production things would become more complex. For example, devise is a great way to start authentication but it would probably 
be worth integrating it with OAuth as well.

## What I didn't like

Rails is known for convention over configuration and overall I think that is great perspective. The issue is when you're not in a specific domain it can be hard to know how it should be done.
I ran into this situation a h handful of times. Figuring out nested attributes and how to pass them into the parent controller was "annoying" at first, but once I knew how Rails wanted it setup it was simple.
Another major point was some of the helpers for forms. Nested forms and how to get them setup was enough to make me second guess my entire decision. I was almost to the point of just manually 
writing out the forms in html. Lucky after some research on the docs I was able to figure it out. This one is a personal problem...I missed having static types. There was more then once dealing 
with fairly complex logic that I  messed up types and had to step through the logs to see what was going on.


## Conclusion

Ruby on Rails gets a lot of flack from the community. Most of the criticism are unjust and blown way out of proportion in my opinion. Using the correct tool for the requirements and the developer behind the tool is just, if not more important.
I've worked on technologies that you would expect to be more performance based on the stack, but the choices of prior developers were not great. At the end of the day most web applications
are just basic CRUD applications with business logic. Sure there are out lairs that need a higher performance stack or language like Go or Rust. Most of my personal projects that are in use are in either 
Dotnet or Go but if I find a small fit for a Rails application I would consider adding it to my small ecosystem.
