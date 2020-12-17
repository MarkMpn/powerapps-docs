---
title: "Details about different security roles required to administer Power Apps portals with specific actions. | MicrosoftDocs"
description: "Learn about the available security roles, admin roles, and other permissions that are required to administer Power Apps portals."
author: neerajnandwana-msft
ms.service: powerapps
ms.topic: conceptual
ms.custom: 
ms.date: 12/15/2020
ms.author: nenandw
ms.reviewer: tapanm
---

# Roles required for portal administration

Power Apps portals has different kinds of administrative tasks that can be done by the members of different roles. The admin and security roles required to do these tasks vary depending on the impact area.

For example, some tasks may require the user to be a member of admin roles in [Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide&preserve-view=true), and others may need membership to security roles in [Power Platform environment](https://docs.microsoft.com/power-platform/admin/database-security).

In this article, you'll learn about the roles and permissions required to do different administrative tasks for portals.

## Required roles and permissions

The following table lists different administrative tasks for portals, and the roles required to do that task. The listed tasks can be done through the membership of the roles listed as required.

| Task | Required roles |
| - | - |
| [Add a custom domain name](add-custom-domain.md) | Any one of the following roles: <ul> <li> [Portal owner](#portal-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> <li> [Global administrator](#global-administrator) </li> </ul>   |
| [Change the Dynamics 365 instance of an add-on portal](change-dynamics-instance.md) | Any one of the following roles: <ul> <li> [Portal owner](#portal-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> <li> [Global administrator](#global-administrator) </li> </ul> |
| [Connect to a Microsoft Dataverse environment using a portal](manage-auth-key.md) | Any one of the following roles: <ul> <li> [Portal owner](#portal-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> <li> [Global administrator](#global-administrator) </li> </ul> |
| [Convert an existing portal to a capacity-based model](portal-lifecycle.md#convert-an-existing-portal-to-a-capacity-based-model) |  [Portal app owner](#portal-app-owner) and any one of the following roles: <ul> <li> [Portal owner](#portal-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> <li> [Global administrator](#global-administrator) </li> </ul> |
| [Convert a portal from trial to production](portal-lifecycle.md#convert-a-portal-from-trial-to-production) | [Portal app owner](#portal-app-owner) and any one of the following roles: <ul> <li> [Portal owner](#portal-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> <li> [Global administrator](#global-administrator) </li> </ul> |
| [Create portal](..\create-portal.md) | Required roles and permissions in **Azure Active Directory**: <ul> <li> Is [portal creation disabled](../create-portal.md#disable-portal-creation-in-a-tenant) in tenant? </li> <ul> <li> If **No** - [Permissions to register an app](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#permissions-required-for-registering-an-app) in the Azure Active Directory required. </li> <li> If **Yes** - Only [Global administrator](#global-administrator) can create a portal. </ul> </ul> <br> Required roles and permissions in **Power Platform** (both required): <ul> <li> User account with [Read-Write Access Mode](#read-write-access-mode). </li> <li> And [System administrator](#system-administrator) role. </li> </ul> <ul>   |
| [Download public key of a portal](get-public-key.md) | Any one of the following roles: <ul> <li> [Portal owner](#portal-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> <li> [Global administrator](#global-administrator) </li> </ul> |
| [Import metadata translation](import-metadata-translation.md) | Any one of the following roles: <ul> <li> [Portal owner](#portal-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> <li> [Global administrator](#global-administrator) </li> </ul> |
| [Reset a portal](reset-portal.md) | [Portal app owner](#portal-app-owner) and any one of the following roles: <ul> <li> [Portal owner](#portal-owner) </li> <li> [System customizer](#system-customizer) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> <li> [Global administrator](#global-administrator) </li> </ul> |
| [Update Dynamics 365 instance of a portal](power-platform-admin-center.md#update-dynamics-365-instance-for-your-portal) | User account with [Read-Write Access Mode](#read-write-access-mode), and any one of the following: <ul> <li> [System administrator](#system-administrator), and [Portal app owner](#portal-app-owner) </li> <li> Or, [Global administrator](#global-administrator) </li> </ul> |
| [Update portal packages](power-platform-admin-center.md#update-the-power-apps-portal-solution) | User account with [Read-Write Access Mode](#read-write-access-mode), and [System administrator](#system-administrator) |
| [View portal error logs](view-portal-error-log.md) | Any one of the following roles: <ul> <li> [Portal owner](#portal-owner) </li> <li> [System administrator](#system-administrator) </li> <li> [Dynamics 365 administrator](#dynamics-365-administrator) </li> <li> [Power Platform administrator](#power-platform-administrator) </li> <li> [Global administrator](#global-administrator) </li> </ul> |

## Manage membership of the required roles

This section explains about managing the membership of the required roles listed above for different kinds of administrative tasks in Power Apps portals.

### Dynamics 365 administrator

Dynamics 365 administrator is a Power Platform service admin role. This role can do admin functions on Power Platform because they have the system admin role.

To assign a user the Dynamics 365 administrator role, go to [Assign a service admin role to a user](https://docs.microsoft.com/power-platform/admin/use-service-admin-role-manage-tenant#assign-a-service-admin-role-to-a-user).

### Global administrator

Global administrator is a Microsoft 365 admin role. A person who purchases the Microsoft business subscription is a global administrator. A global administrator has unlimited control over products in the subscription and access to most data.

To assign a user the global administrator role, go to [Assign admin roles in Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles?view=o365-worldwide&preserve-view=true).

More information: [About admin roles in Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide&preserve-view=true)

### Portal app owner

Portal app owner is a user who owns [portal application registration](https://docs.microsoft.com/azure/active-directory/develop/quickstart-register-ap) in the [Azure portal](https://portal.azure.com).

To add an app owner for the portal app in Azure portal:

1. Sign in to the [Azure portal](https://portal.azure.com).

1. Search for and select **Azure Active Directory**.

1. Under **Manage**, select **App registrations**.

1. Select the Power Apps portals app from the list of available applications.

1. Under **Manage**, select **Owners**.

1. Select **Add owners**.

1. Select a user.

1. Select **Select**.

The user is added as an owner of the portal app.

### Portal owner

Portal owner is the user that created the Power Apps portal. This role can't be managed, and can't be changed.

### Read-Write Access Mode

A user account in Power Platform with **Access Mode** set to *Read-Write*. For detailed steps to configure Access Mode of a user account in Power Platform, go to [Create a Read-Write user account](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles#create-a-read-write-user-account). 

### System administrator

System administrator is a Power Platform security role. This role has full permissions to customize and administrator Power Platform environment.

To assign a user the System administrator Power Platform role, go to [Configure user security to resources in an environment](https://docs.microsoft.com/power-platform/admin/database-security).

### System customizer

System customizer is a Power Platform security role. This role has full permissions to customize Power Platform environment.

To assign a user the System administrator Power Platform role, go to [Configure user security to resources in an environment](https://docs.microsoft.com/power-platform/admin/database-security).

### Power Platform administrator

Power Platform administrator is a Power Platform service admin role. This role can do admin functions on Power Platform because they have the system admin role.

To assign a user the Power Platform administrator role, go to [Assign a service admin role to a user](https://docs.microsoft.com/power-platform/admin/use-service-admin-role-manage-tenant#assign-a-service-admin-role-to-a-user).

### See also

- [Portal admin center](admin-overview.md)
- [Portal Management app](../configure/configure-portal.md)
- [Portal site settings](../configure/configure-site-settings.md)
