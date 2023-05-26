---
title: SAP GUI transaction helper (for SAP consultant)
categories: gui-user
author: Vasiliy Kharitonov
---

I have a list of most useful GUI transactions I personally use. It is hard to
keep it in memory, so I have a written note. I think others might find it useful
as well, so I am moving it here. From now on my note with most useful GUI
transactions will be managed here and regularly updated.

## Contents

- [System monitoring](#system-monitoring)
- [Transport functionality](#transport-functionality)
- [Comparison and alignment](#comparison-and-alignment)
- [Search and research](#search-and-research)
- [Authorizations and user management](#authorizations-and-user-management)
- [Customizing and settings](#customizing-and-settings)
- [Background jobs](#background-jobs)
- [Debugging and tracing](#debugging-and-tracing)
- [Automation](#automation)
- [Basis settings](#basis-settings)

## System monitoring

| ----------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **TCode** | **Name** | **Description** |
| ----------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `BD87` | Status Monitor for ALE Messages | Monitor processed and schedulled IDocs. |
| `DB50` | Database assistant | Database information and custom SQL execution for HANA systems. |
| `SCC4` | Client Administration | View existing clients for the current system. |
| `SLG1` | Application Log: Display Logs | Analyze application logs. |
| `SM04` | Logons to an AS Instance | Look for current logon sessions, close them even for other users. |
| `SM12` | Display and Delete Locks | Look for table locks per user or table. Drop them if needed. |
| `SM50` | Work Processes of AS Instance | Monitor current processes for the current application server instance. |
| `SM51` | Started AS Instances | Look for application server instanses, check work processes for each instance. |
| `SM58` | Asynchronous RFC Error Log | tRFC monitoring. |
| `SM66` | Systemwide Work Process Overview | Monitor current processes for all application server instanses. |
| `SMEC` | Measurement Environment Check | High-level system monitoring. Good to see green/red status on components overall or to navigate to sub-transactions like ST05 or AM50. |
| `SMQ1` | qRFC Monitor (Outbound Queue) | Check for scheduled outbound qRFCs and those in error. |
| `SMQ2` | qRFC Monitor (Inbound Queue) | Check for scheduled inbound qRFCs and those in error. |
| `SMQA` | tRFC/qRFC: Confirm. status & data | tRFC/qRFC monitoring. |
| `SMQR` | Registration of Inbound Queues | RFC scheduler for inbound messages. Here you can stop/start message queues from automatic execution. |
| `SMQS` | Registration of Destinations | RFC scheduler for outbound message. Here you can stop/start message queues from automatic execution. You can also provide maximum number of parallel connection for internal tRFC execution. |
| `SP01` | Output Controller | Find and review printing requests. |
| `ST04` | DB Performance Monitor | Useful to check what is the database used for the system (e.g. Oracle 12.2.0.1.0), check for database-caused slowdowns and [execute custom SQL queries](https://sap.how/gui-support/how-to-execute-custom-sql-request). |
| `ST06` | Operating System Monitor | Check for hardware-caused slowdowns, overview existing application servers and find their connection details. |
| `ST22` | ABAP Dump Analysis | Analyze dumps. |
| `SXI_MONITOR` | XI: Message Monitoring | Monitor XML messages processed with Proxy interfaces (e.g. integration with SAP PO). |

## Transport functionality

| ---------------- | ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **TCode** | **Name** | **Description** |
| ---------------- | ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `/SDF/TRCHECK` | Check Transport Requests | [Check for possible problems during transfer of certain requests](https://sap.how/gui-design/gui-support/problems-during-transfer-of-request). |
| `SCC1` | Client Copy - Special Selections | Copy customizing from another client. |
| `SE01` | Transport Organizer (Extended) | Find information regarding a single transport (usually by its number). Used to create transport requests as well. |
| `SE03` | Transport Organizer Tools | Search for transport request (by table or other object). |
| `SE09` | Transport Organizer | Find information regarding a multiple transports or even all transports. Used to create transport requests as well. |

## Comparison and alignment

| ----------- | --------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **TCode** | **Name** | **Description** |
| ----------- | --------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `SCMP` | View/Table Comparison | [Compare a single database table content between 2 systems](https://sap.how/gui-basis/compare-customzing-tables). |
| `SCU0` | Customizing Cross-System Viewer | [Compare multiple database table contents between 2 systems](https://sap.how/gui-basis/compare-customzing-tables). |
| `SE39` | ABAP Split Screen Editor | Compare a certain development object between 2 systems or different objects in one system. |
| `SREPO` | Repository Comparison | Compare multiple (or all) development objects between 2 systems. |

## Search and research

| ----------- | ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **TCode** | **Name** | **Description** |
| ----------- | ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `CODE_SCANNER` | ABAP Search | Holy Grail for highly customized systems. Search ABAP code in package or across system by text. |
| `SE11` | ABAP Dictionary Maintenance | Research tables, views, data types, domains, type groups. Used to search where they are used as well. |
| `SE16` | Data Browser | View database table contents. Used to change table contents as well. |
| `SE18` | Business Add-Ins: Definitions | Look for extension points (BAdIs). Browse existing implementations for a certain BAdI. |
| `SE19` | Business Add-Ins: Implementations | Research certain BAdI implementation. Used to change them as well. |
| `SE24` | ABAP Class Builder | Research ABAP classes and interfaces. Used to change them as well. |
| `SE37` | ABAP Function Modules | Research ABAP Function Modules. Used to change them as well. |
| `SE80` | Object Navigator | Quite powerful transaction. Can be used to do a lot of different things for any development objects including working with hierarchy for function groups and packages |
| `SE91` | Message Maintenance | Look for message classes, their messages, change/create them. |
| `SE93` | Maintain Transaction Codes | Look for transactions and their properties, change/create them. |
| `SFP` | Form Builder | Create/view/edit printing forms. |
| `SICF` | HTTP Service Hierarchy Maintenance | Research and test existing HTTP services (e.g. Fiori applications, NWBC applications, RF framework). |
| `SM59` | RFC Destinations (Display/Maintain) | Research / change / create connections to other systems. |
| `SPROXY` | Enterprise Repository Browser | Research and test Proxy integration (e.g. with SAP PO). |
| `STERM` | SAPterm Terminology Maintenance | Great tool to lookup SAP Terminology and translations for it. There is [an SAP website with similar content as well](http://sapterm.com). |
| `WE60` | Documentation for IDoc types | View IDoc structure for a certain basic type. |

## Authorizations and user management

| ----------- | ------------------------------ | ---------------------------------------------------------------------- |
| **TCode** | **Name** | **Description** |
| ----------- | ------------------------------ | ---------------------------------------------------------------------- |
| `SU01` | User Maintenance | Create / view / change users. |
| `SU3` | Maintain Users Own Data | Change your user-specific data like time-zone or default parameters. |
| `SU53` | Evaluate Authorization Check | Look for authorization errors for your user and other users as well. |
| `SUIM` | User Information System | Search authorization roles by different criteria. |

## Customizing and settings

| ----------- | ---------------------------- | -------------------------------------------------------------- |
| **TCode** | **Name** | **Description** |
| ----------- | ---------------------------- | -------------------------------------------------------------- |
| `BD97` | Assign RFC dest. to Logical Systems | Part of integration setup with other Netweaver systems. |
| `SCPR3` | Display and maintain BC Sets | Display and maintain BC Sets. |
| `SFW2` | Business Function | Display and maintain business functions. |
| `SM30` | Call View Maintenance | Change customizing for a certain view. |
| `SNRO` | Number Range Objects | Maintain number ranges. |
| `SPRO` | Customizing - Edit Project | Research and change customizing based on IMG activity trees. |
| `WE20` | Partner Profiles | Assign extensions to IDocs based on logical system and message type. |
| `WE57` | Assignment Messages for Appl. Objs | Assign Function Modules to IDoc basic types. |
| `STVARV` | Selection variable maintenance (`TVARV`) | Maintain `TVARV` parameters. |

## Background jobs

| ----------- | --------------------------- | ----------------------------------------------------------------------------- |
| **TCode** | **Name** | **Description** |
| ----------- | --------------------------- | ----------------------------------------------------------------------------- |
| `SM36` | Schedule Background Job | Create background jobs. |
| `SM37` | Overview of job selection | Search and analyse scheduled or executed background jobs, check error logs. |

## Debugging and tracing

| ----------- | --------------------------- | ----------------------------------------------------------------------------- |
| **TCode** | **Name** | **Description** |
| ----------- | --------------------------- | ----------------------------------------------------------------------------- |
| `SAAB` | Checkpoints that Can Be Activated | Activate breakpoints. |
| `SAT` | ABAP Trace | Main transaction to create and analyze ABAP traces. |
| `ST12` | Single transaction analysis | Another ABAP trace transaction. Old and not updated anymore, but still quite more powerfull for some scenarios. |
| `WE09` | Search for IDocs by Content | Search IDocs by values in certain fields. E.g. search shipment IDoc by shipment number. |
| `WE19` | Test tool | IDoc test tool. Simulate receiving of new IDocs based on existing ones. Field/values can be changed before sending. |

## Automation

| ----------- | --------------------------- | ----------------------------------------------------------------------------- |
| **TCode** | **Name** | **Description** |
| ----------- | --------------------------- | ----------------------------------------------------------------------------- |
| `LSMW` | Legacy System Migration Workbench | Automate customizing. |
| `SE71` | SAPscript form | Working with SAPscripts. |
| `SHDB` | Batch Input Transaction Recorder | Record and execute macroses. |
| `SQ01` | SAP Query: Maintain queries | Create custom reports with SAP Queries. |

## Basis settings

| ----------- | --------------------------- | ----------------------------------------------------------------------------- |
| **TCode** | **Name** | **Description** |
| ----------- | --------------------------- | ----------------------------------------------------------------------------- |
| `RZ11` | Profile Parameter Maintenance | Changing Profile Parameters Dynamically. |
