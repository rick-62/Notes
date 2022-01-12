---
id: U50rbDx35rbFscmmglIMR
title: Mocks
desc: ''
updated: 1641972842018
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

## Complex return values (side_effect)
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

To resolve this issue, mock also has the `side_effect` attribute, which accepts callables, iterables, and exceptions, changing behaviour accordingly.

- if an exception is passed the mock will raise it
- if an iterable is passed the mock will yield the results of the iterable
- if a callable is passed the mock will resolve it

```python
m.some_attribute.side_effect = range(3)

m.some_attribute()  # 1
m.some_attribute()  # 2
m.some_attribute()  # 3
m.some_attribute()  # StopIteration exception


# any function
def print42():
    return 42

m.some_attribute.side_effect = print_answer
m.some_attribute()  # 42
```


 







