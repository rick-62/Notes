---
id: U50rbDx35rbFscmmglIMR
title: Mocks
desc: ''
updated: 1645777652288
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
from unittest.mock import patch

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

### Patching decorator
Patching can alternatively be done with the help of a decorator.

```python
[...]

# decorator applied to entire function
@patch('os.path.abspath')

# first argument is now the the mock variable
def test_filepath(abspath_mock):
    relative_path = '../somefile.ext'

    # with statement now removed
    test_abspath = 'some/abs/path'
    abspath_mock.return_value = test_abspath
    assert filepath(relative_path) == test_abspath
```

Same can also be achieved for multiple patches at the same time.

```python
[...]

# two decorators applied
@patch('os.path.getsize')
@patch('os.path.abspath')

# second argument is added for the getsize mock
def test_filepath(abspath_mock, getsize_mock):
    relative_path = '../somefile.ext'

    test_abspath = 'some/abs/path'
    abspath_mock.return_value = test_abspath

    # fake size set as output for os.path.getsize
    test_size = 1234
    getsize_mock.return_value = test_size

    assert filepath(relative_path) == test_abspath
    assert filesize(relative_path) == test_size
```


### Immutable objects
Objects implemented in C are shared between the interpreter and require the objects to be immutable. Therefore it is not always possible to directly patch an object.

For example, if we were to attempt to patch the datetime now method `@patch('datetime.datetime.now')`, this would throw an error `TypeError: can't set attributes of built-in/extension type 'datetime.datetime'`.

There are ways to address this and start from the fact that importing or sub-classing an immutable object gives you a mutable _copy_.

```python
# patch now points to imported module
@patch('fileinfo.logger.datetime.datetime')
def test_log(mock_now):
    test_now = 123
    test_message = "A test message"
    
    # method "now" return value must be set at this point
    mock_now.now.return_value = test_now
    
    test_logger = Logger()
    test_logger.log(test_message)

    assert test_logger.messages == [(test_now, test_message)]
```

Could alternatively create an additional function to call the immutable object and reference from that, however, this requires changing source code. Best practise to avoid changing source code for testing. 










 







