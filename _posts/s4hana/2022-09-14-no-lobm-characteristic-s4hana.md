---
title: No LOBM batch characteristics in S/4HANA
categories:
- S4HANA
- EWM
tags: batches, masterdata, new-instance, implementation
author: Vasiliy Kharitonov
systems:
- SAP S/4HANA 2021
---

You are trying to distribute batch characteristics starting with `LOBM` to
S/4HANA as a decentral EWM system. You receive the following error:

> Characteristic from reserved name range: change not allowed

Or you are trying to distibute a class and receive the following error:

> Characteristc "`LOBM_VFDAT`" not yet created

## Resolution

You can't create `LOBM_*` characteristics by distributing them from ERP system.
You have to copy them from standard client `000`. You can do it in the
following way:

1. Open transaction `SPRO` *Customizing - Execute Project*. Open *SAP Reference
   IMG*.
2. Navigate to node _Logistics – General under Batch Management → Batch
   Valuation → Update Standard Characteristics_.
3. Execute the Activity. This will copy the corresponding characteristics from
   the client `000`.
4. You can check successful characteristics creation using transaction `CT04`.
   See existing characteristics using search help for a field
_Characteristic_.

**Note:** The settings should be done per each landscape and client. Consider
doing this in all the landscapes at the same time to make sure this will not be
missed during cutover.
