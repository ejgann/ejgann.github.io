---
layout: post
title:      "JS/Rails Project: Quote Manager"
date:       2020-12-26 20:25:30 +0000
permalink:  js_rails_project_quote_manager
---


For my JS/Rails project, I created a dashboard to manage the professional quotes one receives for household projects. I have often found myself losing the quotes I've written down when companies called to give estimates. It would have been nice to have a single place to manage those quotes, not only for organizational purposes but also for comparison.

I wanted to be able to create new quotes for an already established project. So, a project `has_many` quotes, and a quote `belongs_to` a project. I created a Quote model and a Project model, plus the respective controllers. I wanted to be able to show only specific parts of my JSON data, so I created serializers for quotes and projects. It took a little while to grasp how to access the models and their attributes based on their relationships with one another, but eventually I was able to show a quote's associated project's information or do the reverse –– show all quotes for a single project.

After testing my Rails API and the resulting JSON data on my local server, I switched gears and began work on the JavaScript side of things. Since this project had to be a single-page application, that seemed to make things a bit easier for planning how I wanted to structure the data and components. 

I wanted to be able to show all active quotes that the user has, which I display in a table. To access that data, I wrote a GET fetch request that utilized the Quote Controller's index method. Since I also wanted the user to be able to add a new quote into the database, I also wrote a POST fetch request so that the information provided by the user –– the company's name and website, the quote amount, and the project to which it would associated –– could be stored into the database.

Since the project also required a third AJAX call, I initially wanted the user to be able to delete a quote (hypothetically, if they decided the quote was not within their project's budget or something). This proved to be too much of a time dump based on the fact that the quote's delete button was part of the template literal used when creating and displaying a quote. Instead, I use a different AJAX call; I created a GET fetch request for a user to be able to view all of a specific project's quotes (i.e. using the project controller's index method).

Once everything was working, I proceeded to the next step –– refactoring to incorporate object-oriented JavaScript (OOJS). The goal of OOJS, as I understand it, is to streamline the creation of new instances of a model and make it easier to access such data without having to use extraneous code. I separated the code relevant to quotes and also the code relevant to projects and placed them in separate files, linking them through the main JS file. This cleaned up the code quite a bit.

There is so much more that I would like to do for this project. I have several stretch goals that I plan to implement, but for now, I'm proud of my MVP.


