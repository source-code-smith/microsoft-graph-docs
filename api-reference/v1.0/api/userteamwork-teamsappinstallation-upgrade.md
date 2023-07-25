---
title: "teamsAppInstallation in personal scope: upgrade"
description: "Upgrade an app installation in the personal scope of a user"
author: "akjo"
doc_type: "apiPageType"
ms.localizationpriority: medium
ms.prod: "microsoft-teams"
---

# teamsAppInstallation in personal scope: upgrade

Namespace: microsoft.graph

Upgrade an [app installation](../resources/teamsappinstallation.md) in the personal scope of the specified [user](../resources/user.md)
to the latest version of the app.

>**Note:** This API works differently in one or more national clouds. For details, see [Implementation differences in national clouds](/graph/teamwork-national-cloud-differences). 

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "userteamwork_teamsappinstallation_upgrade" } -->
[!INCLUDE [permissions-table](../includes/permissions/userteamwork-teamsappinstallation-upgrade-permissions.md)]

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
POST /users/{user-id | user-principal-name}/teamwork/installedApps/{app-installation-id}/upgrade
```

## Request headers

| Header       | Value |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code. It does not return anything in the response body.

## Example

### Request

The following is an example of the request.



# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "user_upgrade_teamsApp",
  "sampleKeys": ["5b649834-7412-4cce-9e69-176e95a394f5", "NWI2NDk4MzQtNzQxMi00Y2NlLTllNjktMTc2ZTk1YTM5NGY1IyNhNmI2MzM2NS0zMWE0LTRmNDMtOTJlYy03MTBiNzE1NTdhZjk"]
}-->

```http
POST /users/5b649834-7412-4cce-9e69-176e95a394f5/teamwork/installedApps/NWI2NDk4MzQtNzQxMi00Y2NlLTllNjktMTc2ZTk1YTM5NGY1IyNhNmI2MzM2NS0zMWE0LTRmNDMtOTJlYy03MTBiNzE1NTdhZjk/upgrade
```

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/user-upgrade-teamsapp-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/user-upgrade-teamsapp-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

### Response

The following is an example of the response.

<!-- {
  "blockType": "response",
  "name": "user_upgrade_teamsApp",
  "truncated": true
} -->

```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "Upgrade teamsApp for user",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": []
}
-->
