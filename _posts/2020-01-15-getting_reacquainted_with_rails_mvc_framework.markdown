---
layout: post
title:      "Getting Reacquainted with Rails MVC Framework"
date:       2020-01-16 01:51:17 +0000
permalink:  getting_reacquainted_with_rails_mvc_framework
---


I took a bit of a break from coding over the past month and am now diving back into it. As such, Rails is back on my repertoire, which means I am getting reacquainted with the MVC framework. As I review this for myself, I thought it might be helpful to capture in a blog post what I'm reliving...er, remembering.

## What is MVC?

Let's say that one is wanting to do just about anything online. To whittle down the possibilities, let's say that this person is interested in shopping online at [chewy.com](http://chewy.com) to find their dog, Gus, a new sweater. After typing the the address into the address bar and hitting "enter", the client (i.e. the computer this person is using) sends a HTTP request to the server used by Chewy's website. In turn, the server responds by loading the website's HTML.

Okay, great, you may be saying. But, what does that have to do with the MVC framework? Well, this whole HTTP request-response process is the MVC at work. Let's pause on sweater-shopping and look a little more in depth at the MVC components. 

MVC stands for "Model View Controller". Each item is a separate component of the framework that does it's own thing but then contributes to the work of the whole framework. From a high level, this framework enables developers to divide the work in a web application among these three different components, each with a singular area of focus: 

- **Models** most readily work with database information (in this case, database information of Chewy's products). Our model is linked to the specific database table that houses all of the dog sweaters sold by Chewy and accesses the sweaters based on our filtered search criteria.
- **Views** are strictly responsible for the visual presentation of the information to the user. They come into play when we as users actually see the results of our search for dog sweaters. Everything from how the page is arranged to the number of sweaters shown on a single page is dictated by the view files.
- **Controllers** serve as the intermediary between the logic/data portion (model) and the interface of the application (view). The controller files orchestrate the entire operation....everything from the model's database query to the parsing of query data to how the view renders. Neither the view nor model do anything unless given the greenlight by the controller.

The separation of these functions from one another is referred to as the "single responsibility principle", also called the "separation of concerns". Each component of the framework should only be tasked with doing its own work and not overlap with any other component.

This separation of powers, so to speak, is literal –– each component exists in its own Ruby file or set of files. 

So, back to Gus's sweater...

Gus's owner has typed into the search bar on Chewy's website "dog sweater". The controller picks this up and solicits the model files to pull all sweaters matched as belonging to dogs from the database. Once that has been done, the controller then directs the view file to take the database query results and show them in the format and style specified by the view files' code. The controller ensures the view renders as it should so that Gus's owner can select from among the options.

## Conclusion
This is a very, very simplistic overview of the MVC process in relation to HTTP requests and responses. As I dig in more, I may add to this in a later blog post. Thank you for reading!






