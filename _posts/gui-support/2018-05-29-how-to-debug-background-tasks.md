---
title: How to debug background tasks?
author: Vasiliy Kharitonov
categories: ewm-management
systems:
- SAP ERP 6.0
- SAP EWM 9.4
- SAP F&R 5.2
---

Does your background task run too long? Did you try to understand why and failed? Then probably the next step is to try to debug it to know exactly why does it happen.

Follow these simple steps to get to debug window.

1. Go to **SM50 transaction**.
2. Find the Work Process corresponding to your background task, select it.
3. Go in top menu to *Administration* -> *Program* -> *Debugging*.
4. The debugging window will open (of course if you have enough authorizations) and you can dive into the code. 
