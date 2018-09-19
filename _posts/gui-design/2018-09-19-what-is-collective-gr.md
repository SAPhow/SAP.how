---
title: What is Collective GR? (EWM)
author: Vasiliy Kharitonov
categories: gui-design
systems:
- SAP EWM 9.4
---

Collective GR or Collective Goods Receipt is a customizing in EWM on business system level for integration with ERP. It is defined in IMG Activity `Set Control Parameters for ERP Version Control`.

It is one of the options for Goods Receipt Mode and it's idea is to combine GR messages into one posting until GR for delivery header is completed.

There is, however, an important restriction. **EWM will combine the goods receipt messages, unless there is other kind of messages** (to be sent to ERP). It means that as soon as we see another message, a partial GR will be sent to ERP system with what was received until this point. For another message we can have the following:
- Posting changes for changing the stock type.
- GR cancellation (even for partial quantity).
- Completion of Putaway for one delivery position.
- Any other messages to be sent to ERP by delivery interface for corresponding inbound delivery.

This can easily result in several postings for one delivery, for example
1. GR for a part of received quantity.
2. Posting change for changing the stock type.
3. Another GR for the rest of the quantity.
