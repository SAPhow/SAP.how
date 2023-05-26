---
title: How to check if there will be problems during transfer of the transport request?
author: Vasiliy Kharitonov
categories:
- gui-design
- gui-support
systems:
- SAP EWM 9.4
- SAP S/4HANA 1809
---

In systems where a lot of people work on different parallel projects we usually
can't be completely sure if we will break some existing functionality during
transfer of some request. It can be quite scary to transfer something in this
environment, but actually there is an easy way to check for such problems
**before** the transfer.

You can follow these steps to do it:

1. Open transaction `/SDF/TRCHECK` _Check transport request_.
2. Optionally provide _RFC to Source System_. You can skip this step if you are
   currently logged in to the source system.
3. Provide _RFC to Target System_. Here you should choose RFC connection to a
   system which the target for corresponding transfer. If you are checking if
   there will be problems during transfer to Quality environment, provide RFC
   connection, that indicates Quality environment system. E.g.
   `ECATT_QS4CLNT200` for system `QS4`. Use search help (_F4_) to select the
   correct value.
4. Provide _Transport Requests_ (you can provide multiple at the same time) that
   you plan to transfer. Alternatively, you could select _Import queue..._ if
   you are interested in **all** the requests from your import queue.
5. Set all transport checks that you want to be performed. I usually select all
   the checks:
    - cross reference;
    - sequence check;
    - cross release;
    - import time in source system;
    - online import check.
6. Press _Execute_ (_F8_).
7. You will most likely be asked to login (2 times) to the target system. Do
   that to initiate the checks.
8. Checks can take some time, especially if you chose multiple requests.
9. Results will be displayed in tabs (1 for each check selected). If the check
   is successful, you will see a green mark in the tab title. E.g. _(✓) Online
   Import Check_.
    - Red exclamation point will indicate that there are problems to be solved
      before the transfer. Usually you ask a developer to check what is the
      problem and how to solve it. E.g. _[!] Cross Reference_.
    - Yellow exclamation point will indicate that there are some warnings to be
      checked. Usually they don't indicate that there will be some problems
      during the transfer. E.g. _<!> Sequence Check_.

The most common source of problems will be on the tab _Cross Reference_. Some of
the objects you have in your requests were previously updated by another
transport request and this another request is not yet transferred to the target
system. Correct way to solve this is usually to transfer the missing transport,
but it isn't always possible. Otherwise, a developer can either put connected
objects to a new request (e.g. missing data types) or to remove conflicting
changes from the object you plan to transfer.
