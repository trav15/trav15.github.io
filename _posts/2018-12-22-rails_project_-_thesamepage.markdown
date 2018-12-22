---
layout: post
title:      "Rails Project - TheSamePage"
date:       2018-12-22 16:11:43 +0000
permalink:  rails_project_-_thesamepage
---


For my Rails project I wanted to create a CMS that would solve a real problem at my current day job as a cook in a restaurant kitchen. With 10+ dishes on the menu and many recipes for sauces and other prep things can get a little confusing when a recipe or dish is updated. With TheSamePage I wanted to be able to keep a running list of updates entered by the cooks or chefs so that everyone could see what the latest change to a recipe or dish is. That way everyone can be on THE SAME PAGE. 

So first thinking about my objects and their relationships I had two main ones and they were dishes and recipes. A dish like a Peking Duck and Biscuits has many recipes that make up its components like how to cook the duck, the duck seasoning blend, the dipping sauce, and how to make the biscuits. And each recipe like the biscuits can have many dishes like Biscuits and Gravy, Chicken Biscuit, etc. At first I thought that a recipe would belongs_to a dish but with the modularity of, for example, a sauce recipe to be used in another dish it fits better as a has_many relationship with dishes. On the users' side of things I did not want to have any user (a cook or chef) to have ownership over dishes or recipes so the belongs_to relationship is out for users and dishes. I do want chefs to have the ability to edit and create dishes and recipes whereas the cooks can only view them and suggest updates (would be similar to comments on a blog post).  
