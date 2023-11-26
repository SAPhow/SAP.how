---
title: Overview of RFID with S/4HANA EWM
categories:
- S4HANA
- EWM
author: Vasilii Kharitonov
systems:
- SAP S/4HANA 2022
---

This article provides an overview of the integration of RFID technology with
S/4HANA EWM (Extended Warehouse Management). We will explore the typical
requirements or business benefits, the architecture of RFID, its standard
support and processes, and also discuss some of the equipment involved.

## Typical requirements for RFID in Warehouse Management

### Printing and Application of RFID tags

In this scenario, RFID labels or tags are primarily used for printing and label
application within the EWM system. The tags are subsequently utilized in later
stages, such as in customer systems or Point of Sale systems.

The S/4HANA EWM requirements here include:
- Creating a unique identification, that will be writenn on the label/tag,
  saving it in the database.
- Creating a label and sending it to the corresponding printer.

### Additional Data Provision for RF Terminals

This approach enables FLT (Fork Lift Truck) drivers to operate in a
"hands-free" manner. They don't need to manually scan bin or HU (Handling Unit)
barcodes, as RFID readers automatically perform these tasks based on proximity.
This method enhances FLT driver safety and efficiency, though its benefits may
be somewhat limited from my perspective.

The S/4HANA EWM requirements in this context are:
- Decoding RFID data for HU/bin input on RF screens.
- Managing double or incorrect inputs. An RFID scanner might detect the wrong
  HU or bin upon movement to a destination, or provide a bin instead of an HU.
  The system needs to handle these errors effectively to avoid confusing FLT
  drivers.
- In this scenario, there's also a need to connect a scanner to the RFID
  device, a requirement that extends to SAP S/4HANA itself.

### Handling Goods Without RF Terminals

To reduce the investment in RF terminals and further enhance FLT driver
efficiency, some processes, such as loading, can be managed without RF
terminals. In these cases, FLT drivers operate without RF terminals, and the
system autonomously records movements in the background.

This method is the only one supported by standard SAP (more details on this
later). It typically involves RFID tags on pallets and resources (like forklift
trucks), with stationary scanners at source/destination locations (such as RFID
gates before loading docks). For error handling, indicator lights can be used
to confirm successful movements (green light) or indicate errors (red light).

The requirements for S/4HANA EWM in this scenario include:
- Supporting RFID goods handling without RF terminals.
- Decoding RFID tags.

## Typical Solutions for RFID Requirements in S/4HANA EWM

### Implementing SAP Auto-ID Infrastructure (SAP AII)

In the standard SAP environment, the primary supported method for working with
RFID is through the SAP Auto-ID Infrastructure (SAP AII). This is technically a
distinct system from SAP S/4HANA and offers capabilities for connecting
RFID-specific equipment like RFID scanners. It also provides functionality for
creating RFID identifiers and decoding RFID tags.

### Creating RFID Identifications (EPC, SSCC)

To utilize standard functionality for creating identifiers like EPC (Electronic
Product Code) and SSCC (Serial Shipping Container Code), integration with SAP
AII is essential. EPC, a popular data format in RFID processes, is developed by
GS1—the organization also known for SSCC. Although there's no direct SAP
standard support for creating EPC/TDS RFID identifiers outside of SAP AII, the
open format allows for custom implementation in ABAP or other languages using
the relevant specifications.

After generating the necessary identifications, you can employ SAP's standard
data structures for RFID (refer to table `/SCWM/EPC` and the processing logic
from package `/SCWM/RFID`). As of 2022, this support extends to Handling Units,
Products, and Resources.

### Printing RFID labels

SAP AII can also facilitate the printing of RFID labels and integration with
RFID printers. If direct printing from SAP S/4HANA is desired without SAP AII,
custom development tailored to specific printers is required. For instance,
Zebra printers can accept RFID content through ZPL (Zebra Programming
Language), and SAP can incorporate ZPL code into its smartforms. [An example of
integration with Zebra R110Xi4 RFID
Printer](https://blogs.sap.com/2012/05/10/zebra-rfid-smartforms-ascii/).

### RFID Data Input for RF Screens

This scenario involves connecting RFID scanners to RF terminals to automate
input, bypassing the need for barcode scanners. It requires both hardware
support (that might not be trivial) and custom logic for decoding EPC binary
strings into recognizable identifiers.

A practical approach is to create a new barcode specification and implement the
corresponding BAdI (Business Add-In) for decoding and identifying connected
SSCC and/or other identifiers. Ensure that the intended screens support
composite barcode input and that incorrect or duplicate inputs are processed
efficiently.

### Supporting RFID Goods Handling without RF Terminals

This requirement is standardly supported by SAP AII. Therefore, implementing
and integrating SAP AII with SAP S/4HANA is recommended for addressing this
need.

As of 2022, SAP supports the following processes:
- **Automatic Loading and Unloading**: Utilizes fixed scanners to automatically
  update the status of Handling Units linked to inbound or outbound deliveries
  upon reading pallet RFID.
- **Automatic Packing Using RFID**: Employs fixed scanners to update HU
  hierarchy automatically by scanning corresponding RFID tags or labels.
- **Custom Actions**: SAP provides a BAdI to enable the creation of custom
  actions that the system will execute automatically after scanning an RFID
  tag.

If you have comments or suggestions, please feel free to [Raise an issue in our
GitHub](https://github.com/SAPhow/SAP.how/issues).
