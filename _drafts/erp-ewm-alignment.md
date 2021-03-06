---
title: How to align ERP with EWM?
author: Vasiliy Kharitonov
categories: ewm-management
systems:
- SAP ERP 6.0
- SAP EWM 9.4
---

If ERP and EWM are not aligned (for example to one of the systems the data was copied from another system), these activities should help to bring everything in order.

## 1. Decide on the way of alignment

Usually it is much easier to copy data from other systems in the same landscape (of course if the data is aligned there). This way with one activity you will have completely aligned systems with almost no possibility of mistake. To do this, just ask you basis team to transfer data to ERP and EWM from aligned systems in the same time.

Surely there could be times when it is not possible (or preferable) but still the systems should be aligned. And here this article should help. The first step is to draw a plan. Or just use the one below.

## 2. Remove transactional data from EWM

This is a local EWM activity, that will close all ongoing activities and prepare the system for alignment.

### 2.1. Complete or cancel all deliveries

Current deliveries have a high chance of creating misalignment in the future, so it is a good idea to complete them all first.

For unloaded inbound deliveries it is easier to complete them with putaway to some certain area-bin. Use warehouse tasks with administrative process type and immediate confirmation. For positions, for which unloading is not yet started it is easier to reject them.

For outbound deliveries situation is the same - if it is easier to perform goods issue - do it. Or if you cancel, move the goods to the same area-bin.

When you completed all deliveries, check if there are any open warehouse tasks. If there is any, it is a good idea to cancel them all.

### 2.2. Remove all stock

EWM stock is not consistent with ERP stock. The good way to make it perfect is to remove it all and upload correct stock again based on data from ERP.

We already have an area-bin with the stock from deliveries completion/cancellation. One of the ways to remove stock from EWM is to post it to not existing ERP storage location via /SCWM/ADGI transaction. This will create queue in ERP which can’t be processed. We will delete them later. Then feel free to delete all other stock, do not forget about stock in transportation units and resources.

Also it is a good idea to delete/complete/cancel all current transportation units, especially if you have integration with ERP shipments. Again, it doesn’t really matter what will you do with them as long as they gone. 

### 2.3. Delete all the bins

This step is not necessary if you are sure, that bins in EWM are ok.

To be continued...
