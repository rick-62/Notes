---
id: ws1H30KTMPg5yP4Ppry24
title: Functions
desc: ''
updated: 1641224699029
created: 1641217262362
---

## Mutable arguments and default values

https://thomas-cokelaer.info/tutorials/python/functions.html

A mutable argument is evaluated and saved only when the function is defined. This means mutable arguments are not reset on each function call. In a lot of cases this is fine, but can result in unintended consequences if not careful.

To avoid this behaviour initialisation must be done with an immutable object:

```python
def inplace(x, lst=None):
    if lst is None: lst=[]
        lst.append()
    return lst
```
Or

```python
original = [0, 1, 2]
function_changes_list(original[:])
original
[0, 1, 2]
```