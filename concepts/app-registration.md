---
title: "Microsoft Graph app registration"
description: "Description of the overall Microsoft Graph app registration process"
author: "michaelvenables"
ms.localizationpriority: high
ms.custom: scenarios:getting-started
---

# Microsoft Graph app registration

## Fresh Azure portal experience

This is new best practices guidance for developers using the new Azure portal experience to register an Azure Active Directory (AAD) app with Data Connect. Additionally, with the new portal experience, developers and global administrators within the tenant can overview all registered applications, level of detail for consent, and ability to manage app registrations. Launch your experience in the [Azure portal](aka.ms/mgdcinazure). When you return to the portal, re-launch it in the search bar.

### Landing page

The first screen welcoming you to the new Azure portal experience will show a message asking you to create a new app registration.

![Graphic showing a landing page of the new Azure portal experience.](images/landing-page-first-screen.png)

> [!IMPORTANT]
> If Data Connect **hasn't been enabled by your admin**, the new portal experience is **disabled**.

After the landing page is populated with registered apps, a table shows details about the apps that were registered, including the following column fields:

1. `Name` the app registration name
2. `App ID` the Azure Active Directory (AAD) application ID
3. `Registered On` the date of registration of the app
4. `Developer` the email address of the developer who registered the application
5. `Multi-tenant` if the app is multi-tenant or single tenant
6. `Last modified` the most recent date when the application was changed

At the top of the table, three buttons are enabled by default: `Add`, `Refresh`, and `Delete`. `Add` starts an action for a new app registration. `Refresh` queries existing app registrations in the tenant again, and refreshes the table. `Delete` is only enabled for single selections, and initiates a deletion process.

![Graphic showing a table with column fields in the new Azure portal experience.](images/landing-page-table.png)

## Add a new app registration

When registering a new app with Data Connect, the add wizard will guide you in completing the required details in three tabs: `Registration Info`, `Datasets`, and `Review + create`.

### Registration Info page

The "Registration Info" page outlines standard requirements for app registrations. First, specify the project details, a process that's similar to creating a resource in Azure. The project detail fields are:

`Subscription` (required) select a subscription in the tenant that will be used exclusively to filter the next 4 selections used to configure the destination for the data.

`Resource Group` (required) select the group location for the data storage.
`Destination Type` select the type of storage from Azure Storage Account or Azure SQL Database Server

If the selected type of storage is SQL Database Server, then it will only support Mapping Data Flows types. Learn more about Mapping Data Flows.

`Storage Account` (required) select the storage account where the data to provision with MGDC will be located, or create a new Azure Storage Account.
`Storage Account Uri` (required) from the storage account selected above, select the Uri to use (Distributed File System (DFS) or blob).

If you select SQL for `Storage Account`, the `Uri` project detail field is disabled.

App registration requires you to select entries for the `Instance Details` that affect default behaviors such as the following fields:

`Application ID` (required) select from the AAD apps in the tenant or create a new one.
`Description` (required) provide details in the text field for app registration: project goal, unique identifier, organization project name, etc.
`Publish Type` (required) select from multi-tenant or single-tenant.
`Key Vault` (required for multi-tenant app registrations) specify the key vault that will enable communication between tenants.

![Graphic showing the registration page for adding applications on Data Connect, including fields related to the Project Details and Instance Details sections.](images/registration-info-page.png)

#### Datasets
