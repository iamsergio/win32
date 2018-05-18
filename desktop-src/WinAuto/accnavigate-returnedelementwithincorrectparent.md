---
title: AccNavigate\_ReturnedElementWithIncorrectParent
description: AccNavigate\_ReturnedElementWithIncorrectParent
ms.assetid: '44447E47-04D5-4784-B5E9-E8C62A9834CE'
---

# AccNavigate\_ReturnedElementWithIncorrectParent

## Text

Calling accNavigate((Live Search), 0, NAVDIR\_FIRSTCHILD) which returned (x-gadget:///gadget.html) returned the incorrect parent(\[NULL\]) and not (Live Search)

## Type

Error

## Description

When [**get\_accParent**](iaccessible-iaccessible--get-accparent.md) is called on the child element returned by [**accNavigate**](iaccessible-iaccessible--accnavigate.md) (using either the NAVDIR\_FIRSTCHILD or NAVDIR\_LASTCHILD navigation constants), the parent element returned does not match the parent element specified in the **accNavigate** call.

![example of an invalid msaa implementation that returns an incorrect parent element.](images/accchecker-invalid-msaa-parent.png)

This issue can cause navigation problems for automated tools because traversing elements might be erratic and unpredictable.

## Possible causes

An incorrect or invalid MSAA implementation.

## Related topics

<dl> <dt>

[**IAccessible::accNavigate**](iaccessible-iaccessible--accnavigate.md)
</dt> <dt>

[**IAccessible::get\_accParent**](iaccessible-iaccessible--get-accparent.md)
</dt> </dl>

 

 



