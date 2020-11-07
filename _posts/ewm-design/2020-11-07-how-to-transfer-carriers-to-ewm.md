---
title: How to transfer carriers to EWM?
categories: ewm-design
author: Vasiliy Kharitonov
systems:
  SAP EWM 9.4
---

Carriers are needed in EWM if you want to integrate ERP shipments
with EWM transportation units using standard IDoc integration.

Carriers are transferred using Core Interface as vendors, but
you might find that although business partners are transferred,
carrier roles for them are not created. For this reason IDocs
will fall in the corresponding error.

There are two ways to fix it - right and wrong. The wrong way
would be to manually add carrier role for partner in EWM in the
transaction `BP`. It will fix the issue, but as ERP is the source
of truth for the business partners, you will need to do this 
again for the new partners or even for existing ones if something
changes.

For this reason it is better to fix it on ERP side. You need to
explicitly provide information which vendors are also carriers,
so integration model will transfer them as ones. To do this you
use Account group. As prerequisite you should be able to define
all carriers using one or multiple account groups. Then you need
to perform customizing.

1. Assign carrier account groups to APO location type `1020` "TSP"
using SPRO, path _Integration with other SAP components -> Advanced planning and optimization -> Application-specific settings and enhancements -> Settings and enhancements for shipments -> Assign vendor Account group to APO location type_.
2. Reactivate core interface integration model with corresponding
vendors using transactions `CFM1` and `CFM2`.

Carrier roles should be automatically created in EWM after these
actions.
