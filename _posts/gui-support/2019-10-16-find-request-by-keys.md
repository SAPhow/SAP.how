---
title: How to find customizing requests by key values in tables?
author: Vasiliy Kharitonov
categories: gui-support
systems:
  - SAP EWM 9.4
---

There are a lot of cases, where you would want to find all requests connected to
some organizational unit (e.g. warehouse number), or check if certain requests
(don't) contain some organizational unit.

I found that the easiest way to do this is to look into the table with requests.
You can follow the steps below:
1. Open transaction `SE16`.
2. Input the table name `E071K` (_Change & Transport System: Key Entries of
   Requests/Tasks_) and open its contents (_F7_).
3. Optionally you can use the field `TRKORR` (_Request/task_) to provide request
   numbers if you need to search though the certain requests.
4. Fill field `TABKEY` with a mask describing what you want to search. E.g. if
   you want to search for all requests regarding the warehouse number `Z001`,
   provide `*Z001*` as the value of this field.
5. Press _Execute_ (_F8_).
6. All table keys will be shown on the screen. Use _ALV Grid_ or _ALV Display_
   list formats to see the exact keys (you can also double click the row in
   standard list format) or [export the results to a
   spreadsheet](/gui-design/export-table-to-excel) to analyze them further.
