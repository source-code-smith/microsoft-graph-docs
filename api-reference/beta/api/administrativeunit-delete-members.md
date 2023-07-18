---
title: "Remove a member"
description: "Use this API to remove a member (user, group, or device) from an administrative unit."
author: "DougKirschner"
ms.localizationpriority: medium
ms.prod: "directory-management"
doc_type: apiPageType
---

# Remove a member

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Use this API to remove a member (user, group, or device) from an administrative unit.

## Permissions
Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).


<!-- { "blockType": "permissions", "name": "administrativeunit_delete_members" } -->
[!INCLUDE [permissions-table](../includes/permissions/administrativeunit-delete-members-permissions.md)]

[!INCLUDE [rbac-admin-units-apis-write](../includes/rbac-for-apis/rbac-admin-units-apis-write.md)]

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
DELETE /administrativeUnits/{id}/members/{id}/$ref
```

> [!CAUTION]
> If you don't append `/$ref` to the request and the calling app has permissions to manage the member object, the object will also be deleted from Azure Active Directory (Azure AD); otherwise, a `403 Forbidden` error is returned. You can restore specific objects through the [Restore deleted items API](directory-deleteditems-restore.md).

## Request headers
| Name      |Description|
|:----------|:----------|
| Authorization  | Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response

If successful, this method returns `204 No Content` response code. It does not return anything in the response body.

## Example
### Request
The following is an example of the request. In the example below, `{id1}` represents the identifier for the target administrative unit, and `{id2}` represents the unique identifier for the member user, group, or device to be removed from the target administrative unit. 

```msgraph-interactive
DELETE https://graph.microsoft.com/beta/administrativeUnits/{id1}/members/{id2}/$ref
```

### Response
The following is an example of the response.
 
```http
HTTP/1.1 204 No Content
```


