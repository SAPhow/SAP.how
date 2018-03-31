---
title: How to export a table to Excel
categories: gui-design
systems:
- SAP EWM 9.4
---

It is a good idea to make data backups of any objects with which you plan some actions, like developments, some cleanup or a data transfer. Transaction SE16 usually is used for table data view, but there is no export to excel button in standart setting.

## View table data as ALV grid

To change the view of your data in SE16 transaction, proceed to top menu *Setting*->*User Parameters..(F8)*.

![Settings->UserParameters screenshot](/assets/i/2018/03/settings-user_parameters.png)

There you can change output type to `ALV Grid Display`.

![UserParameters ALV Grid screenshot](/assets/i/2018/03/UserParameters-ALV-Grid.png)

## Export to desirable format

ALV Grid will allow you to export to Excel and other formats, just press the button *Speadsheet... (Ctrl+Shift+F7)*.

![ALV Grid spreadsheet screenshot](/assets/i/2018/03/ALV-Grid-spreadsheet.png)

**Note**, that the maximum number of hits in the table is `200` as standard for SE16. It is possible, that not all data is shown. You can change the maximum number of hits on the selection screen of the table.
