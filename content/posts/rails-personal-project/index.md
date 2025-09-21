+++
title = 'Rails Personal Project'
date = 2025-08-07T21:06:17-06:00
draft = true
+++

## Prototyping With Rails

About a year ago I hand to step back into my family business due to a death. During that time I was operating the business while trying to figure out a new owner I was looking at trying to stream line a process that had a pain for many years.
It was a fairly simple problem to solve and I had used multiple CRMs geared towards our industry, but none of them had this one feature. So what did I do? I decided prototype an application to see solve my frustration. As a business owner...terrible idea, but as a programmer..typical!
Normally, I would reach for my normal dotnet stack, but I wanted to try out the new Rails 8. This has been the inspiration for the recent Rails posts, and now I want to share the project.


### Ignite Studio

This application was pretty simple and was focused around one core feature. It was a small CRM meant for marital arts studios to track students. The main feature was to stream line the process tracking student ranks.
When a testing event happened it digitalized the scoring process and would auto advance the student's rank if they passed. This process manually done was not hard, but it took time and was prone to simple mistakes. 

#### Core Stack

I wanted to keep the stack fairly simple and use as many built in features that ships with Rails 8. This was just a prototype

- Rails 8
  - Built in Authentication
- Solid Que for jobs
- Bootstrap 5

## Thoughts

It's been a few years since I properly dove into a full applications and it took a bit to get back into it. One of the main things I truly enjoy about Rails is the convention over configuration principle. Coming from Dotnet the configuration setup can sometimes get ecessive. 
I worked on the same teams with multiple project and each one of them have different configuration setups for the same thing. Sure, you could point that out as tech debt or a skill issue - but it's way more common then what people would like to admit.

Active Record's method and how to query for data is similar to Entity Framework, but just different enough to get enough "gotchas". This has a lot to do with ruby vs c# syntax, but context switch was just enough to where I had to repeatidly look up the docs in Active Record or a stack overflow post...maybe even ask ChatGPT
I did find myself wishing the Active Record has a little bit more flexibility as Entity Framework for more complex relationship setups. To be fair, it probably does and my limited experience was hindering my use of the tool.

Deploying with Kamal was amazing and I wish dotnet had a companion. It was refreshing being able to setup a "simple" script and be able to locally deploy my code to anywhere that had an ssh connection. I'm use to using Github Action and Azure Devops Pipelines with yaml files.
While at some abstract level both of these do the same thing, Kamal gives so much more control back to the user. Plus 
