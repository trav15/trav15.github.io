---
layout: post
title:      "Rails Refactor or Renaming Rusty Rails Rendezvous"
date:       2018-12-22 11:11:44 -0500
permalink:  rails_project_-_thesamepage
---


So as I started my Rails Project I had my models sketched out and thought I had some good names in place. The project I was building was called LendingLibrary and I so I thought the join table could be a "lend", the noun version of lending and I did want to separate my project from a monetary loan application. But after I got deeper and deeper into the project I began to realize that "lend" and "lends" weren't good names for my model as I found myself using the word "loan" to describe to index of all a user's borrowings (yeah, that doesn't sound good either). Just look how weird the nested route looks to how I say it in plain English, might I say RESTless even.

![Nested Route](https://i.imgur.com/NXTLM94.png)

But I was so deep in the jungle of my project to try and manually rename everything, I feared. Starting a new rails project was an option albiet a start from scratch approach. And then I thought of my commits! Oh my hard earned commits showing just how I built this thing with my own two hands, brick by brick. And so I sought the wisdom of the Google.  And of course there was a solution because yes, people have made this kind of mistake before. After all to err is human.

![To Err Is Human](https://i.imgur.com/GCX2yql.jpg)

Behold [Rails Refactor](https://github.com/jcrisp/rails_refactor) on Github. Actually, thank you to Fatos Morina for his [blog post](https://www.fatosmorina.com/rename-rails-controllers-views-migrations-rails-refactor/) that demonstrated the power of the Gem. With a couple commands you have have your Model and Controller renamed just like that. Of course there is a fair amount of hunting down any loose ends like your DB migrations. Here is a bit from the readme to illustrate the changes it was automating for me:

To rename a controller: $ rails_refactor rename OldController NewController 
* renames controller file & class name in file
* renames controller spec file & class name in file
* renames view directory
* renames helper file & module name in file
* updates routes

To rename a controller action: $ rails_refactor rename DummyController.old_action new_action
* renames controller action in controller class file
* renames view files for all formats

To rename a model: $ rails_refactor rename OldModel NewModel
* renames model file & class name in file
* renames spec file & class name in file
* renames migration & class name & table names in file

So it was a big lifesaver for me and saved any more anxiety about cleaning up my project. A weight has been lifted so I felt I had to share this. And reading from the creator [James Crisp's blog](https://jamescrisp.org/2010/11/27/rails-refactor-hack-night/) it appears he started the project for Rails Refactor as part of a hack night. That's the beauty of hack nights and the community it can foster in real life as well as online. Gets me excited to get better and participate and see what I can contribute to in the future! Thank you, [James Crisp](https://jamescrisp.org) and [Ryan Bigg](https://ryanbigg.com/) and anyone else who may have contributed! Hopefully once I get more experience I can help improve or update this Gem!
