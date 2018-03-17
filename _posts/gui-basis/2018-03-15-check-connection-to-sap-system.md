---
title: How to check connection to other SAP system?
categories: gui gui-basis
systems:
- SAP EWM 9.4
---

## RFC connections

Connection between integrated by RFC SAP systems (for example, connection from EWM to ERP) can be checked in SM59 transaction.

1. Go to SM59 transaction.
2. Go to ABAP Connections.
3. Double-click on desired system.
4. Go to Connection Test.

It will execute ping function and output transfer times on the screen.
