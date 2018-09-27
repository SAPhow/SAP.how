---
title: ABAP runtime trace. How to create it? How to understand results?
author: Vasiliy Kharitonov
categories: gui-support
systems:
- SAP EWM 9.4
---

You could find some problems that are impossible to understand just using the debugger or standard reports. For some of these problems ABAP runtime trace comes quite useful. These problems could be:

- long execution of system actions;
- problems that occur very rare and it is hard to figure out the cause;
- problems requiring to understand a full tree of ABAP stack, to know how many times some program was executed and where is was called from.

## Instruments to perform ABAP trace

There are a lot of standard SAP GUI instruments for runtime tracing (and a lot more for other kinds of tracing). These are the 2 I usually use:

1. Transaction SAT -- 
2. Transaction ST12

To be continued.
