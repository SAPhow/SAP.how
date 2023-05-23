---
title: How to fill DESADV IDoc structure to create nested Handling Units (HUs)?
categories: s4 le
author: Vasiliy Kharitonov
systems: SAP S/4HANA 2022
---

Here we will explain how to fill HU header (`E1EDL37`) segments to create
nested handling units on the example of IDoc with Delivery Interface basic type
(`DELVRY03`).

1. Segments `E1EDL37` for both child HUs and parent HUs can be on the same
   level.
2. Start with child elements. Although [the other way should be supported
   now](https://me.sap.com/notes/1534765), the better way to do is to go from
   child HU to parent HU.
3. Include segment `E1EDL44` with `VELIN` equal to `1` inside HU header
   (`E1EDL37`) segments for child HUs.
4. Include segment `E1EDL44` with `VELIN` equal to `3` inside HU header
   (`E1EDL37`) segments for parent HU. Reference child HU number in
   `E1EDL44-EXIDV` field. If there are multiple children reference each one of
   them in a separate `E1EDL44` segment.

This should allow you to generate the structure with nested handling units.

## Links

- SAP Note [2370129 - IDoc /SPE/IDOC_INPUT_DESADV1 does not transfer nested HUs](https://me.sap.com/notes/2370129)
- SAP Note [1534765 - IDOC /SPE/IDOC_INPUT_DESADV1: error with nested HUs](https://me.sap.com/notes/1534765)
- SAP Note [1227939 - IDOC error HUGENERAL 089 with nested HUs](https://me.sap.com/notes/1227939)
