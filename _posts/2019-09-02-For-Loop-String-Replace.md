
---
layout: post
title:  Replacing String Values with For Loops
date:   2019-09-02 13:32:20 -0600
categories: jekyll update
author: Carter Rees
tags: [python]
---

### Replacing string values with a for loop.

The data set below is at the subsidary unit of analysis. Misspellings are often part
of nested data, especially data that is scraped from the web. The code below creates a list of
values for the subsidary Micro, Inc. of Parent Company A and standadizes those values.

```python
import pandas as pd

df = pd.DataFrame(
    [['Parent Company A', 'Micro, Inc', 221], 
    ['Parent Company A', 'micro inc', 221], 
    ['Parent Company A', 'Micro, inc' , 221],
    ['Parent Company B', 'Poop Corp', 435],
    ['Parent Company B', 'Poop Corp', 435]],
    columns=['parent_company', 'subsidary', 
             'revenue_millions'])
  
# Print the data 
print(df)
```
<!-- make sure you put a line break before any table code otherwise it won't render on page -->

parent_company    | subsidary       | revenue_millions   
:------------:    | :-------------: | :------------:
Parent Company A  | Micro, Inc      | 221
Parent Company A  | micro inc       | 221
Parent Company A  | Micro, inc      | 221
Parent Company B  | Poop, Corp      | 435
Parent Company B  | Poop, Corp      | 435

```python
comp_a_sub_names = ['Micro, Inc', 'micro inc', 'Micro, inc']
for sub_names in comp_a_sub_names:
    df['subsidary'] = df['subsidary'].str.replace(sub_names, 'Micro, Inc.')

print(df)
```

parent_company    | subsidary       | revenue_millions   
:------------:    | :-------------: | :------------:
Parent Company A  | Micro, Inc.     | 221
Parent Company A  | Micro, Inc.     | 221
Parent Company A  | Micro, Inc.     | 221
Parent Company B  | Poop, Corp      | 435
Parent Company B  | Poop, Corp      | 435
