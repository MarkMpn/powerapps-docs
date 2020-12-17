---
title: "View, download, and review portal capacity consumption reports for Power Apps portals | MicrosoftDocs"
description: "Learn how to view, download, and review the Power Apps portals capacity consumption reports from the Power Platform admin center."
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: 
ms.date: 12/14/2020
ms.author: sandhan
ms.reviewer: tapanm
---
 
# Portals capacity consumption reports

Power Apps portals is licensed using **per login**, and **per page view** capacity add-ons for external users. This capacity must be allocated to a Power Platform environment by an administrator. For more information about Power Apps portals licensing, go to [licensing FAQ](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#portals).

Administrators can download portal login and page view reports from the [Power Platform admin center](https://admin.powerplatform.com). These reports show the number of **logins** and **page views** for Power Apps portals across all environments for a tenant.

## Download reports

The individual reports contain data for a duration of 30 days preceding the date you select while downloading the reports.

To download the reports:

1. Go to [Power Platform admin center](https://admin.powerplatform.com).

1. In the left pane, expand **Resources**.

1. Select **Capacity**.

    ![Capacity](media/portal-consumption-reports/select-capacity.png "Capacity")

1. Scroll down to the **Add-ons** section, and select **Download reports**.

    ![Add-ons](media/portal-consumption-reports/summary-add-ons.png "Add-ons")

1. Select **Portal Logins**, or **Portal Views** report.

1. Select a **Target Date**. The report includes the data for the duration of past 30 days from the **Target Date** you select.

1. Select **Submit**.

    ![Confirmation for the request](media/portal-consumption-reports/confirmation.png "Confirmation for the request")

    A confirmation notification shows the download request acknowledgment.

1. After the generated report becomes available, select **Download**.

    ![Download report](media/portal-consumption-reports/download-notification.png "Download report")

    > [!TIP]
    > To quickly regenerate the report for the selected report type and target date, select **Regenerate report** from the consumption report notification.

1. **Save**, and **Open** the downloaded Excel report file.

## Analyze reports

The report contains date-wise capacity consumption of all available portals across all environments for the tenant. You can filter the Excel file with different columns, such as portal ID, environment ID, or date range, for additional analysis.

The following table provides the details about the columns in the downloaded report.

> [!NOTE]
> Format is the same for both types of reports - **Portal Logins**, and **Portal Views**.

| Column name | Description |
| - | - |
| **Date** | Date for the report data available in the row. |
| **PortalId** | ID of the portal. To check the ID of a portal, open the [services - about page](clear-server-side-cache.md) for that portal. |
| **EnvironmentId** | ID of the Power Platform environment. To check the ID of an environment: <ul> <li> Go to [Power Apps](https://make.powerapps.com). </li> <li> Select the environment from the environments list on the top-right side. </li> <li> Copy the environment ID from the browser's address bar. <br> For example, `https://make.powerapps.com/environments/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/home` lists the ID of the environment. </li> </ul> |
| **Consumption** | The total number of logins or views, depending on the report selected for download. You can compare the date-wise consumption number in the report for each environment with the configured maximum allowed numbers for logins or views using [Power Platform admin center - Manage add-ons](https://admin.powerplatform.microsoft.com/resources/capacity#add-ons). More information: [Power Platform add-on capacity management](https://docs.microsoft.com/power-platform/admin/capacity-add-on) |
| **PortalType** | Type of the portal - *Prod* for production, and *Trial* for trial. |
| **LicenseType** | Type of the license, *Capacity*. More information: [Licensing FAQ for Power Apps](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#portals), [Download Power Apps Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130)

### See also

- [Power Platform add-on capacity management](https://docs.microsoft.com/power-platform/admin/capacity-add-on)
- [Licensing FAQ for Power Apps](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#portals)
- [Download Power Apps Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130)
