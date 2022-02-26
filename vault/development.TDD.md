---
id: od4fW4S9BpXMXF89fiaco
title: TDD
desc: ''
updated: 1645916498673
created: 1641720907552
---

## TDD Rules
_Clean Architecture in Python_

- Test first, code later
- Add bare minimum code required to pass tests
- Shouldn't have more than one test failing at a time
- Write code to pass test, then refactor
- Test should fail first time ran, otherwise question whether test is needed
- Never refactor code without tests in place

## Types of test
_Clean Architecture in Python_

Flow | Type | Description |Test?
-----|------|------|------
Incoming | Query | unit accepts arguments and returns some value | Yes
Incoming | Command | unit accepts arguments and changes state of system | Yes
Private | Query | unit interacts with internal unit to attain a value | Maybe
Private | Command | unit interacts with internal unit to change state | Maybe
Outgoing | Query | unit interacts with external component and gets response | Mock
Outgoing | Command | unit changes the state of an external component | Mock

## Patching
In order to independently test units of code which interact with external components, patching can be applied which _mocks_ aspects of the underlying code. The benefit being that this can be done without having to edit the source code, but you are required to understand the source code in order to implement patching. 

This goes against the grain of TDD, so there are some useful guidance for implementing mocks and ensuring that unit and integration testing remain separate. Three _rules_ which help to determine whether the testing approach needs to be reviewed:

1. An increasing number of patches e.g. > 3
2. Overly complex patching e.g. several layers deep into class
3. Consider patching like _hooks_ where each _hook_ is a step back from the perfect assumption.


