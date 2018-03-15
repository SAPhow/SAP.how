---
Creation date: 2018-03-15
Author: Vasiliy Kharitonov
---

# How to set defaults for user parameters?

User parameters can be set in SAP GUI via top SAP menu *System -> User profile -> Own data -> Parameters*. Parameter ID and value should be provided.

For example, EWM default values for warehouse number and warehouse monitor can be set for /SCWM/MON transaction:

| SET/GET Parameter ID | Parameter value | Short description |
|--------------------|---------------|-----------------|
|       /SCWM/LGN      |       0001      |  Warehouse Number |
|       /SCWM/MON      |       SAP       |      Monitor      |

## Verified systems

- SAP EWM 9.4
