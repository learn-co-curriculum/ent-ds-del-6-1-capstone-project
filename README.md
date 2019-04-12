
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
import pandas as pd
df = pd.read_csv('company-funding.csv')
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>permalink</th>
      <th>company</th>
      <th>numEmps</th>
      <th>category</th>
      <th>city</th>
      <th>state</th>
      <th>fundedDate</th>
      <th>raisedAmt</th>
      <th>raisedCurrency</th>
      <th>round</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>lifelock</td>
      <td>LifeLock</td>
      <td>NaN</td>
      <td>web</td>
      <td>Tempe</td>
      <td>AZ</td>
      <td>1-May-07</td>
      <td>6850000</td>
      <td>USD</td>
      <td>b</td>
    </tr>
    <tr>
      <th>1</th>
      <td>lifelock</td>
      <td>LifeLock</td>
      <td>NaN</td>
      <td>web</td>
      <td>Tempe</td>
      <td>AZ</td>
      <td>1-Oct-06</td>
      <td>6000000</td>
      <td>USD</td>
      <td>a</td>
    </tr>
    <tr>
      <th>2</th>
      <td>lifelock</td>
      <td>LifeLock</td>
      <td>NaN</td>
      <td>web</td>
      <td>Tempe</td>
      <td>AZ</td>
      <td>1-Jan-08</td>
      <td>25000000</td>
      <td>USD</td>
      <td>c</td>
    </tr>
    <tr>
      <th>3</th>
      <td>mycityfaces</td>
      <td>MyCityFaces</td>
      <td>7.0</td>
      <td>web</td>
      <td>Scottsdale</td>
      <td>AZ</td>
      <td>1-Jan-08</td>
      <td>50000</td>
      <td>USD</td>
      <td>seed</td>
    </tr>
    <tr>
      <th>4</th>
      <td>flypaper</td>
      <td>Flypaper</td>
      <td>NaN</td>
      <td>web</td>
      <td>Phoenix</td>
      <td>AZ</td>
      <td>1-Feb-08</td>
      <td>3000000</td>
      <td>USD</td>
      <td>a</td>
    </tr>
  </tbody>
</table>
</div>



OK, now answer the following questions *(write code in the boxes below, and fill out the "answer" comments)*:


```python
# How many different currencies were funds raised in?
# Answer: 3
# What percentage of the raised were in USD?
# Answer: 1458/1460 = 99.86%

df["raisedCurrency"].describe()
```




    count     1460
    unique       3
    top        USD
    freq      1458
    Name: raisedCurrency, dtype: object




```python
# How many different states had at least one fund raising in this 
df["state"].describe()
```




    count     1460
    unique      33
    top         CA
    freq       873
    Name: state, dtype: object




```python
# What was the average amount raised?
# Answer: $10,131,487.5
df["raisedAmt"].mean()
```




    10131487.5




```python
# What was the median amount raised?
# Answer: $5,500,000.0
df["raisedAmt"].median()
```




    5500000.0




```python
# What percentage of the raises were in New York (state)?
# Answer: 125/1460 
ny_raises = df.loc[df["state"] == "NY"]
print(len(ny_raises))
print(len(df))

# What was the average amount raised in New York?
# Answer: $7,121,480
print(ny_raises.raisedAmt.mean())

# What was the average amount raised in California?
# Answer: $10,723,235
ca_raises = df.loc[df["state"] == "CA"]
ca_raises.raisedAmt.mean()
```

    125
    1460
    7121480.0





    10723235.96792669




```python
# What was the average seed round raised in California?
# Answer: $877,821
ca_raises = df[df["state"] == "CA"]
ca_seed_raises = ca_raises[ca_raises["round"] == "seed"]
ca_seed_raises.raisedAmt.mean()
```




    877821.4285714285




```python
# What were all of the different values for the "round" column?
# Answer: a, b, c, angel, seed, d, unattributed, debt_round, e
df['round'].value_counts()
```




    a               582
    b               371
    c               141
    angel           135
    seed            128
    d                47
    unattributed     28
    debt_round       17
    e                11
    Name: round, dtype: int64




```python
# What is the average number of raises per company?
# Hint, check out the df.groupby() method
# Answer: 1460 raises / 909 companies = 1.6
groupby_company = df.groupby("company")
print(len(groupby_company))
print(len(df))
```

    909
    1460



```python
# What is the largest number of raises by any single company?
# Hint: the is a max() method
# Answer: 7
groupby_company = df.groupby("company")
groupby_company.count().raisedAmt.max()
```




    7




```python
# What is the largest total amount of money raised by any one company?
# Hint: there is a sum() method
# Answer: $495,700,000
groupby_company = df.groupby("company")
print(groupby_company.sum()["raisedAmt"].max())
```

    495700000



```python
# Take all of the angel round deals and make them into seed rounds 
df.loc[df["round"] == "angel", "round"] = "seed"
df["round"].value_counts()
```




    a               582
    b               371
    seed            263
    c               141
    d                47
    unattributed     28
    debt_round       17
    e                11
    Name: round, dtype: int64




```python
# Take all of the seed and a rounds and make them "early stage" instead
df.loc[df["round"] == "seed", "round"] = "early stage"
df.loc[df["round"] == "a", "round"] = "early stage"
df["round"].value_counts()
```




    early stage     845
    b               371
    c               141
    d                47
    unattributed     28
    debt_round       17
    e                11
    Name: round, dtype: int64




```python
# In the modified dataframe, what percentage of the rounds left were "early stage" (seed or a) in New York?
# Answer: 845 / 873 = 97%
ny_rounds = df.loc[df["state"] == "NY"]
print(len(california_rounds))
ny_seed_rounds = df.loc[df["round"] == "early stage"]
print(len(ny_seed_rounds))
```

    873
    845



```python
# Finally, please save the results from the modified dataframe to a file called "funding2.csv"
df.to_csv('funding2.csv')
# Then reopen the file, reading it into a new dataframe
# How many records does it contain?
# Answer: still 1460 - it worked!
df2 = pd.read_csv('funding2.csv')
len(df2)
```




    1460



## Web Scraping Practice

Here's a chance to practice your web scraping skills. In this final section, you'll practice your scraping skills on a music website: https://www.residentadvisor.net. Start by navigating to the events page [here](https://www.residentadvisor.net/events) in your browser.

<img src="images/ra.png">

Next up, open the "inspect element" feature in your web browser in order to preview the underlying HTML associated with the page. 

Start by importing all of the methods you need and then loading all of the event listings into a collection called `event_listings`


```python
import re
import pandas as pd
import requests
from bs4 import BeautifulSoup

response = requests.get("https://www.residentadvisor.net/events/us/newyork")
soup = BeautifulSoup(response.content, 'html.parser')

event_listings_collection = soup.find('div', id="event-listing")
event_listings = event_listings_collection.findAll('li')
print(len(event_listings), event_listings[0])
```

    113 <li><p class="eventDate date"><a href="/events.aspx?ai=8&amp;v=day&amp;mn=4&amp;yr=2019&amp;dy=12"><span>Fri, 12 Apr 2019 /</span></a></p></li>


Now iterate over the collection to load the Event_Name, Venue and Event_Date into a DataFrame:


```python
rows = []
for entry in event_listings:
    #Is it a date? If so, set current date.
    date = entry.find('p', class_="eventDate date")
    event = entry.find('h1', class_="event-title")
    if event:
        details = event.text.split(' at ')
        event_name = details[0].strip()
        venue = details[1].strip()
        rows.append([event_name, venue, cur_date])
    elif date:
        cur_date = date.text
    else:
        continue
df = pd.DataFrame(rows)
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Stavroz live! presented by Zero</td>
      <td>The Wiilliamsburg Hotel</td>
      <td>Fri, 12 Apr 2019 /</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Club Night Club presents: Pariah</td>
      <td>TBA - Brooklyn</td>
      <td>Fri, 12 Apr 2019 /</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ladyfag presents No Frills</td>
      <td>Kings Hall - Avant Gardner</td>
      <td>Fri, 12 Apr 2019 /</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Kindergarten with DJ Bus Replacement Service, ...</td>
      <td>Elsewhere</td>
      <td>Fri, 12 Apr 2019 /</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Quantic Residency with Darker Than Wax Plus Fi...</td>
      <td>Good Room</td>
      <td>Fri, 12 Apr 2019 /</td>
    </tr>
  </tbody>
</table>
</div>



And finally, save the results to a csv file called `events.csv`, and confirm you can read from the file into a new DataFrame.


```python
df.to_csv('events.csv')
new_df = pd.read_csv('events.csv')
new_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Stavroz live! presented by Zero</td>
      <td>The Wiilliamsburg Hotel</td>
      <td>Fri, 12 Apr 2019 /</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Club Night Club presents: Pariah</td>
      <td>TBA - Brooklyn</td>
      <td>Fri, 12 Apr 2019 /</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Ladyfag presents No Frills</td>
      <td>Kings Hall - Avant Gardner</td>
      <td>Fri, 12 Apr 2019 /</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Kindergarten with DJ Bus Replacement Service, ...</td>
      <td>Elsewhere</td>
      <td>Fri, 12 Apr 2019 /</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Quantic Residency with Darker Than Wax Plus Fi...</td>
      <td>Good Room</td>
      <td>Fri, 12 Apr 2019 /</td>
    </tr>
  </tbody>
</table>
</div>



## Summary

Congratulations! Thanks so much for taking the time to improve your skills. This course won't answer all of your questions or provide all of the skills that you need. The number of tools out there and the speed at which technology changes makes that impractical. But hopefully you'll be able to use what you have learned as a starting point for future exploration and improvements! Thanks so much for your time!

