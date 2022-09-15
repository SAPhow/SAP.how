---
title: UKMS technical settings are not maintainable without a transport request
categories:
- S4HANA
tags: UKMS, MDG, implementation, mapping, masterdata
author: Vasiliy Kharitonov
systems:
- SAP S/4HANA 2021
---

You are using UKMS to map keys, e.g. to change material name for non-harmonized
masterdata. You set up everything in Development landscape and it is working.
However, when you moved to Quality you can't set up the required settings in
IMG node _Cross-Application Components -> Processes and Tools for Enterprise
Applications -> Master Data Governance -> Central Governance -> General
Settings -> Key Mapping -> Define Technical Settings -> **Define Technical
Settings for Business Systems**_, --- it asks you to provide a trasport
request, meaning you have to change it in the development client. This will not
work of course, as these settings are needed to a map business system with
logical system and RFC destionation, meaining they have to be different between
different landscapes.

## Resolution

There is an error in standard settings for a view `MDGV_BUS_TECH`
(`MDGV_BUS_ATTR`, `MDGV_BUS_BO`, `MDGV_BUS_TECH`), it has the wrong delivery
class. It should be possible to maintain this table in any client. 

According to the note
[3218973](https://launchpad.support.sap.com/#/notes/3218973) SAP did fix this
issue in the release `75H` support package `SAPK-75H01INSAPABA` of the software
component `SAP_ABA`. So, the solution is to upgrade to the according bersion of
the component.

In case you need a temporary workaround, you could open your quality
environment for changes and create a request there directly. However, I advise
against it unless you need a fix urgently.
