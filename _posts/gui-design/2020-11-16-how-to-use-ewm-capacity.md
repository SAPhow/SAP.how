---
title: How to use EWM capacity?
author: Vasiliy Kharitonov
categories:
- gui-design
systems:
- SAP EWM 9.4
- SAP S/4HANA 1809
---

When you use storage types with storage behavior "Standard Warehouse", but 
still want to restrict capacity of the bins, you can use EWM capacity. It
allows you to restrict (and change created restrictions) how many handling 
units can be stored in a bin using only master data, without a need to 
perform customizing. You can also use it to restrict how many boxes or pieces 
of product can be stored in a bin even without handling units.

It can be used to restrict yard capacity as well, e.g. when you want to
restrict how many Transportation Units can fit in one Yard bin.

To use EWM capacity you need to fulfull the following prerequisites:

1. Storage type's Capacity check should be set to `1`, `2` or `3`. If you 
want to restict the number of HUs stored in the bin, select `2`
_Check according to Key Figure Packaging Material_.
2. Set some value to the attribute _Capacity_ of a bin you want to restrict.
3. Set some value to the _Capacity consumption_ attribute for units of measure
of material you want to restrict. If you want to restrict the number of HUs
stored in the bin, set _Capacity consumption_ for the base unit of measure for
packaging material, that will be used to create HUs. The field should be filled
on EWM side, you can use transaction `/SCWM/MAT1` _Warehouse product Maintenance_ or Warehouse Monitor to update it massively (Report _Product Master Data -> Warehouse Attribute -> Unit of Measure_).

> **Note:** Change in capacity of packaging material doesn't change capacity
> of existing HUs or TUs. New value will be used for new HUs, and old HUs
> should be updated manually.

