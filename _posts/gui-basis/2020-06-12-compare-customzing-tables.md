---
title: How to compare customizing tables between 2 systems?
categories: gui-basis
author: Vasiliy Kharitonov
---

In case you have a complex layout with 2 or more systems, there is always a need
to make sure they are aligned. And they usually should be aligned in both,
customizing and workbench objects. In this article we are focusing on
customizing. [Click here](how-to-compare-objects-between-systems) if you want
to compare workbench objects.

## Transaction `SCMP`

Transaction **SCMP** *View/Table Comparison* allows you to compare a single
table between 2 systems. It is quite useful for comparing customizing tables as
well as other tables. The limitation is that you can only compare a single
table/view, so if you are comparing them in bulk, it is better to use something
else.

To compare a single table between 2 systems perform the following actions.

1. Open transaction **SCMP**.
2. Provide the name of the table to *View/Table* field.
3. Provide a destination system in *R/3 connection* field. ABAP connection for
   corresponding system should exist in **SM59** transaction. Although the field
   name suggest you to provide ERP system there, you can provide any NetWeaver
   system in the field.
4. Press *Compare View/Table (F5)* button.
5. Provide login details for corresponding system if asked.
6. Comparison view will be opened.
   - `R` to the left of the row indicates keys that only exist in the
     destination system.
   - `L` to the left of the row indicates keys that only exist in the
     source system.
   - `MR` to the left of the row indicates that keys exist in both systems, but
     values for them are different. It indicates values for keys in destination
     system.
   - `ML` to the left of the row indicates that keys exist in both systems, but
     values for them are different. It indicates values for keys in source
     system.


If you want to compare multiple tables at the same time you can try transaction **SCU0**.

## Transaction `SCU0`

Transaction **SCU0** *Customizing Cross-System Viewer* allows you to compare
multiple customizing tables at the same time. You can't use it to compare all
database tables between 2 systems (except by manual selection, but it is not as
efficient), only customizing tables, but it is quite useful if you need to
compare ALL customizing activities between 2 systems (e.g. between development
and quality landscapes).

You can select pull of tables by a certain Project or SAP Reference activities,
or you can do it by application components, or even certain transports. I
usually add custom development to the standard customizing tree, so all
customizing can be compared with option *SAP Reference IMG*.

To compare all customizing between 2 systems perform the following actions.

1. Open transaction **SCU0**.
2. Select option *SAP Reference IMG*.
3. Press *Create*.
4. Provide *Description* and destination system in *R/3 connection* field. ABAP
   connection for corresponding system should exist in **SM59** transaction.
   Although the field name suggest you to provide ERP system there, you can
   provide any NetWeaver system in the field.
5. Press button *Full comparison*.
6. Provide login details for corresponding system if asked.
7. A list with results will be displayed. By default it displays all tables
   compared, so I advice to set the following filters: *Adjustment status =
   Open* and *Comparison status = Differences*. Then only tables with
   differences will be displayed.
8. To see differences between keys in a certain table you can right click on the
   corresponding row and select *Comparison (F5)*. Comparison view will be
   opened.
   - `R` to the left of the row indicates keys that only exist in the
     destination system.
   - `L` to the left of the row indicates keys that only exist in the
     source system.
   - `MR` to the left of the row indicates that keys exist in both systems, but
     values for them are different. It indicates values for keys in destination
     system.
   - `ML` to the left of the row indicates that keys exist in both systems, but
     values for them are different. It indicates values for keys in source
     system.

## You might also be interested in

- [How to compare objects between 2 systems](how-to-compare-objects-between-systems)
