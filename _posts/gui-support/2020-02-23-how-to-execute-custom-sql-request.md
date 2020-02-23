---
title: How to execute a custom SQL request?
author: Vasiliy Kharitonov
categories: gui-support
systems:
  - SAP EWM 9.4
  - SAP S/4HANA 1809
---

You can use **SQL Command Editor** to execute a custom SQL query. Open it via
transaction `ST04`, navigate to _Performance -> Additional Functions -> SQL
Command Editor_. There you can provide your query in the textarea _Input Query_.
Then press _Execute_ (F8) to send it to the database.

E.g. query `SELECT COUNT(*) FROM "/SCWM/ORDIM_C" WHERE “LGNUM”='0001'` will
show how many completed tasks there are in the warehouse number `0001` (SAP
EWM).

This can be useful to create complex reports with joints of multiple tables 
automatically analyzing data with the certain perspective. Result can be 
easily exported to an Excel sheet via corresponding button.
