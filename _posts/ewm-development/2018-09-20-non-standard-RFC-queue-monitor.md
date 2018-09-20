---
title: How to make non-standard RFC queue visible in the warehouse monitor?
author: Vasiliy Kharitonov
categories: ewm-development
systems:
- SAP EWM 9.4
---

You created a new queue masks for qRFC like `ZWMD...`, but it is not shown in warehouse monitor transaction, so your users can't see if something went wrong. Here you will find a guide on how to add your custom queue to the monitor report "Message Queue".

## Define Message Queue Definitions

The first step would be to perform customizing in IMG Acticity `Define Message Queue Definitions`. Workbench request is needed for following activities. But no developer code is not always needed.

1. Create a new row in the IMG `Define Message Queue Definitions` to create a new queue definition. You can use some similar existing row to copy from.
2. Fill "Description" and "Busines Object" in accordance with your queue.
3. Check that provided "Queue Name Prefix" is correct. It should correspond to your queue name, for example `ZWMD`.
4. Another important point here is the "Class for Message Queue Definition" and "qRFC Function Module". These are responsible for transcipting queue name into object codes for displaying in the monitor and other custom logic if needed. If your queue starts with `Z` or `Y`, you probably should create your own versions of class and function modules, becase standard ones will not now how to decode it.

## Define Message Queue Groups

Actually that's all. But you can also check if you new Message Queue Definition is shown for Queue Group "All Message Queue Definitions" `/SCWM/TEC_ALL`. If it is not there, you probably need to create a custom Queue Group to add you definition there.

Your custom messages should start showing in the Warehouse Monitor report `Message Queue`.
