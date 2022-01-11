---
id: 9WCro6jjiIP1agBapobm2
title: Pytest
desc: ''
updated: 1641756437443
created: 1641755735575
---

## Parametrize
Test multiple different inputs within the same test function/class.

```python
@pytest.mark.parametrize(

    # argument names
    [arg1_name, arg2_name, ...],  

    # argument values
    [
        (arg1, arg2, ...),  # test 1
        (arg1, arg2, ...),  # test 2
        (arg1, arg2, ...),  # test 3
    ]

)
```

## Exceptions
Tests for exception when expected.
```python
with pytest.raises(Exception):
    test_func()
```

## Approximations
Useful for floating point comparison.

```python
assert 6.6666666 == pytest.approx(6.6666)  # True
```



