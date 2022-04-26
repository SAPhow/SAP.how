---
title: How to count SAP EWM delivery items in an existing system?
categories: ewm-basis
author: Vasiliy Kharitonov
systems:
- SAP EWM 9.4
- SAP S/4HANA 2021
---

In the new version of SAP EWM the main metric to understand hosting (for cloud
system) and license usage is average number of delivery items per day.

Within implementation project of SAP S/4HANA EWM PCE we had to understand how
to calculate the metric as a lot of things depend on it: the size of the
system, how much customer should pay for hosting and licenses, how many
production instances we can have.

According to [*RISE with SAP S/4HANA, private cloud edition Service Description
Guide*](https://assets.cdn.sap.com/agreements/product-policy/hec/service-description/rise-with-sap-s4hana-private-cloud-edition-service-description-guide-english-v1-2021.pdf)
the main metric for *SAP S/4HANA for extended warehouse management, extra
stack, private cloud edition* is number of items:
> Items represent the average number of Items (as defined below) per day based
> on the number of active days, managed in the Cloud Service during a contract
> year. A contract year is a 12- month period beginning on the first day of the
> Subscription Term or its annual anniversary. For shipper scenario, Items are
> delivery line items. A delivery is the documentation for a shipment sent
> to/from a warehouse location to/from a destination (customer, vendor or other
> plant/location). The items of the delivery are the unique material codes
> irrespective of quantity shipped under that delivery.  
> 
> For the transit warehousing scenario, Items are the packaging items (handling
> units) moved through the system from origin to destination. The packaging
> items are counted only once in this process

However it is not clear how exactly these items are calculated. If we already
have a system (the old decentral EWM or S/4HANA is already used), how to
calculate this metric? Should we count only main items, should we count text or
zero items, should we count PMR/EGR items, --- it is not clear from SAP
documentation.

Another complication we had is a number of warehouses, --- we have a lot of
them. How to understand the metric **per warehouse** number?

---

The solution to these problems is the table `/SCWM/DLVCNTRAW`, --- the one that
intended to be used by SAP when they perform audit. The table contains counters
for delivery items per warehouse per day, so it is useful for performing all
kind of reports.

If you want to count an average delivery items per year, you select all records
for a year, sum up the column `COUNTER` and divide it by 365 (days in a year),
--- voila! You have an average number of items per day for a whole year.

However, if your business has seasonality, you might want to consider
calculating the metric monthly and then use number from the biggest month. Or
you might want to do it per warehouse: you can use the same table.

Another benefit is that the table includes already archived data. However,
there seems to be its own archiving: the table holds only 24 months of data.

**Note:** use the metric at your own risk. I wasn't able to receive 100%
confirmation from SAP on how to actually calculate the metric. Moreover, I
received some contradicting messages. I suggest you to look for all existing
options before coming to the same conclusion: this is the best way to calculate
it.
