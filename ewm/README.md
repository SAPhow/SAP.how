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

- **[Goods tracing](functions/goods-tracing)** on pallet, pack or even individual piece level.
- **Address storage**.
- **Warehouse reporting**.
- **Warehouse automation**.

## Documents

- **[Warehouse request](documents/warehouse-request)** — including inbound delivery request, outbound delivery request, expected goods receipt (and notification), posting change request.
- **[Delivery](documents/delivery)** — including inbound delivery, outbound delivery order, outbound delivery, posting change, production material request, stock transfer.
- **[Warehouse order](documents/warehouse-order)**
- **[Warehouse task](documents/warehouse-task)**
- **Wave**
- **[Handling unit](documents/handling-unit)** - including transportation unit.
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

### Management

{% for post in site.categories.ewm-management %}
  - [{{ post.title }}]({{ post.url }})
{% endfor %}

### Development

{% for post in site.categories.ewm-development %}
  - [{{ post.title }}]({{ post.url }})
{% endfor %}
