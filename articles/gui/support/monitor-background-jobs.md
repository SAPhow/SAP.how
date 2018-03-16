---
Creation date: 2018-03-16
Author: Vasiliy Kharitonov
---

# How to monitor execution of background jobs?

If you have some critical for business background jobs, it is a good idea to have support team monitoring them.

Use SM37 transaction to check execution of background jobs. Following data is suggested for selection screen.

- Job Name - *job name*
- User Name — `*`
- Job Start Condition
  - From (date) - *current date*
  - To (date) - *current date*
  
*Execute* button will show all the launches of the program in a backgroun mode for provided date.

What could be interesting in the shown report:

- **Job created by**. If the certain user (for example corresponding to external system) should create the tasks, it is a good idea to check if it is correct. Keep in mind that it is only the user who created the task, execution of the task could be performed by another user.
- **Status**. Green status `Finished` will indicate that it was performed.
- **Start Time**. Check, that the start time is the same that was planned by design.

## Dumps

Another useful thing for background jobs is the check for dumps (Dump - in a simple way - is when during execution of the program something bad happened and the system upon dying recorded th dump, i.e. all it's attributes and the place of the error. This will help to find/reproduce/correct the issue.). Dumps could be find in ST22 transaction. Following data is suggested for the selection screen:

- Start and End Date and time - date and time of the start and end of the background job (from the report from SM37 transaction). If you do not want to fill the selection screen you can use buttons *Today* and *Yesterday* — the system will show dumps for the current or the previous day.

Press *Start*.

What could be interesting in the shown report:

- Time of dump inside the execution time of the background job.
- Canceled Program. If the name of the program correspond to one of your background jobs to be checked this is a red flag.

Existing of dumps for corresponding programs indicates that there are still issues with the background job even if it has `Finished` status.

## Verified systems

- SAP EWM 9.4
- SAP F&R 5.2
