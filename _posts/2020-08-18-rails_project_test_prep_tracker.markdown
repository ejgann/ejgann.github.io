---
layout: post
title:      "Rails Project: Test Prep Tracker"
date:       2020-08-18 18:48:27 +0000
permalink:  rails_project_test_prep_tracker
---


I have a few acqaintances who have recently started studying for graduate and professional exams, such as the GRE and LSAT. So, my rails project idea, a test prep tracker, was inspired by them. 

## What is it?
![](https://i.imgur.com/6SIlZ3Z.png?2)

My Test Prep Tracker app allows a student to track their test prep activities and log practice sessions. He/she can identify how much time is required for, say, a flash cards session and then log a practice session of the flash cards and rate/comment on it to note how well they did and how they can improve for next time.

## Architecture and models
Once a user signs up and/or logs in, he/she will be directed to a dashboard where they can access one of three models: Tests, Practices, and Activities. Tests is where they can identify the test for which they are preparing and the test date. Activities is where there is a list of pre-existing study activities, such as flash cards, study groups, tutoring, etc., from which they can select. Each activity has an estimated "time required" field and also a description of what it is. Practices are where the user can log their completion of a specific study activity, including the date of the practice, their rating of their performance of the activity session, and any comments they wish to note.

The models are associated as follows:

Test >-- User --< Practice >-- Activity

![](https://i.imgur.com/vAz5DwN.png?2)

## Process
I had a few false starts with this app. When instructors or others tell you to plan carefully, they aren't joking! I would draw out what I thought was a solid schema, including attributes, relationships, etc., only to realize later on that I had not considered extensively enough how two models' relationships would impact the functionalities that I wanted to include.

After creating the initial new app and linking it to my Gitub repository, I set out to generate the resources associated with each model. Once all of the resources were created, I went into each model file to set up the associations among them. Next came the routes file where I specified any initially known nested resources.

![](https://i.imgur.com/YjwOUhg.png?2)

I wanted to start by building out the signup, login, and logout functionalities so I created the appropriate routes first. Then, in the users_controller, I created the signup actions, followed by the login-related actions in a separately created sessions_controller. It was then time to create the related view files for the users and sessions controllers to access, including a form partial through which users could sign up. After some small errors here and there, things began to align, and I experienced my first bit of success with this app. Now it was time to start on the core functionalities.

To start this portion, I decided to build out the Test model first since it was a fairly compact resource. Next came the Activity model since, along with the User model, it would be required to be in place before building the join table, Practices. When I initially started this project, it was at this point that I [royally] messed up since I had not sufficiently thought out my schema. I had to toss my work and start over with some newly configured models with different relationships. Even when you think you have taken everything into consideration, go through it again!

After tackling the nuts and bolts of the controller actions getting them to talk to the view files, I took a break from back-end things and switched gears to work on the app's styling. I had previously been exposed to html and CSS, so this part came a little easier. There are so many ways you can style something that I think it sometimes makes me have "analysis paralysis" over which styles to employ. The final product is not nearly as styled as I would normally have it, but I wanted to finish this project and not waste any more time than I already had.

Getting back into the back end development, I launched myself into the world of scope methods. I would have liked to have employed more scope methods than I did, but that is something that will have to come later. The method I did use was to order the user's activities#index view by their most popular (i.e. most often completed) activities.

## Concluding thoughts
Writing about this experience and reflecting on how I accomplished this project made me revisit the blood, sweat, and tears I'd experienced along the way. I spent a lot of time reviewing, experimenting, consulting videos, and reading the documentation. I feel like I took a lot longer than the average person to complete this project, but I wanted to really understand every bit of what I was doing. I have a growing list of things I want to add to and change about this app. For now, however, I'm proud of my work.

