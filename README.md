
# Capstone Project


## Introduction

Wow - it's been quite a ride. Just a few weeks ago most of you hadn't used Python, and now you're importing, cleaning up and exporting data like a pro! In this final lesson, we're going to give you a few challenges to perform to pull everything together. There will also be some time for more open Q&A and discussion around next steps. 


## Objectives
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

## Warm up #1 - csv import & exploration

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
# Answer: 

# What was the average amount raised in New York?
# Answer: 

# What was the average amount raised in California?
# Answer: 

```


```python
# What was the average seed round raised in California?
# Answer: 
```


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
# What is the aveage number of raises per company?
# Answer: 

```


```python
# Which company had the largest number of raises?
# Answer: 

```


```python
# Which company raised the largest amount of money?
# Answer: 

```


```python
# Take all of the angel round deals and make them seed rounds from the dataframe
# Answer: 

```


```python
# Remove all of the debt_rounds and unattributed rounds from the dataframe
# Answer: 

```


```python
# In the modified dataframe, what percentage of the rounds left were "early stage" (seed or a)?
# Answer: 

```


```python
# In the modified dataframe, what percentage of the dollars raised were "early stage" (seed or a)?
# Answer: 

```


```python
# What is the aveage number of raises per company?
# Answer: 
```

## Warm up #2 - working with free text




## Summary

Congratulations! Thanks so much for taking the time to improve your skills. This course won't answer all of your questions or provide all of the skills that you need. The number of tools out there and the speed at which technology changes makes that impractical. But hopefully you'll be able to use what you have learned as a starting point for future exploration and improvements! Thanks so much for your time!

