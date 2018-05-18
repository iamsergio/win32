---
Description: 'Contains a list of the protocols to be used by DCOM. It contains an object for each protocol.'
ms.assetid: 'f553ce01-39b6-4dc3-9696-978b390a5c7d'
title: DCOMProtocols collection
---

# DCOMProtocols collection

Contains a list of the protocols to be used by DCOM. It contains an object for each protocol.

This collection supports the [**Add**](icatalogcollection-add.md) and [**Remove**](icatalogcollection-remove.md) methods of the [**COMAdminCatalogCollection**](comadmincatalogcollection.md) object.

## Members

The **DCOMProtocols** collection inherits from the [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509) interface but does not have additional members.

## Related Collections

You can navigate from this collection to any of the following collections:

-   [**ErrorInfo**](errorinfo.md)
-   [**PropertyInfo**](propertyinfo.md)
-   [**RelatedCollectionInfo**](relatedcollectioninfo.md)

You can navigate to this collection from the following collections:

-   [**Root**](root.md)

## Properties

The following properties are supported by the [**COMAdminCatalogObject**](comadmincatalogobject.md) object within the collection:

-   [Name](#name)
-   [Order](#order)
-   [ProtocolCode](#protocolcode)

### Name



|                |                                                                                                                                                             |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Description    | The name of the protocol. This property is returned when the [**Name**](icatalogobject-name.md) property method is called on an object of this collection. |
| Access         | ReadWrite                                                                                                                                                   |
| Type           | String                                                                                                                                                      |
| Default        | "New Protocol"                                                                                                                                              |
| Minimum system | Windows 2000                                                                                                                                                |



 

### Order



|                |                                         |
|----------------|-----------------------------------------|
| Description    | The order in which to try the protocol. |
| Access         | ReadWrite                               |
| Type           | Long (0-65000)                          |
| Default        | 0                                       |
| Minimum system | Windows 2000                            |



 

### ProtocolCode



|                |                                                                                                                                                                                                                                                                             |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Description    | The code specifying the RPC protocol sequence. The supported protocol codes include the following: ncacn\_ip\_tcp, ncacn\_http, ncacn\_spx. This property is returned when the [**Key**](icatalogobject-key.md) property method is called on an object of this collection. |
| Access         | WriteOnce                                                                                                                                                                                                                                                                   |
| Type           | String                                                                                                                                                                                                                                                                      |
| Default        | ""                                                                                                                                                                                                                                                                          |
| Minimum system | Windows 2000                                                                                                                                                                                                                                                                |



 

## See also

<dl> <dt>

[COM+ Administration Collections](com--administration-collections.md)
</dt> </dl>

 

 


