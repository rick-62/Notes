---
id: od4fW4S9BpXMXF89fiaco
title: TDD
desc: ''
updated: 1641802995208
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

Flow | Type | Description |Test?
-----|------|------|------
Incoming | Query | unit accepts arguments and returns some value | Yes
Incoming | Command | unit accepts arguments and changes state of system | Yes
Private | Query | unit interacts with internal unit to attain a value | Maybe
Private | Command | unit interacts with internal unit to change state | Maybe
Outgoing | Query | unit interacts with external component and gets response | Mock
Outgoing | Command | unit changes the state of an external component | Mock

