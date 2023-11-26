---
title: Overview for RFID with S/4HANA EWM
categories:
- S4HANA
- EWM
author: Vasilii Kharitonov
systems:
- SAP S/4HANA 2022
---

This article is intended to be an overview of RFID functionality in combination
with S/4HANA EWM. We will look at typical requirements (or business benefits),
RFID architecture, standard support and processes and even some equipment.

## Typical requirements for RFID in warehouse management

### Only printing and application

Here RFID labels or tags are not really used in EWM system aside from using the
system for printing and label application. The tags will be used in the
consequent steps, e.g. in customer system or in a Point of Sale system.

The requirements for S/4HANA EWM system in this case could be:
- Creating a unique identification, that will be writenn on the label/tag.
- Creating a label and sending it to the corresponding printer.

### Additional way to provide data for RF terminals

In this case we allow FLT drivers to work "hands-free", they don't need to scan
a bin barcode or an HU barcode with a hand scanner, it is done by RFID reader
automatically based on proximity. This allows to increase safety and
effectiveness of FLT drivers, although the benefits are quite limited in my
point of view.

The requirements for S/4HANA EWM system in this case:
- RFID data decoding for HU/bin input for RF screens.
- Double/wrong input handling. RFID scanner could pick up a wrong HU or bin. Or
  provide a bin instead of HU. If the systm displays errors for all those
  accidental inputs, it will be confusing for FLT drivers.

In this case I assume we also need a possibility to connect a scanner to RFID
device, which might be not trivial, although this a requirement for SAP S/4HANA
itself.

### Handling of goods without using RF terminals

In order to decrease investments for RF terminals and increase efficiency for
FLT drivers we can consider implementing process handling withouth RF terminals
for some of the processes, e.g. loading. Thus, FLT drivers can work without RF
terminals, the system will record the movements itself in a background.

This setup is the only one supported in standard SAP, but more on that later.
Here, we usually have RFID tags on pallets and resources (e.g. forklift trucks)
and stationary scanners in source/destinaton location (e.g. RFID gates before
loading docks). If error handling is needed, there could be also some indicator
lights to confirm successful movmenet (with a green light) or indicate an error
(with a red light).

The requirements for S/4HANA EWM system in this case:
- Support of RFID goods handling without a use of RF terminal.
- Decoding RFID tags.

## Typical solutions for RFID requirements

In SAP standard the only supported way of working with RFID is implemented
using SAP Auto-ID Infrastructure (SAP AII), that is technically a separate
system from SAP S/4HANA. It implements possibilities to connect RFID-specific
equipment (e.g. RFID scanners), as well as functionality to create RFID
identifiers and decode RFID tags.

### Creating an RFID identification (EPC, SSCC)

As mentioned above, if you want this functionality to be standard, you need to
implement SAP Auto-ID Infrastructure and integrate it with SAP S/4HANA to
support creation of such identifiers. The most popular data format used in RFID
processes is EPC (created by the same organization known for SSCC: GS1). Even
though there is no standard SAP support for creating EPC/TDS RFID identifiers
outside of SAP, the format is open, so you could implement it in ABAP (or other
language) using the corresponding specification.

After generating the corresponding identification you can use SAP standard data
structures for RFID (see table `/SCWM/EPC` and the processing logic from
package `/SCWM/RFID`). As of 2022 there is support for HUs, Products and
Resources.

### Printing RFID labels

SAP AII (Auto-ID Infrastructure) can be used to support the printing (and
integrate with RFID printers) in standard SAP. If you want to print directly
from SAP S/4HANA without SAP AII, you could also do it by implementing a
development. The development should be specific to the printer, e.g. for Zebra
printers RFID contents can be passed using ZPL, while SAP supports including
ZPL code to its smartforms. [An example of integration with Zebra R110Xi4 RFID
Printer](https://blogs.sap.com/2012/05/10/zebra-rfid-smartforms-ascii/).

### RFID data input for RF screens

For this scenario we assume you connect RFID scanners to RF terminals in order
to automate input without using barcode scanners. Hardware support might not be
trivial and additionally you will need to implement your logic for decoding EPC
binary strings to the corresponding identifiers.

The logical solution is to create a new barcode specification and implement the
corresponding BAdI for decoding and determination of connected SSCC. Make sure
that indended screens do support composite barcode input and make sure
wrong/double input is processed correctly.

### Support of RFID goods handling without the use of RF terminal

This requirement is supported by SAP AII in standard, so I recomend to
implement SAP AII system and integrate it with SAP S/4HANA to solve it.

The following processes are supported by SAP as of 2022:
- Automatic loading and unloading. Upon reading pallet RFID by a fixed scanner,
  the status of HU connected to inbound/outbound delivery automatically
  changes.
- Automatic packing using RFID. Use a fixed scanner to automatically update HU
  hierarchy by reading the corresponding RFID tags or labels.
- Your own actions. There is a BAdI to create your own actions that system will
  perform automatically after scanning the RFID tag.
