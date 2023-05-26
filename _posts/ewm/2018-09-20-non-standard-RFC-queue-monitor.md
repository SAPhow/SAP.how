---
title: How to make non-standard RFC queue visible in the warehouse monitor?
author: Vasiliy Kharitonov
categories: ewm-development
systems:
- SAP EWM 9.4
---

You created a new queue masks for qRFC like `ZWMD...`, but it is not shown in warehouse monitor transaction, so your users can't see if something went wrong. Here you will find a guide on how to add your custom queue to the monitor report "Message Queue".

## Define Message Queue Definitions

The first step would be to perform customizing in IMG Acticity `Define Message Queue Definitions`. Workbench request is needed for following activities. But developer code is not always needed (it is not needed if you can use standard Class for Message Queue Definition and qRFC Function Module).

1. Create a new row in the IMG `Define Message Queue Definitions` to create a new queue definition. You can use some similar existing row to copy from.
2. Fill "Description" and "Busines Object" in accordance with your queue.
3. Check that provided "Queue Name Prefix" is correct. It should correspond to your queue name, for example `ZWMD`.
4. Another important point here is the "Class for Message Queue Definition" and "qRFC Function Module". These are responsible for transcipting your queue name into object codes for displaying in the monitor and/or other custom logic if needed. You probably will have to create your own version of the class, becase the standard one may not know how to decode it. You can check if you need to do it by evaluating the logic inside the standard class from the row you used to copy, for example `/SCWM/CL_CORE_MQ_EVAL`.

## Define Message Queue Groups

Actually that's all. But you can also check if you new Message Queue Definition is shown for Queue Group "All Message Queue Definitions" `/SCWM/TEC_ALL`. If it is not there, you probably need to create a custom Queue Group to add you definition there.

Your custom messages should start showing in the Warehouse Monitor report `Message Queue`.
