---
layout: post
title:      "Setting Up Your Rails Project in Github"
date:       2020-06-17 18:38:37 +0000
permalink:  setting_up_your_rails_project_in_github
---

In the early months of my time in Flatiron's software engineering program, Github scared the heck out of me. I had nightmares of inadvertently deleting things or diong other things with unintended consequences. One of the early problems I encountered was correctly setting up a new Rails project and linking it to my Github repo. Also, if I created files in a certain order, I had several problems later when I tried to connect my project to my Github account.

[Cue a blood-curling scream]

Now that I'm about to start my Rails project, I am taking the bull by the horns and am wrestling (or "wrasslin'" if you're from Oklahoma like me) this beast into submission.

## 1. Where will your project files live?
First, decide where on your computer you want your project files to live. For instance, I have been storing all of my Flatiron assignments in a folder called "code" within the Development folder on my computer. So, from my terminal, I "cd" (or "change directory") into my "code" folder within the Development folder.

## 2. Create your Rails project
From your terminal, create your Rails project.

```
$ rails new YourProjectName
```

## 3. Create a new repo in Github
Head over to `github.com/new` (you'll need to be logged into your account). 
![](https://imgur.com/WA29s4u)

Type in the name of your respository (I retain the name of my project for simplicity's sake). You can add a description if you want to. Select whether your repo will be public or private (public is the default). I personally do not check the box "Initialize this repository with a README" since the rails generator automatically creates one for us. I also select "None" for both the "Add .gitignore" and "Add a license" dropdowns. Click on "Create repository".

## 4. Connect your project to your new Github repo
After you create your repo, the next screen will show steps for how to set it up. Since you've just created a new repo, you'll want to follow the instructions for "...or create a new repository on the command line". In your terminal, change directories to the one that houses your new project. One at a time, run the following commands:
```
git init
git add .
git commit -m "My first commit."
git remote add origin git@github.com:yourname/yourprojectname.git
git push -u origin master
```

And voila!! You're in business.

Whenever you make changes to your project from this point forward, you will want to commit your changes frequently (emphasis added on frequently). Commits are the lifeblood of your project in Github, and it can make the difference if something really goes wrong and you need to revert to a previous version of your project. To make commits, you will type the following into your terminal:
```
git add .
git commit -m "Revamped the login views"
git push
```

Happy coding! Commit often!
