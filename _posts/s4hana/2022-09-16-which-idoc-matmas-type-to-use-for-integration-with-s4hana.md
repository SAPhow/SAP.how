---
title: Which MATMAS IDoc type to use for integration with S/4HANA?
categories:
- S4HANA
- ERP
tags:
- idoc
- material
- masterdata
- matmas
author: Vasiliy Kharitonov
systems:
- SAP S/4HANA 2021
- SAP ERP 6.0
---

There is a number of `MATMAS` IDoc types present in the system, e.g.
`MATMAS03`, `MATMAS04`, `MATMAS05`, etc. Which one to use when you integrate
with S/4HANA system?

Generally speaking you should use the latest IDoc type you have in both sending
system and receiving system. When you send information from good old ERP to a
new S/4HANA system, choose the latest version (with the biggest number) you
have in the ERP system. If you have the following versions of `MATMAS`:
`MATMAS01`, `MATMAS02`, `MATMAS03`, `MATMAS04`, `MATMAS05`, --- choose
`MATMAS05`.

## Integration with S/4HANA as decentralized EWM system

When you follow the HTG guide for decentralized EWM integration, the IDoc type
is chosen for you automatically during execution of the program
`/SPE/R_DEC_EWM_REDUCE_MESSTYPE`. By default it sets the basic type to
`MATMAS03` which is missing the fields like _Warehouse material group_
(`WHMATGR`) or _Packaging material type_ (`VHART`). In case you need those
fields, you should update basic type for the corresponding parner profile and
message type to a higher version like `MATMAS05`. After this action the
corresponding fields should be filled and distributed automatically.

Use transaction `WE20` _Partner profiles_ to perform the update:

1. In SAP ERP open transaction `WE20`.
2. Select partner type `LS` and partner number corresponding to you EWM S/4HANA system.
3. Select message type `ZEWMMATMAS`, go to parameter details (double-click on the row).
4. Update the selected basic type `MATMAS03` to a higher version, e.g. `MATMAS05`.
5. Save.

The same procedure can be used to update message types `CHRMAS`, `CLSMAS`,
`CLFMAS`, `ADRMAS`, `ZEWMCREMAS`, `ZEWMDEBMAS`, `BATMAS` and `MATQM`.
