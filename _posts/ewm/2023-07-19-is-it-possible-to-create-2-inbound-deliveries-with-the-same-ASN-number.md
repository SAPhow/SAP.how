---
title: Is it possible to create 2 inbound deliveries with the same ASN number in SAP EWM?
categories: S4HANA EWM
author: Vasilii Kharitonov
systems:
- SAP EWM 9.4
- SAP S/4HANA 2022
---

Here we will look into the case where the same supplier sends us 2 deliveries
with the same ASN (Advanced Shipping Notification) numbers. Can we process them
in SAP EWM? Is it possible to control possibility to process them in standard
SAP?

In some cases we want to forbid such processing, as the same document could be
processed twice in case of human mistake or our system landscape doesn't
support having 2 documents with the same external identification.

In other cases suppliers can't ensure to provide a unique number each time,
e.g., their numbering is based on day and month, but repeats each year.
Therefore, it is important to have control over ASN uniqueness.

## Customizing to control ASN uniqueness

In SAP EWM, a specific setting controls the uniqueness of ASN. You can locate
this setting by navigating the following path:  *Extended Warehouse Management
-> Cross-Process Settings -> Delivery - Warehouse Request -> Process Management
and Control -> **Define Process Profile for Document Header***. It allows you
to manage the uniqueness of the ASN at the level of the level of Process
profile (which in turn is assigned to EWM Delivery Type). There are following
options present:

- `System Default`. The defaults are different per different
  systems, please check what is set for your system to undestand the behaviour:
    - *SAP S/4HANA Cloud* — Do not check if ASN number is Unique. Here this
      setting is hard-coded, you can't change it.
    - *SAP S/4HANA* — Check if ASN number is Unique. Even though this is what SAP
      Performance Assistant mentions, in my case with SAP S/4HANA 2022 default
      behaviour was **not to check** ASN uniqueness.
    - *SAP EHP3 for SAP ERP and higher* — Check if ASN number is Unique.
    - *SAP ERP 6.0* — Check if ASN number is Unique.
    - *R/3 46C, 470, 500* — Do not check if ASN number is Unique.
- `Check if ASN number is Unique`. The system will check that the ASN number is unique **per ship-from party and business system**. If it is not unique the delivery will be blocked from processing.
- `Do not check if ASN number is Unique`. The system will not
  check if ASN number is unique. You can easily receive 2 different deliveries
  with the same ASN number from the same supplier.

