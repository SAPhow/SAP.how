---
title: How to compare objects between 2 systems?
categories: gui-basis
author: Vasiliy Kharitonov
---

In case you have a complex layout with 2 or more systems, there is always a need
to make sure they are aligned. And they usually should be aligned in both,
customizing and workbench objects. In this article we are focusing on
workbench objects.

## Transaction `SE39`

Transaction **SE39** *ABAP Split Screen Editor* allows to compare a single object
(Program/Function/Class) betweeen 2 systems.

To perform comparison:
1. Open transaction `SE39`.
2. Press button *Compare Different Systems (Shift+F7)*.
3. Select object you want to compare and provide its name, both in *Left* and
   *Right* sections.
4. Provide *RFC Destination* for a system with which you want to perform
   comparison. You can use transport destinations starting with `TMSSUP`.
5. Press the button *Display*.
6. Login window will be opened. You need to provide login information for a
   destination system.
7. Object in both systems will be opened side-by-side. If you want system to
   highlight differences, press the button *Comparison On (Ctrl+F4)*.

## Transaction `SREPO`

If you need to compare multiple objects or even all objects, you can use
transaction **SREPO** *Repository Comparison*.

To perform comparison:
1. Open transaction `SREPO`.
2. Provide *RFC Destination* for a system with which you want to perform
   comparison.
3. Select object which you want to compare. I usually use package names to
   perform comparison, as in the most cases people put all custom objects 
   in the same package. E.g. `ZERP` for all custom objects for ERP system. 
   It can also be usefull to select by transport request, if e.g. you compare
   objects after a release of multiple requests.
4. Press button *Create Object Intersection (F5)*.
5. You might be asked to login into a destination system. Provide login
   information if necessary.
6. A window with 3 columns will be opened. Left column contains objects, that
   exist only in source system, right column -- objects, that exist only in
   destination system, and middle column -- objects that exist in the both
   systems.
7. If you want to compare versions of objects between 2 systems, select
   rows in the middle section and press the button *Version Comparison (F5)*.
8. For each compared object a row will be displayed on the screen. Objects
   without difference will have a green status (column *Exception*) and a
   corresponding value in the column *Diagnosis* (e.g. "Identical"). Object
   with differences can be identified by a red status and a corresponding value
   in the column *Diagnosis* (e.g. "Not Equal To").
9. If you are interested in what exactly the differences are, you can double
   click the corresponding row to open compare view.

## You might also be interested in

- [How to compare customizing tables between 2 systems?](compare-customzing-tables)
