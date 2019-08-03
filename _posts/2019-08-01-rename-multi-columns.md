---
layout: post
title:  Rename Multiple Columns
date:   2019-08-01 13:32:20 -0600
categories: jekyll update
tags: [python]
excerpt_separator: <!--more-->
---
#### Renaming multiple columns with a for loop.

Below I demonstrate how to rename multiple columns in a sequence using a for loop in Python. <!--more-->
I often seen longitudinal data stored this way inclusive of the poor naming convention. I assume the columns
are in the proper order and want to add a numerical sequenced index to the column name.


```python
# Python code demonstrate how to create  
# Pandas DataFrame by lists of lists. 
import pandas as pd 
  
import pandas as pd

df = pd.DataFrame(
    [['Jim', 200, 221, 230], 
    ['Todd', 145, 178, 155], 
    ['Bill', 133, 143, 123]],
    columns=['name', 'weight_lbs', 
             'weight_lbs', 'weight_lbs'])
  
# Print the data 
print(df)
```
<!-- make sure you put a line break before any table code otherwise it won't render on page -->

name           | weight_lbs      | weight_lbs     | weight_lbs
:------------: | :-------------: | :------------: | :------------:
Jim            | 200             | 221            | 230
Todd           | 145             | 178            | 155
Bill           | 133             | 143            | 123


```python
cols = df.columns.tolist() 
df.columns = cols[:1] + ['weight_lbs_%i' % i for i in range(1, len(cols[1:])+1)]

print(df)
```

name           | weight_lbs_1      | weight_lbs_2     | weight_lbs_3
:------------: | :-------------: | :------------: | :------------:
Jim            | 200             | 221            | 230
Todd           | 145             | 178            | 155
Bill           | 133             | 143            | 123

