---
title: "Use SQL to query data (Microsoft Dataverse) | Microsoft Docs" # Intent and product brand in a unique string of 43-59 chars including spaces
description: "Learn how to query Microsoft Dataverse entity data using SQL." # 115-145 characters including spaces. This abstract displays in the search result.
ms.custom: ""
ms.date: 12/16/2020
ms.reviewer: "pehecke"
ms.service: powerapps
ms.topic: "article"
author: "mayadumesh" # GitHub ID
ms.author: "pehecke" # MSFT alias of Microsoft employees only
manager: "kvivek" # MSFT alias of manager or PM counterpart
search.audienceType: 
  - developer
search.app: 
  - PowerApps
  - D365CE
---

# Use SQL to query data (Preview)

[!INCLUDE[cc-data-platform-banner](../../includes/cc-data-platform-banner.md)]

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

> [!IMPORTANT]
> This feature has been re-enabled in the majority of regions. Please resume testing, and provide feedback. We thank you for your patience and feedback.<p/>
> [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]

A SQL data connection is available on the Microsoft Dataverse endpoint. The SQL connection provides read-only access to the entity data of the target Dataverse environment. This allows you to execute SQL queries against the entity data table. Table columns provide the attribute data of the entity. No custom views of the data have been provided.

## Applications support

TDS (SQL) endpoint applications support for Power Apps and SQL Server Management Studio is described below.

### Power Apps

You can use the **Analyze in Power BI** option (**Data** > **Entities** > **Analyze in Power BI**) in Power Apps (https://make.powerapps.com) to use the Dataverse connector to analyze data in Power BI Desktop. More information: [View entity data in Power BI Desktop](/powerapps/maker/data-platform/view-entity-data-power-bi)

> [!NOTE]
> To enable this feature, see the TDS endpoint setting in [Manage feature settings](/power-platform/admin/settings-features). Once enabled you should see a button **Analyze in Power BI** in the command bar of Power Apps.

### SQL Server Management Studio

You can also use [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms) (SSMS) version 18.4 or later with the Dataverse endpoint SQL connection. Examples of using SSMS with the SQL data connection are provided below.

![Expanded account table](media/ssms-table-expanded.PNG)

## Security and authentication

The Dataverse endpoint SQL connection uses the Dataverse security model for data access. Data can be obtained for all entities to which a user has access to in Dataverse.

Only Azure Active Directory authentication is supported. SQL authentication and Windows authentication are not supported. Below is an example of how to logon to the SQL connection in SSMS. Notice the server name is the organization address URL.

![Connec dialog](media/ssms-connect-dialog.PNG)

> [!NOTE]
> The requirement to specify a port number after the service URL has been removed.

## Example entity data queries

Below are a couple of example queries composed in SSMS. The first image shows a simple query using aliases and result ordering.

```tsql
select top 5 a.name as [VIP customer], a.address1_postalcode as [ZIP code] from account a order by a.address1_postalcode desc
```

![Simple query using aliases and ordering](media/ssms-simple-query.PNG)

This next query shows a JOIN.

```tsql
select name, fullname from account a inner join contact c on a.primarycontactid = c.contactid
```

![Another query using a JOIN](media/ssms-join-query.PNG)

## Supported operations and data types

For a detailed list of supported SQL operations on the Dataverse endpoint see [How Dataverse SQL differs from Transact-SQL](how-dataverse-sql-differs-from-transact-sql.md).

Any operation that attempts to modify data (i.e., INSERT, UPDATE) will not work as this is a read-only SQL data connection. Dataverse option sets are represented as \<OptionSet\>Name and \<OptionSet\>Label in a result set.

The following Dataverse datatypes are not supported with the SQL connection: `binary`, `image`,
`ntext`, `sql_variant`, `varbinary`, `virtual`, `HierarchyId`, `managedproperty`, `file`, `xml`, `partylist`, `timestamp`.

> [!TIP]
> `partylist` attributes can instead be queried by joining to the `activityparty` table as shown below.
> 
> ```tsql
> select act.activityid, act.subject, string_agg([to].partyidname, ', ')
> from activitypointer as act
> left outer join activityparty as [to] on act.activityid = [to].activityid and [to].participationtypemask = 2
> group by act.activityid, act.subject
> ```

## Limitations

There is an 80MB maximum size limit for query results returned from the Dataverse endpoint. Consider using data integration tools such as [Data Export Service](https://docs.microsoft.com/powerapps/developer/data-platform/data-export-service) and [dataflows](https://docs.microsoft.com/power-bi/transform-model/dataflows/dataflows-introduction-self-service) for large data queries that return over 80MB of data. More information: [Importing and exporting data](/powerapps/maker/data-platform/import-export-data)

Dates returned in query results are in local time for the executing user. The corresponding time in Universal Time Coordinated (UTC) can also be retrieved from the corresponding column with a `utc` suffix, e.g.:

```tsql
select createdon, createdonutc
from account
```

The UTC columns are not available from Power BI, but can be accessed from SSMS.

> [!NOTE]
> Until a service update planned for January 2021 has deployed, using date filters will be slow.

Querying data using SQL does not trigger any plug-ins registered on the <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> or <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> messages. Any re-writing of the query or results that would normally be performed by such a plug-in will therefore not take effect for a SQL query.

Queries using the TDS endpoint execute under the service protection API limits.

## Troubleshooting authentication problems

Only Azure Active Directory authentication is supported on the Dataverse endpoint SQL connection. The preferred authentication mechanism is "Azure Active Directory – Universal" with multi-factor authentication (MFA). However, "Azure Active Directory – Password" will work if MFA is not configured. If you try to use other forms of authentication, you will see errors like the following.

- Error returned when using **Azure Active Directory – Integrated** authentication.

“Login failed: The HTTP request was forbidden with client authentication scheme 'Anonymous'.
RequestId: TDS;81d8a4f7-0d49-4d21-8f50-04364bddd370;2
Time: 2020-12-17T01:10:59.8628578Z (.Net SqlClient Data Provider)”

- Error returned when using **SQL Server** authentication.

“Login failed: Request is not authenticated.
RequestId: TDS;918aa372-ccc4-438a-813e-91b086355343;1
Time: 2020-12-17T01:13:14.4986739Z (.Net SqlClient Data Provider)”

- Error returned when using **Windows** authentication.

“Login failed: Request is not authenticated.
RequestId: TDS;fda17c60-93f7-4d5a-ad79-7ddfbb917979;1
Time: 2020-12-17T01:15:01.0497703Z (.Net SqlClient Data Provider)”

### See also

[Use FetchXML to construct a query](dataverse-sql-query.md)  
[Service Protection API Limits](api-limits.md)
