---
title: "Metered APIs and services in Microsoft Graph FAQ"
description: "Find answers for frequent questions about using metered APIs and services in Microsoft Graph."
author: "JeremyKelley"
ms.localizationpriority: high
ms.custom: scenarios:getting-started
---

# Metered APIs and services in Microsoft Graph FAQ

## Billing setup FAQs

### What permissions are required to setup billing?
Setting up billing requires permissons both for the application registration and the Azure subscription you wish to use. Required permissions for the application registration are Application Owner or Application Administrator. Required permissions for the Azure subscription are Subscription Contributor, Owner / Resource Group Contributor, or Owner.

### Can I use a Service Principal to setup billing?
Yes, this requires an Application Administrator or similar role for the Service Principal. The role can be scoped to only the target application that is being setup for billing to prevent overly broad permissions from being granted.

### Can I use a Managed Identity to setup billing?
Yes, you can create a Managed Identity for Azure resources. Assign role based access control to your subscription or resource group, and add Active Directory-Application Administrator role to the Service Principal associated with the Managed Identity. See [Use a managed identity to access Azure Resource Manager - Windows - Microsoft Entra](/azure/active-directory/managed-identities-azure-resources/tutorial-windows-vm-ua-arm) for an example.

### How can I verify that my application is properly setup for billing?
Instructions for verifying billing setup can be found [here](/graph/metered-api-setup?tabs=azurecloudshell#verify-setup)

## Microsoft Teams export API billing FAQs

### Are there additional requirements beyond setting up billing to call Microsoft Teams export APIs?
Yes, Microsoft Teams export APIs require a Model parameter to be passed as part of the API call. Depending on the value of the Model parameter a user license may also be required for certain data. Please see [Teams API payment models and licensing requirements](teams-licenses.md) for details about the required Model parameters and user licenses.

### After setting up billing as a member of the preview program why am I not seeing billing data in Azure Cost Analysis or my exported reports?
As part of the preview program transition it may take up to seven days for billing data to begin appearing in the Azure billing system.

### How do I know which model parameter is being used in API calls?
Inspecting the code of the calling application is the best way to determine which model parameter is being used.

### What should I verify as a member of the preview program as billing is enforced?
- Verify that an Azure subscription is associated with your application
- Verify that the application passes the proper model parameter
- If appropriate verify the appropriate user licenses are acquired; Please see [Teams API payment models and licensing requirements](teams-licenses.md) for details about required licenses

### Why do my Azure billing information and the Teams admin dashboard information not match?

### How is seeded capacity calculated?
Seeded capacity for Teams export APIs being called with the model A parameter is calculated based on the number of eligible users in the target tenant. Seeded capacity is then applied to each application running against that tenant.

### How is seeded capacity applied?
Seeded capacity is evaluated at the beginning of the month, any eligible license counts to the tenant level calculation of seeded capacity. Each application then consumes the seeded capacity allocated to it until it is depleted. Further consumption by the application is then metered and appears on the monthly bill.

### What happens when an app that is registered but not setup for billing calls a metered Teams export API?
The API call will fail with a 402 Payment Required error. This is the case even if targeting a user with a valid user license and passing the model A parameter.

### What happens when the model parameter is excluded from a call to a Microsoft Teams export API that requires it?
When calling an API without a required model parameter the API will default to evaluation mode behavior. Evaluation mode provides a limited number of API calls per month before returning the 402 Payment Required error. Evaluation mode is provided for evaluation and development only and not intended for production use.  

## Application consumer FAQ

### Why is my application provider asking me to setup billing?
Billing for metered APIs and services in Microsoft Graph is handled by the owner of the application registration. If you have acquired an application that requires you to be the owner of the application registration you will be responsible for any metered APIs and services used by the application.

### Do I need licenses for every user in my tenant?
A license is required for each user that is subject to security and compliance policies. Other scenarios may not require a license, see [Teams API payment models and licensing requirements](teams-licenses.md) for more details about user license requirements for Microsoft Teams export APIs.

## Microsoft Teams chat export API billing pause FAQ

### Do I need to onboard billing given the billing pause?
The Teams chat export API billing pause does not affect other metered APIs, as a result your app will need to be setup for billing to continue calling the metered APIs. Although you will not be billed for usage of the paused API, billing setup is required to ensure a smooth transition when the pause ends.

### Do I need to pass the correct model parameter on Teams APIs even if the billing pause is in effect?
Yes, since APIs other than the Microsoft Teams chat export API are unaffected by the billing pause passing the correct model parameter is important to ensure that you are being billed correctly for other metered APIs.

### Which customers are impacted? 
Billing pause will affect only customers using Export API (/user/id/chats/getallmessages) to extract messages out of teams.
Billing enforcement (i.e., App id connected to azure subscription) will affect all customers using any of the metered Teams APIs.

### What happens after September 30?
After September 30th billing will resume on the Microsoft Teams chat export API. Applications calling the API will begin incurring metered charges at that point. 

### How can I estimate potential costs during the billing pause?
During the billing pause it will be up to application developers to monitor their usage of the API from outbound requests to the API and the data returned.