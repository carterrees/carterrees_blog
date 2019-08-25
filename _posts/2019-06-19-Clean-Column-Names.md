---
layout: post
title:  Cleaning Column Names with Regex
date:   2019-06-19 13:32:20 -0600
categories: jekyll update
author: Carter Rees
tags: [python]
---

#### Renaming multiple columns with a for loop.

Column names can be messy and full of junk characters. I like underscores to separate words
and everything lowercase.
This is a quick general cleaning script to deal with most situations.


```python
# Python code demonstrate how to create  
# Pandas DataFrame by lists of lists. 
  
import pandas as pd

df = pd.DataFrame(
    [['Jim', 200, 221, 230], 
    ['Todd', 145, 178, 155], 
    ['Bill', 133, 143, 123]],
    columns=['First.Name', 'countS', 
             'weight.lbs', 'shoe-size-mm'])
  
# Print the data 
print(df)
```
<!-- make sure you put a line break before any table code otherwise it won't render on page -->

First.Name     | countS          | weight.lbs     | shoe-size-mm
:------------: | :-------------: | :------------: | :------------:
Jim            | 200             | 221            | 230
Todd           | 145             | 178            | 155
Bill           | 133             | 143            | 123


```python
df.columns = df.columns.str.replace('[^0-9a-zA-Z]+', '_').str.lower()

print(df)
```

first_name     | count           | weight_lbs     | shoe_size_mm
:------------: | :-------------: | :------------: | :------------:
Jim            | 200             | 221            | 230
Todd           | 145             | 178            | 155
Bill           | 133             | 143            | 123

