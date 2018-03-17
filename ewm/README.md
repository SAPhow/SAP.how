# SAP EWM

SAP Extended Warehouse Management.

## Contents

- [Business functions](#business-functions)
- [Documents](#documents)
- [Warehouse processes](#warehouse-processes)
  - [Inbound](#inbound)
  - [Outbound](#outbound)
  - [Internal/common](#internalcommon)
- [Customizing](#customizing)
- [Articles](#articles)

## Business functions

- **[Goods tracing](functions/goods-tracing.md)** on pallet, pack or even individual piece level.
- **Address storage**.
- **Warehouse reporting**.
- **Warehouse automation**.

## Documents

- **[Warehouse request](documents/warehouse-request.md)** — including inbound delivery request, outbound delivery request, expected goods receipt (and notification), posting change request.
- **[Delivery](documents/delivery.md)** — including inbound delivery, outbound delivery order, outbound delivery, posting change, production material request, stock transfer.
- **[Warehouse order](documents/warehouse-order.md)**
- **[Warehouse task](documents/warehouse-task.md)**
- **Wave**
- **[Handling unit](documents/handling-unit.md)** - including transportation unit.
- **Vehicle**

## Warehouse processes

### Inbound

- Production
- Unloading from truck
- Goods receipt
- Putaway

### Outbound

- Staging
- Value added services
- Consumption to production
- Loading
- Goods issue

### Internal/common

- Dock appointment schedulling
- Yard management
- Goods movement
- Material flow system (integration with PLCs)
- Counting
- Scrapping
- Indirect labor

## Customizing

## Articles

{% for post in site.categories.ewm %}
- [{{post.title}}]({{post.url}})
{% endfor %}
