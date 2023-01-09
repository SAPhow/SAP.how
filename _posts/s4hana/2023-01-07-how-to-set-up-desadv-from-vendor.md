---
title: How to set up inbound processing for DESADV IDoc from Vendor?
categories:
- S4HANA
- ERP
tags:
- IDoc
- EDI
- DESADV
author: Vasiliy Kharitonov
systems:
- SAP S/4HANA 2022
---

This article is a quick guide on how to setup processing of advanced shipping
notifications from vendors based on `DESADV` IDoc. This should allow you to
create inbound deliveries automatically based on messages from supplier.

1. First of all, your basis should set up connections and ports for you to be
   able to receive IDocs in the system. This setup is not included into the
article.

2. Then responsible for middleware (or responsible from the vendor directly,
   depending on your setup) should distibute a test IDoc to your system. This
will allow you to understand which basic type is used for the IDoc.

3. Use **`BD87`** *(Status monitor for ALE messages)* or other transaction of
   your choice to find the IDoc and see a basic type for it. Let's say it is
`DELVRY05`, message type `DESADV`.

4. Then you need to check which Function modules are allowed in your system for
   the corresponding basic type in the transaction **`WE57`** *(Assignment
Messages for Application Objects)*. Search a row with message type `DESADV` and
your version of basic type (e.g.  `DELVRY05`).  You can also search directly in
the table `EDIFCT`, I found it more convinient. 

5. Then use transaction **`WE64`** *(Documentation message types)* to determine
   the correct proccess code.  You can search by message type, e.g.  `DESADV`.
Look into the description of suitable process codes and assigned Function
Modules to identify the one you will use. Function module should match allowed
ones for your message in **`WE57`**. Let's say it is `DELSP` with FM
`IDOC_INPUT_POS_DESADV`.

6. Use the corresponding Process code to set up a partner profile in
   transaction **`WE20`** *(Partner Profiles)* for the vendor number you
receive within the IDoc.

7. Request an new IDoc with a real test data. This time it should be
   processed succesfully.

**Note:** If you want to use a certain Function module, e.g.
`/SPE/IDOC_INPUT_DESADV1`, you can allow its processing using the transaction
**`WE57`**. You should have enough authorizations and a Workbench request to
make changes in this table. In this case use the process code that assigned to
the corresponding Functional Module, e.g. `DELS`.
