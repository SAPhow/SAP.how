---
title: How to use TVARVC parameter table in developments?
categories: ewm-development
author: Vasiliy Kharitonov
systems:
  SAP EWM 9.4
---

In some cases you might need to create a changeable parameter in a development.
If it is user changeable usually it is better to create a master data, because
this is how SAP does it in standard. With master data approach developments
should be seamless versus SAP standard. But there are some cases, e.g. logic
that will be performed only by technical specialists, where you don't need
master data transaction. In such cases additional master data can overcomplicate
the development and create additional effort for the developer. The most usual
case is when there are multiple "variants" of the same program and we need some
control to choose the one that we plan to use at the current moment.

## TVARVC parameter table

For such cases SAP created a special `TVARVC` parameter table, where user can
choose which "variant" should be used at the current moment.

### Developer side

First developer should include usage of a `TVARVC` parameter inside your custom
program. Some parameter will be defined to branch corresponding logic. The usual
advice is to have static selection logic for database table `TVARVC` created by
the developer, so additional selection from database would not significantly
influence performace of your program.

### Transaction STVARV

Transaction `STVARV` can be used to set the value for a parameter customized by
developer. Devepending on the value parameter you should be able to execute
different logic created by your developer. So, the usual flow is:
1. Run some tests.
2. Change the value of the agreed parameter in `STVARV` transaction.
3. Run the tests again.
