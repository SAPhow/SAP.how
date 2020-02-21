---
title: How does combined picking work?
categories: ewm-design
author: Vasiliy Kharitonov
systems:
  SAP EWM 9.4
---

Functionality _combined picking_ first appeared in EWM 9.4 and can help you in
cases where you need to pick multiple warehouse tasks from the same bin or
handling unit. Basically, it combines multiple tasks to be processed as a
single one. However, there are some important restrictions for using it.

The main restriction is that the task can only be combined if they are intended
for the same quant. In total they should have the same values for the following:

- Source bin
- Source handling unit
- Pick handling unit
- Stock type
- Owned and entitled
- Batch
- No serial number
- Alternative unit of measure
- Consolidation group

If the tasks have matching attributes, and the corresponding customizing is in 
place, RF user will be able to process them as one. It is also possible to
uncombine them during the processing if the user chooses so.

## Enhancing for picking different batches

There are a lot of business cases, where business wants to pick several batches
in one action. As you saw earlier it is not possible to do it in standard. But
there is a pretty easy way to do it with enhancement.

### Allow combining of multiple tasks with different batches

1. Create implicit enhancement in the beginning of FM `/SCWM/RF_PICK_PIMTTO_PBO`.
2. Check that this is a case relevant for your development.
3. Empty `ORDIM_CONFIRM-BATCHID` and `TT_ORDIM_CONFIRM-BATCHID`.

### Allow confirmation of multiple tasks with different batches

1. FM `/SCWM/RF_PICK_PICPMT_PB` needs to be enhanced (from my point of view it
is easier to create a custom version of corresponding FM and use it with RF
customization).
2. Right after reading additional material information with FM
`/SCWM/MATERIAL_READ_SIGLE` perform the following actions.
3. Check that `ORDIM_CONFIRM-BATCHID` is empty. If it is, clear `LS_MAT_GLOBAL-
BATCH_REQ`. This way the system will not ask for individual batch confirmations.

## Useful links

- [SAP Help - Combined picking](https://help.sap.com/doc/saphelp_ewm94/9.4/en-US/d5/96a75623814023e10000000a44147b/content.htm)
- [SAP Help - Combined picking using Radio Frequency](https://help.sap.com/doc/saphelp_ewm94/9.4/en-US/45/95c3565619df32e10000000a4450e5/frameset.htm)
