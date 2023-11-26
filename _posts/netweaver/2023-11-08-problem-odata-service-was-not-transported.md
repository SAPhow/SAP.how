---
title: Problem - OData service was not transported
categories:
- S4HANA
- NetWeaver
author: David Berneburg
systems:
- SAP S/4HANA 2022
---

This article provide a possible solution to the problem you might have: OData
service was not transported.

## Symptoms

- OData Service is not included into the transport.
- OData Service in the target system is not active.

## Causes

- OData Service was activated, but saved locally.

## Solutions

Change development package for the Service correspondingly.

Procedure:
1. Open transaction `SE03` *Transport organizer tools*.
2. Go to *Change Object Directory Entries*.
   ![SE03 -> Change Object Directory Entries](/assets/i/2023/11/se03.jpeg)
3. Add selection fields for object types `IWSG` *SAP Gateway: Service Group...*
   and `IWOM` *SAP Gateway: Model Metadata...*, proved the names of the
   corresponding objects.
   ![Add selection fields for object types](/assets/i/2023/11/selection-by-objects.jpeg)
4. Execute, changing the development package correspondingly.
5. Upon changing the package, the system asks for a Transport Request, provide an open transport.
6. Release the request, import it to the corresponding system.
