---
layout: post
title:      "Scraping the DC Michelin Guide"
date:       2018-10-21 15:26:59 +0000
permalink:  scraping_the_dc_michelin_guide
---

For my CLI project I took some inspiration from the [World's Best Restaurants](https://github.com/cjbrock/worlds-best-restaurants-cli-gem) example that scrapes the San Pelligrino sponsored World's 50 Best Restaurants website and gives it a CLI interface and display. 

But since I live in Washington, DC I decided to scrape the [Michelin Guide](https://guide.michelin.com/us/washington-dc/) to provide a CLI interface and display of One Star, Two Stars, Three Stars, and Bib Gourmand restaurants. This proved to be a little more difficult to scrape than the World's 50 Best list but it at the end of it using Nokogiri finally became an enjoyable experience. 

At first this project seemed daunting because up until this point there was a lot of hand-holding and then all of a sudden I was left to my own devices, alone. But I really wasn't alone, having a good explanation of the project, Avi's video lectures, Section Leads, and Project support sessions available. And so, feeling like there were people who had my back, I dove right into coding the CLI interface as I followed along with Avi's example, stubbing out functionality and hard-coding some data just to get a bare-bones app up and running. And in the immortal words of Avi Flombaum:

![Avi Write The Code](https://i.imgur.com/2U78zQX.png)

And this proved to be a good way to get started and build out the application, revealing to me the interaction with the CLI and kinds of data I would need. And once I got it up and running I felt great and had motivation to push on through to the tough stuff.

![CLI](https://i.imgur.com/6HE22dY.png)
![Fake It TIll You Make It](https://i.imgur.com/30LkAzw.png)

And so the real meat and bones of the application had to be dealt with. Breaking down the functionality and what Classes I would need helped me to think and the methods encapsulated within that would do the work and handle the data.
```
class DCMichelinGuide::Scraper
  #get page
  #scrape page to create list of restaurants
  #make Restaurant instances for each restaurant on the list
	
class DCMichelinGuide::Restaurant
  attr_accessor :name, :url, :cuisine, :location, :distinction, :classification, :price, :services, :mpov, :hours, :website
	
class DCMichelinGuide::CLI #Our CLI Controller
  def call
    list_distinctions
    show_list
    menu
    resto_choice
    goodbye
  end	

```

Working through all of this really reinforced my learning up to this point. It forced me to think about how each Class related to each other and what my code is doing. Initially I was dreading Nokogiri as the html you see when you inspect a page can look like mumbo jumbo but when I had to really face Nokogiri I began to see its virtues and understand it as a tool rather than a scary weapon. 

![Scraping](https://i.imgur.com/1raKhFH.gif)

And in fact it even became fun scraping my pages and seeing how it worked and how to get the data I wanted. Without getting into the nitty gritty with it I would have never felt this comfortable utilizing it for future applications. Once I got the data I wanted it was another challenge to strip out all the stuff I didn't want (like whitespace and /n). Googling my issue and learning about strip, strip!, chomp and gsub methods helped to push me along. After I had the data I wanted in the form I wanted it was just a matter for displaying the data on the CLI and making my interface robust with input and menu navigation. And for me I thinking writing control flow is fun because you think about the different inputs or cases and what happens in each case:
```
  def get_page(input)
    if input == 1
      url_fragment = "1-star-michelin"
    elsif input == 2
      url_fragment = "2-stars-michelin"
    elsif input == 3
      url_fragment = "3-stars-michelin"
    elsif input == 4
      url_fragment = "bib-gourmand"
    else
    end
    Nokogiri::HTML(open("https://guide.michelin.com/us/washington-dc/#{url_fragment}/restaurants"))
  end
```
Now, at the end of this project, I have a working CLI application that checks all the boxes in requirements and I'm glad that I've worked through it all. The process has reinforced my learning and brought up a lot of questions that I was able to find the answer to and come out that much better at the end of it. What once was scary and daunting is now friendly and welcoming. 

![BYE](https://i.imgur.com/VkC7soI.png)


