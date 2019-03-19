---
layout: post
title:      "Vinyl Vault - Final Project"
date:       2019-03-18 17:07:00 -0400
permalink:  vinyl_vault_-_final_project
---


![vinyl vault](https://raw.githubusercontent.com/trav15/trav15.github.io/master/img/vinyl-vault.png)
For my Final Project I chose to buid a CMS to keep track of a vinyl record collection. Users can add records with information such as artist, album title, cover image, and any notes (such as condition or where purchased). The project was a culmination of everything I've learned on this journey but focused on using React/Redux as a front-end framework and Ruby on Rails as an API server on the back end. 

I have to admit this project did push my learning and forced me to see where my understanding of the material wasn't as strong. I definitely had to spend many hours with my Google-Fu trying to work out problems that where coming up as I was building this out. 

One challenge I had on the CSS side of things was I chose to try out [Materialize CSS](https://materializecss.com/) instead of Bootstrap for the first time. To be more specific I used [React Materialize](https://react-materialize.github.io/) which had Material Design components using Materialize CSS. These premade components proved to be a bit cumbersome especially when using React Router with the Navbar as it would nest <a> tags within <a> tags which threw [an error](https://github.com/react-materialize/react-materialize/issues/706). After more Google-fu I learned this was a known issue and that you could use  NavLink from React Router with <li> to prevent that error. For future projects I would definitely try Materialize again but use Materialize CSS to really understand what gets abstracted by React Materialzie so I can have more control over it. I do like the design philosophy of Material Design so I hope to further explore and implement that in my future projects. 
