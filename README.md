
# Capstone Project


## Introduction

Wow - it's been quite a ride. Just a few weeks ago most of you hadn't used Python, and now you're importing, cleaning up and exporting data like a pro! In this final lesson, we're going to give you a couple of challenges to work on to pull things together. 

In the first, you'll import from a csv file and access information about the data set using various Pandas methods. In the second, you'll scrape information from another website and save the results to a csv. There will also be some time for more open Q&A and discussions about what to do next after completing the course.


## Objectives|
You will be able to:
* Import, examine, transform and save data from a variety of sources

## How are we Doing?

Lets start by taking a little bit of time to discuss how has the course gone? Take a few minutes to answer the following questions:
1. After the course, how specifically do you expect to use the skills you have learned during the course?
2. What skills that you have learned do you think will be particularly useful?
3. Are there any things we've covered that you do not think will be applicable? Which ones?
4. Are there any things you wish we would have had time to cover - and what would those things have allowed you to do at work that we've not provided you with the skills to work on?
5. What is one thing you could do in the next week that would start to use some of these skills to automate some of the work that you currently have to do manually?

Your instructor will facilitate the process of discussing your answers and providing feedback and thoughts on good next steps!

## Challenge 1 - csv Import & Exploration

Let's start with a fairly straightforward project. There is a file in this directory called `company-funding.csv`. It is is a listing of 1,460 company funding records reported by TechCrunch.

Start by reading the data into a dataframe, and examining it.


```python
# Your code here
```

OK, now answer the following questions *(write code in the boxes below, and fill out the "answer" comments)*:


```python
# How many different currencies were funds raised in?
# Answer: 
# What percentage of the raised were in USD?
# Answer: 

```


```python
# How many different states had at least one fund raising in this 
```


```python
# What was the average amount raised?
# Answer: 
```


```python
# What was the median amount raised?
# Answer: 
```


```python
# What percentage of the raises were in New York (state)?
# Answer: 
```


```python
# What was the average seed round raised in California?
# Answer: 
```


```python
# What were all of the different values for the "round" column?
# Answer: a, b, c, angel, seed, d, unattributed, debt_round, e
```


```python
# What is the average number of raises per company?
# Hint, check out the df.groupby() method
# Answer: 
```


```python
# What is the largest number of raises by any single company?
# Hint: the is a max() method
# Answer: 
```


```python
# What is the largest total amount of money raised by any one company?
# Hint: there is a sum() method
# Answer: 
```


```python
# Take all of the angel round deals and make them into seed rounds 
```


```python
# Take all of the seed and a rounds and make them "early stage" instead
```


```python
# In the modified dataframe, what percentage of the rounds left were "early stage" (seed or a) in New York?
# Answer: 
```


```python
# Finally, please save the results from the modified dataframe to a file called "funding2.csv"

# Then reopen the file, reading it into a new dataframe
# How many records does it contain?
# Answer: 
```

## Web Scraping Practice

Here's a chance to practice your web scraping skills. In this final section, you'll practice your scraping skills on a music website: https://www.residentadvisor.net. Start by navigating to the events page [here](https://www.residentadvisor.net/events) in your browser.

<img src="images/ra.png">

Next up, open the "inspect element" feature in your web browser in order to preview the underlying HTML associated with the page. 

Start by importing all of the methods you need and then loading all of the event listings into a collection called `event_listings`

Now iterate over the collection to load the Event_Name, Venue and Event_Date into a DataFrame:

And finally, save the results to a csv file called `events.csv`, and confirm you can read from the file into a new DataFrame.

## Summary

Congratulations! Thanks so much for taking the time to improve your skills. This course won't answer all of your questions or provide all of the skills that you need. The number of tools out there and the speed at which technology changes makes that impractical. But hopefully you'll be able to use what you have learned as a starting point for future exploration and improvements! Thanks so much for your time!

