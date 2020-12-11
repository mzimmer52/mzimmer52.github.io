---
layout: post
title:      "BeautifulSoup Best Practices "
date:       2020-12-10 23:09:42 -0500
permalink:  beautifulsoup_best_pracices
---

![](https://miro.medium.com/max/1560/1*-ZQxCcXWY0nhQms2vZYDKQ.jpeg)
## My Story

After having used BeautifulSoup multiple times to scrape information from various websites, there are some common issues that might arise due to a lack of experience or experimentation. These issues range from information not being included in a tag, errors resulting from trying to scrape information that doesn't exist, or extracting issues from JSON objects included in the HTML code. For each of these scenarios, there are fixes that may or may not be well-known, but for sure will help to alleviate any undue stress over the course of your journey experimenting with BeautifulSoup. 



## Scraping Information That is Not Present:

One of the most frustrating parts of web-scraping for me is that information that is on one page might not be in another. When you use a find() or find_all() method from beautiful soup on information that is not present, an error will be thrown and your program will crash. One of the most useful work arounds for this issue is to encorporate try and except blocks into your code. The beauty of try and except blocks when using BeautifulSoup is that information that is not found will not throw an error. Your program will continue to run, and basically skip over the section where it tried to scrape information that didn't exist. The syntax for a try and except block goes as follows:


try: 
     "code"
except: 
     "code"

	
Any code written below try will be the action that your program is trying to accomplish. If not error results from the "try" code, the except block will be passed over. However, if the try block results in an error, the code below "except" will be run. In terms of webscraping, it was most useful for me to include a pass statement under the except code, meaning that if the try block resulted in an error, the program would simply keep running. 

![](https://www.learnbyexample.org/wp-content/uploads/python/Python-try-except-Syntax.png)




## Finding Information That is not Included in Tags:

While most information on websites is usually included in tags with a specific class, there are sometimes instances where the information does not have a tag, or has an extremely broad tag that includes a large chunk of the HTML code. For instance, if a block of information is included in a "div" tag, it most likely also includes a lot of other information about the webpage. If a budget of a movie is included in the div tag as "Budget: $1,000,000", but has no class, there is an easy way to scrape this information using pythons built in split() method. 


If you "get text" from all the div tags in a specific HTML document, you can then use the split() method by inserting the string "Budget:" (  split("Budget:")  ) to split the text into everything to the left of "Budget", and everything to the right of "Budget:". The split method will output a list with  two elements (text to the left and right of "Budget:"). From here, you know the first bit of text in the text to the right of "Budget:" is the information you are looking for, and you can make sure of a multitude strategies in order to obtain the information you have been looking for the entire time, the $1,000,000. 




## Scraping Information From a JSON Object:

For me, the most efficient way to extract this sort of information from an HTML page is to firstly import the json the library. Atleast in my case, all the JSON objects I have ran into thus far have been included in a tag with a specific class. If this is the case, your code should look something like this :

1. source_code = requests.get(URL).text
2. parsed_code = BeautifulSoup(source_code, "html.parser")
3. json.loads(parsed_code.find('TAG', type='TYPE').string)

In the above block of code, URL is the url in which you are trying to extract information, and TAG and TYPE are the specifications of the JSON object. In BeautifulSoup 4, you must include ".string" at the end of this block of code instead of ".text". Including ".text" will result in a NoneType Object being returned , which can be frustrating as this change is very minimal, but necessary! 

Once the json object received, the specific data in the JSON object can be accessed just like accessing data from a dictionary. 


# Conclusion
The BeautifulSoup library in Python has helped to change the way people gather information from online. While it is an incredible tool that is relatively easy to use, there are nevertheless some issues that new coders might run in their first couple times webscraping through Python. While there are definetly more nuances to BeautifulSoup, there are certainly ways to work aroudn the three problems described above. I hope this can be of use to anyone currently running into issues with the BeautifulSoup library!














