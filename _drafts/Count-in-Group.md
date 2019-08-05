---
layout: post
title:  Top Count within Groups
date:   2019-07-10 13:32:20 -0600
categories: [python, groupby]
author: Carter Rees
tags: [python]
---


import pandas as pd

df = pd.DataFrame(
    [['abc_company', 'azt56v', 'trav.com'], 
    ['abc_company', 'azt57e', 'trav.com'], 
    ['abc_company', 'azt58d', 'trav.com'],
    ['abc_company', 'azt58w', 'trapper.com'],
    ['abc_company', 'azt58o', 'trip.com'],
    ['def_company', 'azt59f', 'skitch.com'],
    ['def_company', 'azt59g', 'sack.com'],
    ['def_company', 'azt59n', 'trav.com'],
    ['def_company', 'azt5z', 'trav.com']],
    columns=['company', 'serial_no', 
             'domain'])
  
# Print the data 
print(df)
```
<!-- make sure you put a line break before any table code otherwise it won't render on page -->

name           | weight_lbs      | weight_lbs     | weight_lbs
:------------: | :-------------: | :------------: | :------------:
Jim            | 200             | 221            | 230
Todd           | 145             | 178            | 155
Bill           | 133             | 143            | 123
