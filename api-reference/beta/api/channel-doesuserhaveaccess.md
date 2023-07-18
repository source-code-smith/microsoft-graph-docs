---
title: "channel: doesUserHaveAccess"
description: "Determine whether a user has access to a shared channel."
author: "devjha-ms"
ms.localizationpriority: medium
ms.prod: "microsoft-teams"
doc_type: apiPageType
---

# channel: doesUserHaveAccess
Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Determine whether a [user](../resources/useridentity.md) has access to a shared [channel](../resources/channel.md).

## Permissions
Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "channel_doesuserhaveaccess" } -->
[!INCLUDE [permissions-table](../includes/permissions/channel-doesuserhaveaccess-permissions.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
GET /teams/{team-id}/channels/{channel-id}/doesUserHaveAccess
```

## Function parameters
In the request URL, provide the following query parameters with values.
The following table shows the parameters that can be used with this function.

|Parameter|Type|Description|
|:---|:---|:---|
|tenantId|String|The ID of the Azure Active Directory tenant that the [user](../resources/useridentity.md) belongs to. The default value for this property is the current **tenantId** of the signed-in user or app.|
|userId|String|Unique identifier for the [user](../resources/useridentity.md). Either specify the **userId** or the **userPrincipalName** property in the request.|
|userPrincipalName|String|The user principal name (UPN) of the [user](../resources/useridentity.md). Either specify the **userId** or the **userPrincipalName** property in the request.|


## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|

## Request body
Do not supply a request body for this function.

## Response

If successful, this function returns a `200 OK` response code and a Boolean in the response body.

## Examples

### Example 1: Check access for an internal user

The following is an example of a request that checks whether an internal user has access to a shared channel.

#### Request

The following is an example of a request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "channel_doesuserhaveaccess",
  "sampleKeys": ["19:33b76eea88574bd1969dca37e2b7a819@thread.skype", "0fddfdc5-f319-491f-a514-be1bc1bf9ddc", "6285581f-484b-4845-9e01-60667f8b12ae"]
}
-->
``` http
GET https://graph.microsoft.com/beta/teams/0fddfdc5-f319-491f-a514-be1bc1bf9ddc/channels/19:33b76eea88574bd1969dca37e2b7a819@thread.skype/doesUserHaveAccess(userId='6285581f-484b-4845-9e01-60667f8b12ae')
```

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/channel-doesuserhaveaccess-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/channel-doesuserhaveaccess-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The following is an example of the response.

<!-- {
  "blockType": "response",
  "@odata.type": "string"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": true
}
```


### Example 2: Check access for an external user

The following is an example of a request that uses the **tenantId** property to check whether an external user has access to a shared channel.

#### Request

The following is an example of a request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "channel_doesuserhaveaccess_externaluser",
  "sampleKeys": ["19:33b76eea88574bd1969dca37e2b7a819@thread.skype", "0fddfdc5-f319-491f-a514-be1bc1bf9ddc", "62855810-484b-4823-9e01-60667f8b12ae", "57fb72d0-d811-46f4-8947-305e6072eaa5"]
}
-->
``` http
GET https://graph.microsoft.com/beta/teams/0fddfdc5-f319-491f-a514-be1bc1bf9ddc/channels/19:33b76eea88574bd1969dca37e2b7a819@thread.skype/doesUserHaveAccess(userId='62855810-484b-4823-9e01-60667f8b12ae', tenantId='57fb72d0-d811-46f4-8947-305e6072eaa5')
```

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/channel-doesuserhaveaccess-externaluser-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/channel-doesuserhaveaccess-externaluser-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The following is an example of the response.

<!-- {
  "blockType": "response",
  "@odata.type": "string"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": true
}
```


### Example 3: Check user access for a user using the user principal name

The following is an example of a request that uses the **userPrincipalName** property to check whether an internal user has access to a shared channel.

#### Request

The following is an example of a request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "channel_doesuserhaveaccess_usingupn",
  "sampleKeys": ["19:33b76eea88574bd1969dca37e2b7a819@thread.skype", "0fddfdc5-f319-491f-a514-be1bc1bf9ddc", "john.doe@contoso.com"]
}
-->
``` http
GET https://graph.microsoft.com/beta/teams/0fddfdc5-f319-491f-a514-be1bc1bf9ddc/channels/19:33b76eea88574bd1969dca37e2b7a819@thread.skype/doesUserHaveAccess(userPrincipalName='john.doe@contoso.com')
```

# [Java](#tab/java)
[!INCLUDE [sample-code](../includes/snippets/java/channel-doesuserhaveaccess-usingupn-java-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/channel-doesuserhaveaccess-usingupn-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---

#### Response

The following is an example of the response.

<!-- {
  "blockType": "response",
  "@odata.type": "string"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": false
}
```

