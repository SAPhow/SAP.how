---
title: How good is OpenAI's ChatGPT for SAP Consulting?
categories:
- AI
tags:
- IDoc
- EDI
- DESADV
- QM
- ChatGPT
- OpenAI
author: Vasiliy Kharitonov
---

I was exploring OpenAI's ChatGPT with a question in mind: "Can it be usefull for
SAP Consultant?". Short answer is yes. However, this is not panacea, you have to
keep some important restrictions in mind.

## Conversation with ChatGPT on IDocs

Please find a quote from the conversation we had about IDocs:

> **Vasiliy:**
> 
> How well do you know SAP IDocs?
> 
> **ChatGPT:**
> 
> I have knowledge of IDocs (Intermediate Document) in the SAP system.
> IDocs are a standard data structure for electronic data interchange (EDI) in
> the SAP system. They are used to exchange business data between different SAP
> systems or between an SAP system and a non-SAP system. IDocs are similar to
> EDI documents, but are specific to the SAP system. They are used for various
> business transactions such as orders, invoices, and shipping notices. I can
> provide more information on IDocs and their usage in SAP if needed.
> 
> **Vasiliy:**
> 
> Do you know what is the message type for ASN from supplier?
> 
> **ChatGPT:**
> 
> The message type for an Advance Shipping Notice (ASN) from a supplier
> in SAP IDocs is `DESADV`
> (DESADV01 / DESADV02 / DESADV03 / DESADV04 / DESADV05 / DESADV06 / DESADV07 / DESADV08 / DESADV09 / DESADV10 / DESADV11 / DESADV12 / DESADV13 / DESADV14 / DESADV15).
> The ASN message type is used to send delivery and shipment information to the
> receiving party, in this case, the supplier. It contains information such as
> the delivery date, the number of items shipped, and any other relevant
> details about the shipment. The ASN can also be used to confirm the delivery
> schedule and to provide tracking information.
> 
> **Vasiliy:**
> 
> What is the correct process code for `DESADV` message type?
> 
> **ChatGPT:**
> 
> The correct process code for the `DESADV` (Advance Shipping Notice)
> message type in SAP IDocs is `EDI_DESADV`. This process code is used to process
> the IDocs of the message type `DESADV` in the SAP system. It is used to process
> the Advance Shipping Notice (ASN) IDocs that are received from a supplier.
> This process code triggers the necessary actions in the SAP system such as
> updating the stock levels, triggering a goods receipt, and updating the
> purchase order status. It also allows you to set up different settings for
> different message types and to manage the flow of IDocs in the SAP system.
> 
> **Vasiliy:**
> 
> Which transaction can I use to set it up?
> 
> **ChatGPT:**
> 
> In SAP, you can use the transaction `WE20` to set up the process code
> `EDI_DESADV` for the `DESADV` message type.  The transaction `WE20` is used to set
> up the partner profiles for EDI message processing. In this transaction, you
> can create, change, or display partner profiles, which are used to define the
> parameters and settings for EDI message processing.  You can use the
> following steps to set up the process code `EDI_DESADV` for the `DESADV` message
> type:
> 1. In the SAP system, navigate to the transaction `WE20`.
> 2. In the Partner Type field, enter the partner type, for example, LS
>    (Logistics service provider)
> 3. In the Partner Number field, enter the number of the partner for whom you
>    want to create the partner profile.
> 4. Click on the button 'Change'
> 5. Go to the IDoc Interface tab and there you can find the process code
>    field, enter `EDI_DESADV` there.
> 6. Go to the IDoc types tab and enter the message type `DESADV` in the IDoc
>    type field.
> 7. Save your changes.  Please note that this is just a general guide and the
>    steps may vary depending on the version of SAP you are using.

As you can see, the conversion we had is quite good and ChatGPT was generally
helpful, especially by providing the correct transaction in the end. I believe
this topic is somewhat easy to be good at as it is old and popular, so there
should be a lot of useful information connected to it on the internet.

So, I decided to have another conversation, this time on a newer, more
complicated topic.

## Conversation with ChatGPT on Quality Management

> **Vasiliy:**
> 
> I would like to discuss with you quality management process with S/4HANA
> embedded EWM. Is it possible to integrate ERP inspection lots (the ones that
> start with 10\*) with embedded EWM for update of the stock type?
> 
> **ChatGPT:**
> 
> Yes, it is possible to integrate ERP inspection lots (the ones that start with
> 10\*) with embedded EWM for update of the stock type in S/4HANA. This can be
> done through the use of the Inspection Lot API, which allows for the creation
> and update of inspection lots in the ERP system. This API can then be used to
> update the stock type in EWM based on the inspection results. Additionally, you
> can also use the warehouse task API to update the stock type in EWM based on
> the inspection results.
> 
> **Vasiliy:**
> 
> Please give me technical names for Inspection Lot API. Is it some kind of
> business event?
> 
> **ChatGPT:**
> 
> Inspection Lot API in S/4HANA is a set of BAPIs (Business Application
> Programming Interfaces) that can be used to create, update, or retrieve
> inspection lots in the ERP system. The specific BAPIs that are used for this
> purpose are:
> 
> * `BAPI_INSPLOT_CREATE`
> * `BAPI_INSPLOT_CHANGE`
> * `BAPI_INSPLOT_GETDETAIL`
> * `BAPI_INSPLOT_SAVEDATA`
> * `BAPI_INSPLOT_CREATEFROMDATA`
> 
> It is not a business event, but it's a set of function modules. These BAPIs can
> be called from an external system or custom program to create, update, or
> retrieve inspection lot data in the ERP system.
> 
> **Vasiliy:**
> 
> I didn't find those BAPIs in my system, but I found BAdIs, e.g.
> `QPLEXT_LOT_CHANGE` and `QPLEXT_LOT_DECISION`. Do you know something about
> them? My intention is to use `QPLEXT_LOT_DECISION` to integrate the decision to
> EWM.
> 
> **ChatGPT:**
> 
> Yes, I am familiar with those BAdIs. BAdIs (Business Add-Ins) are a way to
> enhance the standard functionality of the system without modifying the original
> code.
> 
> * `QPLEXT_LOT_CHANGE` is an enhancement point of the change BAPI for Inspection
> Lot. It allows you to add custom logic to the change BAPI for Inspection Lot
> * `QPLEXT_LOT_DECISION` is an enhancement point for the inspection decision. It
> allows you to add custom logic to the inspection decision process.
> 
> You can implement these BAdIs in your system to add custom logic to the
> inspection lot change and decision process. You can use the
> `QPLEXT_LOT_DECISION` BAdI to integrate the decision to EWM by adding a custom
> code logic to update the stock type in EWM based on the inspection results in
> your implementation class.
> 
> Please note that, The BAPI, BAdI and API names and their functionality might
> slightly change based on the version of S/4HANA you are using, so before making
> any change please check the availability in your system and refer to the
> official documentation of your S/4HANA version.
> 
> **Vasiliy:**
> 
> I red into the documentation and it looks like the BAdI QPLEX_LOT_DECISION is
> intended for EWM inspection lots, meaning the ones starting with 17\*. So, it
> looks like you are wrong, we can't use them for inspection lots 10\*.
> 
> **ChatGPT:**
> 
> I apologize for any confusion, you are correct that the BAdI
> `QPLEXT_LOT_DECISION` is intended for EWM inspection lots (starting with 17\*),
> and it is not intended for ERP inspection lots (starting with 10\*). The BAdI
> `QPLEXT_LOT_DECISION` allows you to add custom logic for the decision process
> of EWM inspection lots.
> 
> The BAPIs and BAdIs that are available for ERP inspection lots (starting with
> 10\*) are different from those that are available for EWM inspection lots
> (starting with 17\*). If you want to integrate ERP inspection lots (starting
> with 10\*) with embedded EWM for update of the stock type, you would need to
> use the BAPIs that are specifically intended for ERP inspection lots, such as
> `BAPI_INSPLOT_CREATE`, `BAPI_INSPLOT_CHANGE`, `BAPI_INSPLOT_GETDETAIL`. You can
> use these BAPIs to create, update or retrieve inspection lot data in the ERP
> system, and then use the warehouse task API to update the stock type in EWM
> based on the inspection results.
> 
> **Vasiliy:**
> 
> And what about BAdI `INSPECTIONLOT_UPDATE`? Did you hear about it?
> 
> **ChatGPT:**
> 
> I apologize for the confusion, Yes, I am familiar with BAdI
> `INSPECTIONLOT_UPDATE`, it's an enhancement point for the inspection lot, it
> allows you to add custom logic to the inspection lot process.
> 
> This BAdI is intended for ERP inspection lots (starting with 10\*), it will be
> called when you change any inspection lot from the ERP system, you can use this
> BAdI to integrate the decision to EWM by adding a custom code logic to update
> the stock type in EWM based on the inspection results in your implementation
> class.
> 
> Please note that, The BAPI, BAdI and API names and their functionality might
> slightly change based on the version of S/4HANA you are using, so before making
> any change please check the availability in your system and refer to the
> official documentation of your S/4HANA version.

First of all, I am impressed that he knows the difference between BAPIs and
business events. I am sure, most of the consultants could not tell me what is a
business event: it is quite new in SAP world. Possibly ChatGPT is taking
advantage of his knowledge from adjacent (not SAP) topics, where this concept
exists for some time already.

Regarding the questions I had, ChatGPT showed to be familiar with the concept,
however, it could not answer my question. The more important issue is that
ChatGPT didn't confess that it doesn't know the answer. It chose to made up
something, that would look like an answer instead.

You could also see this behaviour in the next conversation we had regarding MDG.

## ChatGPT conversation about MDG Key Mappings

> **Vasiliy:**
> 
> Could you please let me know a transaction to view keys and values for MDG key
> mappings?
> 
> **ChatGPT:**
> 
> To view the keys and values for MDG key mappings, you can use the "GET"
> transaction. The syntax for this transaction is as follows:
> 
> ```js
> GET [namespace] [key]
> ```
> 
> Where "namespace" is the name of the namespace
> that contains the key mapping, and "key" is the name of the key whose value you
> want to retrieve.
> 
> For example, to retrieve...
> 
> **Vasiliy:**
> 
> I was talking about SAP MDG key mappings. Could you please give me a
> transaction name?
> 
> **ChatGPT:**
> 
> In SAP MDG, the transaction to view key mappings is "`MDG_KK_MAPPING`".
> 
> You can use this transaction to view, create, change, and delete key mappings
> in SAP MDG.
> 
> You also can use this transaction to find the mapping entries for a specific
> key or to navigate through the mapping entries of a specific namespace.

I am quite sure the transaction `MDG_KK_MAPPING` is made up. ChatGPT didn't
know (or didn't care) about the real one, so he created something that looks
real, but doesn't work.

It should be quite obvious, but I believe ChatGPT doesn't know a difference
between saying something based on it's knowledge and just making something up,
that is actually not true. We expect this by default from all humans, so I
expected it from ChatGPT as well.

## Summary

ChatGPT actually knows a lot about SAP and can be quite useful for SAP
Consultants. The main usage I see is having a very smart [rubber
duck](https://en.wikipedia.org/wiki/Rubber_duck_debugging) for a quick
brainstorm.

Unfortunately, you can't rely on ChatGPT to provide you answers that are true.
They could seem to be correct, but you always have to check yourself how true
they are.

Nevetheless, I would be happy to integrate this tool in my workflow.
