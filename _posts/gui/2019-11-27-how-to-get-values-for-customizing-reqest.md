---
title: How to get values for customizing transport request?
categories: gui-basis
author: Vasiliy Kharitonov
systems:
- SAP EWM 9.4
---

Sometimes it is needed to find out which transport request changed some values
for a certain key. It is quite easy to find a request by key ([How to find
customizing requests by key values in
tables](/gui-support/find-request-by-keys)), but we also might want to check
which values where set by the corresponding request.

A short answer is that **it can't be done**. Unfortunately it seems that SAP
didn't design such an instrument for us. The values for corresponding keys are
stored in files on the server, which are compiled with SAP closed technologies.
So even if you download a request file from the server, you will have no way to
read it.

But there is actually another way to do it. You can import the corresponding
customizing request to a sandbox or temporary system and review the table
contents there. Because this method is not very convenient, the usual answer is
that it can't be done.

Technically there should be a way to design your own instrument by using SAP
programs/commands for converting the data file contents into a readable format
by means of ABAP programming, but it is very unlikely to be simple.
