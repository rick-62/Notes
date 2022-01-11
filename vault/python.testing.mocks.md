---
id: U50rbDx35rbFscmmglIMR
title: Mocks
desc: ''
updated: 1641890189692
created: 1641889560814
---

## Intro
Mocks provide a way to interact with external systems during testing, without needing access the external system.

```python
from unittest import mock

# create mock object
m = mock.Mock()

# set an attribute
m.some_attribute

# set a function/method
m.some_attribute()

# set return value
m.some_attribute.return_value = 42
m.some_attribute()  # returns 42
```

## Side effect
However, the problem comes when trying to set a function as the return value to the attribute. 

Example:
```python

# any function
def print42():
    return 42

# set attribute return value to print42
m.some_attribute.return_value = print42

m.some_attribute() 
# call attribute from mocks - expecting the return value of 42
# does not resolve print42 function and prints function meta data instead

```
 







