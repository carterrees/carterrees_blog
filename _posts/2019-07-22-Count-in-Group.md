---
layout: post
title:  Top Count within Groups
date:   2019-07-10 13:32:20 -0600
categories: [python, groupby]
author: Carter Rees
tags: [python]
---

The data set below is at the product serial number unit of analysis. A company can have multiple
serial numbers assigned to web domains. I would like to return a data set that 
captures the domain that shows up most often within each company.

```python
import pandas as pd

df = pd.DataFrame(
    [['abc_company', 'azt56v', 'trav.com'],
    ['abc_company', 'azt57e', 'trav.com'],
    ['abc_company', 'azt58d', 'trav.com'],
    ['abc_company', 'azt58w', 'trapper.com'],
    ['abc_company', 'azt58o', 'trip.com'],
    ['def_company', 'azt59f', 'skitch.com'],
    ['def_company', 'azt59g', 'sack.com'],
    ['def_company', 'azt59n', 'sack.com'],
    ['def_company', 'azt5z', 'sack.com'],
    ['ghi_company', 'azt64a', 'punk.com'],
    ['ghi_company', 'azt64b', 'skip.com'],
    ['ghi_company', 'azt64c', 'blerp.com']],
    columns=['company', 'serial_no',
             'domain'])
  
# Print the data 
print(df)
```
<!-- make sure you put a line break before any table code otherwise it won't render on page -->

company           | serial_no       | domain     
:------------:    | :-------------: | :------------:
abc_company       | azst56v         | trav.com  
abc_company       | azt57e          | trav.com
abc_company       | azt58d          | trav.com
abc_company       | azt58w          | trapper.com
abc_company       | azt58o          | trip.com
def_company       | azt59f          | skitch.com
def_company       | azt59g          | sack.com
def_company       | azt59n          | sack.com
def_company       | azt59Z          | sack.com
ghi_company       | azt64a          | punk.com
ghi_company       | azt64b          | skip.com
ghi_compamy       | azt64c          | blerp.com


```python
def get_top_domain(g):
    return g['domain'].value_counts().idxmax()
    
top_domain = df.groupby('company').apply(get_top_domain).to_frame().reset_index()
top_domain.columns = ['company', 'top_company_domain']

print(top_domain)

```
<!-- make sure you put a line break before any table code otherwise it won't render on page -->

company              | top_company_domain
:------------:       | :------------:
abc_company          |trav.com
def_company          |sack.com
ghi_company          |blerp.com


The domain with the highest count is returned and represents the domain with the highest number
of associated serial numbers. Note that the ghi_company returned the domain that is first in 
alphabetical order given each domain has one serial number.
