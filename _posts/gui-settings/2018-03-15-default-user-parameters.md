---
title: How to set defaults for user parameters?
categories: gui-settings
systems:
- SAP EWM 9.4
---

User parameters can be set in SAP GUI via top SAP menu *System -> User profile -> Own data -> Parameters*. Parameter ID and value should be provided.

For example, EWM default values for warehouse number and warehouse monitor can be set for /SCWM/MON transaction:

| SET/GET Parameter ID | Parameter value | Short description |
|----------------------|-----------------|-------------------|
| /SCWM/LGN            | 0001            | Warehouse Number  |
| /SCWM/MON            | SAP             | Monitor           |
