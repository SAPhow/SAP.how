---
title: How to reprocess iDoc?
categories: gui
systems:
- SAP EWM 9.4
---

## Successfully processed iDocs

iDoc can be sent (received) again via WE19 transaction.

1. Open WE19 transaction.
2. Input the number of iDoc to be reprocessed and press *Create* (F8).
3. Press *Standard Inbond Processing* for inbound iDocs or *Standard Outbound Processing* for outbound iDocs.

## Processed with errors

iDocs, that were processed with errors can be processed again via BD87 transaction.

1. Open BD87 transaction.
2. Input selection parameters (dates or iDoc Number) and press *Execute* (F8).
3. Expand subtrees and find corresponding iDoc.
4. Select corresponding iDoc and press *Process Selected Node* (F8) in the to menu.
