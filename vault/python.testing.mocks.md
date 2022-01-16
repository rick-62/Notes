---
id: U50rbDx35rbFscmmglIMR
title: Mocks
desc: ''
updated: 1642364002265
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

## Asserting calls

```python
class MyObj():
    def __init__(self, repo):
        repo.connect()

from unittest import mock
import myobj

def test_connect():
    external_obj = mock.Mock()
    myobj.MyObj(external_obj)
    external_obj.connect.assert_called_with()
```

This would pass the test as the mock in this case is simply recording what it was called with, using the `assert_called_with()` method. 

It is also possible to pass the expected arguments e.g. `assert_called_with(t=10, x="string")`. In the above example this would fail as the argument was actually called with no arguments. 

There are other methods and attributes mock provides:
- `assert_called_once_with`
- `assert_any_call`
- `assert_has_calls`
- `assert_not_called`
- `call_count`
- etc...

## Patching
Patching essentially intercepts known function calls and replace the return value.

This can be useful when we know the value will change dependent on external factors, which do not depend on our code. The downside to patching is the test is no longer pure and relies on knowing upfront which callable return value will require patching.

```python
import os

def filepath(relative_path):
    return os.path.abspath(relative_path)

def test_filepath():
    relative_path = '../somefile.ext'

    # patch externally dependent callable and test within with block
    with patch('os.path.abspath') as abspath_mock:

        # fake absolute path
        test_abspath = 'some/abs/path'

        # set new output for os.path.abspath
        abspath_mock.return_value = test_abspath

        # when os.path.abspath called returns 'some/abs/path' instead
        assert filepath(relative_path) == test_abspath
```










 







