---
title: Upgrade the Return to the Workplace solution for Microsoft Power Platform | Microsoft Docs
description: Provides an overview of how to upgrade the Return to the Workplace solution.
author: wbakker-11
ms.service: powerapps
ms.topic: conceptual
ms.custom: 
ms.date: 08/27/2020
ms.author: garybird
ms.reviewer: kvivek
---
# Upgrade the Return to the Workplace solution

This article provides step-by-step instructions for how to upgrade the existing Return to the Workplace solution to the latest version. If you're deploying the solution for the first time, see [Deploy the Return to the Workplace solution](deploy.md). Follow the steps to upgrade the solution and then follow the upgrade path that is applicable for you.

## Prerequisites

- You must be a global administrator or Microsoft Power Platform administrator to do the installation.

- You must be a global administrator and must have a Power BI Pro license to configure and publish reports.

- You must have installed the earlier version of Return to the Workplace and have the environment details. 

> [!TIP]
> Upgrading the solution affects the user experience. We recommend that you upgrade the solution outside of normal business hours, and test the changes on a development or test environment before moving it to a production environment. 

## Step 1: Update the solution

You can update the Return to the Workplace solution by using the Power Platform admin center.

> [!NOTE]
> If you're a US Government customer, you'll have to update the solution by using the latest version of the deployment package available on GitHub. More information: [Appendix: Deploy the app and publish Power BI dashboard (US Government customers only)](deploy.md#appendix-deploy-the-app-and-publish-power-bi-dashboard-us-government-customers-only)

  1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).

  2. On the left pane, select **Environments**, and then select the environment where you want to update the solution.

  3. On the left pane, select **Resources** > **Dynamics 365 apps**. From the list of apps, select **Power Platform Return to the Workplace - Apps**, which is the Return to the Workplace solution.

     > [!div class="mx-imgBorder"]
     > ![List of apps in the admin center](media/app-management-environment-view.png "List of apps in the admin center")

  4. The status field indicates that there's an update available for **Power Platform Return to the Workplace - Apps**. From the command bar, select **Update** or select the **Update Available** status to start the update process. From the command bar, you can also select **Details** to see the progress of the installation.
  
For more information about the update process, go to [Manage Dynamics 365 apps](https://docs.microsoft.com/power-platform/admin/manage-apps).

## Step 2: Update Power BI dashboards

When a new version of the  **Return to the Workplace** solution is available, you can be notified in two ways:

- An update banner appears in the Power BI Service informing you that a new app version is available.

    > [!div class="mx-imgBorder"]
    > ![Power BI banner](media/power-bi-new-app-version-notification-banner.png "Power BI banner")

- You'll receive a notification on the Power BI notification pane.

    > [!div class="mx-imgBorder"]
    > ![Power BI notification pane](media/power-bi-new-app-version-notification-pane.png "Power BI notification pane")

> [!NOTE]
> If you're a US Government customer, you'll have to update the Power BI dashboard using the latest version of the deployment package available on GitHub. More information: [Appendix: Deploy the app and publish Power BI dashboard (US Government customers only)](deploy.md#appendix-deploy-the-app-and-publish-power-bi-dashboard-us-government-customers-only)

1. To install the update, either select **Get it** on the notification banner or in the notification center, or find the app in the AppSource and select **Get it now**. If you have a direct link for the update, select the link.

2. You'll be asked whether you want to overwrite the current version or to install the new version in a new workspace. By default, **Overwrite an existing version** is selected.

   > [!div class="mx-imgBorder"]
   > ![Update App overwrite](media/power-bi-update-app-overwrite.png "Update App overwrite")

   If you already installed the existing version, leave it on **Overwrite an existing version**. Select **Install to a new workspace** to install a fresh version of the workspace and app that you need to reconfigure (connect to data, define navigation and permissions).
  
3. Install the app in a new workplace by following these steps in the deploy topic:
    - [Step 3: Configure and publish Power BI dashboards](/powerapps/sample-apps/return-to-workplace/deploy#step-3-configure-and-publish-power-bi-dashboards)
    - [Step 4: Schedule report refresh](/powerapps/sample-apps/return-to-workplace/deploy#step-4-schedule-report-refresh)
    - [Step 5: Embed the Power BI report in the model-driven app](/powerapps/sample-apps/return-to-workplace/deploy#step-5-embed-the-power-bi-report-in-the-model-driven-app)


## Upgrade from version 1.0 to 1.1

### Step 1: Install the Workplace Care Management dashboard

You can use the Workplace Care Management dashboard to track overall employee cases. More information: [Use the Workplace Care Management dashboard](dashboard-case-management.md)

To install the Workplace Care Management dashboard, follow the instructions in [Deploy the Return to the Workplace solution](deploy.md#step-3-configure-and-publish-power-bi-dashboards).


### Step 2: Update facilities

With the new version, we are introducing the notion of areas and floors for a facility. A floor indicates how many levels are present within a facility. An area allows you to define a space within a floor that has a certain capacity. Through bookings in the Employee app, you can book an area. More information: [Use the Facility Safety Management app](app-for-facility-manager.md).

Facilities now also have entry windows defined, which allow you to indicate in which time window people can enter the building. More information: [Use the Facility Safety Management app](app-for-facility-manager.md).


### Step 3: Define capacity for your reopen phases

Capacity is defined for an area, but it's also bound by the phase your facility is in. Every reopen phase defines the percentage by which capacity will be limited. More information: [Configure the solution](configure.md)


### Step 4: Make employee cases inactive

In the new version of the solution, employee cases become inactive when they're completed. More information: [Use the Workplace Care Management app](app-for-health-and-safety-lead.md#manage-employee-cases)


## Upgrade from version 1.1 to 1.2

### Step 1: Configure the solution settings

With the introduction of version 1.2, you will see more options in the solution settings. Numerous features are now configurable in the solution settings. For guests, we added new terms of agreements that are required. More information: [Configure the solution](configure.md#set-solution-settings)


### Step 2: Set up duplicate detection rules for employee cases

To limit the number of employee cases on an employee, it's possible to set up duplicate detection rules that warn you when making multiple employee cases. More information: [Configure the solution](configure.md#set-duplicate-detection-rules-for-employee-cases)


### Step 3: Facility access available

In previous versions, it was possible to indicate on an employee case whether the employee is allowed to enter a facility. This release changes the process so it blocks the employee from entering a facility. More information: [Manage employee cases - Monitoring](app-for-health-and-safety-lead.md#manage-employee-cases)

### Step 4: Send guest pass

With the introduction of guest passes, you can share passes with guests. From within the employee app, these **Share** buttons send an email via Outlook to the guest who is invited. To set this up, go to [Deploy the solution - Turn on Flows](deploy.md).


## Upgrade from version 1.2 to 1.3

### Step 1: Return to the Workplace Portal

With version 1.3 we are introducing the Return to the Workplace portal, which allows third-parties to indicate they are coming the facility. The portal is installed separate, which allows you to choice if you want to install it. What the portal can do, you can find in [Return to the Workplace portal](portal-extension.md). On how to install the portal, you will find that in the [Deploy the solution](deploy.md).  

### Step 2: Access Control

In version 1.2 we allowed case manager to block employees from access to the facility. We made this feature more generic which allows you to block employees via multiple ways either being from for example Power Automate or via the API. If you blocked employees earlier, please create access controls now. More information: [Facility Access](app-for-facility-manager.md#facility-access).

### Step 3: Notifications

With the introduction of version 1.3, we implemented notifications to notify employees about important events. They will receive these notifications either in the employee app or via different ways of communication. Out of the box, we supply email notifications. More information: [Enable Flows](deploy.md#step-9-enable-flows)

### Step 4: Power BI Dashboards

The Power BI Dashboards now contain information about the activities in the Return to the Workplace portal. We also implemented county / state level details for United States to get a more detailed view of the virus spread. More information: [Location Readiness dashboard](dashboard-for-executive-leadership.md)


## Give feedback about the solution

To provide feedback about the Return to the Workplace solution, visit <https://aka.ms/rtw-community>.
