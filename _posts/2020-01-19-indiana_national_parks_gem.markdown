---
layout: post
title:      "Indiana National Parks Gem"
date:       2020-01-19 16:37:59 +0000
permalink:  indiana_national_parks_gem
---


I chose to build my CLI Data Gem on a state that I am moving to. Growing up as a Boy Scout, I developed an affinity for nature. I enjoy going backpacking and camping within the wilderness, so I thought I would use this project as an opportunity to learn more about Indiana, and its National Parks.

At the start of my project, I had no clue how to get started. I didn’t know how to set up a Ruby Gem from scratch. After watching a lecture and a few other CLI Project videos, I was able to get the gist of creating a gem. Run the command bundle gem and the name of your gem and that gets a gem set up. Next, I created a file to run the program in the bin directory, gave it executable rights, and added a few object files to my lib directory: cli.rb, scraper.rb, and park.rb.

From there, it was all about bringing everything together. “I got this!” I thought to myself but instantly did not know how to start. I decided to start with my CLI object and build out what the user sees. This helped put everything into perspective.

Next, I wanted to scrape the data and instantiate park objects using that data. The scraping part was a bit difficult, but I was able to figure it out by reviewing some previous scraping labs. After I got my scraper to collect the information I needed, I created the park object. I already knew that a park would have 4 attributes: name, type of park, location, and description, so the park object was probably the easiest object to create of the three.

Lastly, it was time to use real data in the CLI, so I began to iterate through my park objects all class method and retrieve the data I needed from the @@all array. Once I have everything running and displaying as expected, I wanted to add some input validation to make sure that users wouldn’t be able to break my program with commands that are part of the program. This was harder than expected, but after a pair programming session with a few of the guys from my cohort, We were able to figure out the logic.

What I learned from this project is that even when I didn’t know how or where to start, just starting to build the gem, even when I was making mistakes, would lead to a scalable, object-oriented gem. Eventually, I will add in a “search parks by state” feature to my gem. I’m sure this will require adding a State object that has-many parks. Until then, enjoy learning about Indiana’s National Parks!
