---
layout: post
title: How to enable Printer Determination for a custom PPF action?
author: Vasiliy Kharitonov
categories: ewm-development
systems:
  SAP EWM 9.4
---

After creation of a custom PPF action for printing in EWM, checkbox for printer determination for the new action will not be active for changing. So only one certain printer can be set for printing.


It can be changed by modifying standard BAdI implementations for printer determination PRINTER_DETERM_PPF.

A filter with name of PPF action should be added to corresponding implementation.

- Implementation for **Printer Determination for S&R Documents** - /SCWM/SR_PRINTER_DET.
- Implementation for **Delivery: Printer Determination** - /SCWM/PRINTER_PPF.
- Implementation for **Printer Determination for Inventory** - /SCWM/PI_PRINT_DET.

After filter is added the checkbox will become active.

## Verified systems
- SAP EWM 9.4
