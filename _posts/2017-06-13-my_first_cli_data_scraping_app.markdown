---
layout: post
title:  "My first CLI Data Scraping App"
date:   2017-06-13 21:33:37 +0000
---


Today I have finished my CLI Data Gem Project. I am so proud I reached this milestone and finally was able to implement all the knowledge I had been getting during past months. The fact that all the experience of working on labs collapsed in this project gave me some sense of completeness. 

I expected the idea of starting my own project from scratch to be the most challenging thing. However, in my case it was about learning to feel comfortable facing the errors and finding out new ways to debug. Using such tools as ‘rake’ and ‘pry’ helped a lot. At some point I stopped minding having errors and thinking how long it took me to solve them, as couple of months ago I even would not be able to write any code to fix it! 

The reason why it was way easier to debug having prewritten tests was not only because they tell you exact expectations, but also because the tasks themselves are already designed for you. And sometimes I found myself finishing labs and wondering what was going to happen next – okay, this method returns a modified array, all tests pass, so? In ‘best-dogs-for-apartments-cli-data-project’ I was completely responsible for my own code. Designing phase was the most difficult yet exciting. I would say the concept of OO Ruby makes sense to me, although being able to use all it’s capacity requires practice and creativity. 

By now for this purpose I used pen and paper to think of collaborations between several classes, their quantity, where it was necessary to create actual instances, and where not etc. As far as in Ruby there are pretty much only variables and methods, in other words, data and functionality, I decided to initiate instances in a class, which was responsible for storing information, while classes, which were built in order to add actions to the app (ie, retrieving data, interacting with user) did not need to have instances. In this project this approach helped me to find a solution for this dilemma. Please, feel free to check my github and dive into details.

https://github.com/laramontana/best-dogs-for-apartments-cli-data-project

