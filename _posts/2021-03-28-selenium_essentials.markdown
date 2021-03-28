---
layout: post
title:      "Selenium Essentials"
date:       2021-03-28 15:12:39 -0400
permalink:  selenium_essentials
---


![](https://miro.medium.com/max/817/1*nxIlcc-RJSOq_PgE5GMo0A.png)


While gathering the data for my capstone project, I ran into an initial issue. When trying to gather the relevant data from the tables on crossfit.com, I kept getting error messages due to the information in the table being updated using javascript. I used the python library, Selenium, in this project to webscrape due to its ability to handle the javascript, and interact with a website without actually using your mouse. 

Because each page of crossfit.com only showed information and scores for 50 competitors, in order to gather 20,000 rows of data (my initial goal), I had to find a way to automate a loop that would read in 50 rows, and then click the "Next" button at the bottom of the website in order to gather the next 50 rows of data. Adding on, the data I was trying to gather for each row came in two seperate parts, each one being hidden in a different part of each competitor's designated section. In the end, I realized I had to gather one section of the information from all 50 rows, go back up to the beginning of the webpage, gather the other section of information for all 50 rows, and then have selenium click the "Next" button to proceed to the next page. 

![](https://www.netwoven.com/wp-content/uploads/2020/06/Use-of-Selenium-other-than-Software-Testing.jpg)

The first major tip I would give to anyone using selenium is to make sure that when trying to press any button to make sure that the button is actually visible in the webpage. For example, the first couple times when I tried to press the "Next" button to grab more information from the next web page, I would receive an error. What ended up fixing this issue was having the webpage scoll to a specific location where the button was visible. Only then, would an error message not come up. The code for scrolling to a specific location would look something like this:

`driver.execute_script("window.scrollTo(X, Y)")`

Another tip I would give anyone starting Selenium would be to make use of the time library, specifically when interacting with multiple webpages. One thing I didn't understand at first when navigating to new websites was why I would get errors after clicking certain buttons that lead to new websites. I ultimately found out that the error messages were due to Selenium trying to grab specific information before a website had fully finished loading, meaning specific information would not yet be available to scrape. A good solution for this was to make your program/loop wait a couple seconds after navigating to a new webpage to ensure that everything had finished loading. Making use of the time library, I used code along the lines of:

`time.sleep(# of seconds)`

Lastly, as always for any webscraping project, I would highly recommend taking advantage of "try" and "except" statements. Information from websites can be unpredictable, and you may never know when you are trying to access information that isn't there. Instead of crashing your program, you can tell your program exactly what you want it to do when encountering a certain error (trying to access information that isn't there) under the except block. For example, inserting a "pass" statement under the except block will simply keep your code running without throwing a dreaded error message. 

All in all, Selenium is a very powerful library that can automate many tasks when navigating through webpages, thereby saving much time and effort. If the following tips are followed, selenium can help any aspiring data scientist create large datasets in limited amounts of time, and ensure that the data collection process does not consume the majority of effort for a given project. 











