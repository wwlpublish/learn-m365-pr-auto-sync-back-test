Users are assigned to the Power BI admin and Microsoft Power Platform admin roles in the Microsoft 365 admin center. Global admins and Power BI service admins can see the following tabs in the admin portal:

 -  **Usage metrics.** Usage metrics enable the admin to monitor the organization’s Power BI usage. It also indicates which users and groups are the most active within Power BI.
 -  **Users.** Power BI users, groups, and admins are managed in the Microsoft 365 admin center. This tab provides a link to the admin center in the organization’s tenant.
 -  **Audit logs.** Power BI audit logs are managed in the Microsoft 365 Security and Compliance Center (SCC). This tab provides a link to the SCC for the organization’s tenant. To use audit logs, admins must ensure the [Create audit logs for internal activity auditing and compliance](/power-bi/service-admin-portal?azure-portal=true) setting is enabled.
 -  **Tenant settings.** This tab enables control over the features that are made available to the organization. These controls include:
    
     -  Help and support settings
     -  Workspace settings
     -  Information protection
     -  Export and sharing settings
     -  Content pack and app settings
     -  Integration settings
     -  Custom visual settings
     -  R visuals settings
     -  Audit and usage settings
     -  Dashboard settings
     -  Developer settings
     -  Dataflow settings
     -  Template app settings
     -  Q&amp;A settings
 -  **Capacity settings.** The capacity tab that's displayed is dependent on the Power BI SKU that's purchased.
    
     -  **Power BI Premium.** This tab enables admins to manage any Power BI Premium capacities that have been purchased for their organization. All users within the organization can see the Power BI Premium tab. However, they can only see content within it if they're either a Capacity admin or a user that has assignment permissions.
     -  **Power BI Embedded.** This tab enables admins to view Power BI Embedded capacities that have been purchased. Power BI Embedded SKUs can only be purchased from Azure and managed through the Azure portal.
 -  **Embed Codes.** Admins can view the embed codes that are generated for their tenant to share reports publicly. They can also revoke or delete codes.
 -  **Organization visuals.** This tab enables admins to deploy and manage custom visuals inside their organization.
 -  **Dataflow settings.** By default, data used with Power BI is stored in internal storage provided by Power BI. With the integration of dataflows and Azure Data Lake Storage Gen2, dataflows can be stored in the organization's Azure Data Lake Storage Gen2 account.
 -  **Workspaces.** Admins can view the workspaces that exist in their tenant, sort and filter the list of workspaces, and display the details for each workspace.
 -  **Custom branding.** Admins can customize the look of Power BI for their entire organization.

Power BI enables administrators to script common tasks with PowerShell cmdlets. It also exposes REST APIs and provides a .NET SDK for developing administrative solutions.

**Additional reading.** For more information, see [PowerShell cmdlets, REST APIs, and .NET SDK for Power BI administration](/power-bi/service-admin-reference?azure-portal=true).

For more information about the Power BI service administrator role, see [Understanding the Power BI admin role](/power-bi/service-admin-role?azure-portal=true).

### Row level security

Row-level security (RLS) with Power BI can restrict data access for given users. Filters restrict data access at the row level, and report creators can define filters within roles. In the Power BI service, members of a workspace have access to datasets in the workspace. RLS doesn't restrict this data access.

Report creators can configure RLS for data models imported into Power BI with Power BI Desktop. They can also configure RLS on datasets that are using DirectQuery, such as SQL Server. The security option doesn't show up for live connection datasets. For Analysis Services' live connections, RLS is configured on the on-premises server.

### Power BI licensing

In the Power BI service, users have defined capabilities based on two attributes:

 -  The type of per-user license they have.
 -  Whether the content they're acting on is in a workspace assigned to a Power BI Premium capacity.

The Power BI licensing options are managed through the Microsoft 365 admin center. The options that are available to users include:

 -  **Per-user (Power BI Pro and Power BI (free) licenses).** A Power BI Pro license enables a user to collaborate with other Power BI Pro users. They do so by consuming content from and sharing content with other users with a Power BI Pro license. Only users with a Power BI Pro license can publish content to app workspaces, share dashboards, and subscribe to dashboards and reports. A free license enables a user to consume content in a workspace assigned to a Power BI Premium capacity and access to some of the features of the Power BI service for their own personal content in their My Workspace. For more information, see [Sign up for Power BI as an individual](/power-bi/service-self-service-signup-for-power-bi?azure-portal=true) and [Purchase and assign Power BI Pro user licenses](/power-bi/service-admin-purchasing-power-bi-pro?azure-portal=true).‎
 -  **Power BI Premium capacity (Power BI Premium licensing).** Power BI Premium provides dedicated capacity to deliver more consistent performance and support larger data volumes in Power BI. Power BI Premium also enables widespread distribution of content by Power BI Pro users without requiring users who view the content to have Power BI Pro licenses. For more information, see "[What is Power BI Premium?](/power-bi/service-premium-what-is?azure-portal=true)"

### Integrating mobile apps with Intune

Microsoft Intune enables organizations to manage devices and applications. The Power BI mobile applications for iOS and Android devices integrate with Intune. This integration enables admins to manage the application on devices and control security. Through configuration policies, admins can control items such as:

 -  Requiring an access pin.
 -  How data is handled by the application.
 -  Encrypting application data when the app isn't in use.

### Power BI URLs for allowlisting

The Power BI online service, also known as the Power BI SaaS (Software as a Service) application, requires connectivity to the internet. As such, certain endpoints must be reachable when using the Power BI online service. For more information, see [Add Power BI URLs to your allowlist](/power-bi/admin/power-bi-allow-list-urls?azure-portal=true).
