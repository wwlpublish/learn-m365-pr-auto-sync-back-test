General purpose Power Automate capabilities are licensed on a standalone basis. Limited Power Automate capabilities are also included within Power Apps, Microsoft 365, and Dynamics 365 licenses.

Customers that need full-fledged, general purpose workflow/business process automation capabilities should consider purchasing standalone Power Automate licenses. Licensing is supported on both a “per user” basis and a “per flow” basis. Both standalone licenses include the full capabilities on Power Automate.

:::row:::
  :::column:::
    **Power Automate**
  :::column-end:::
  :::column:::
    **Per user**
  :::column-end:::
  :::column:::
    **Per flow**
  :::column-end:::
  :::column:::
    **Seeded Flow**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Licensing scheme**
  :::column-end:::
  :::column:::
    Per user
  :::column-end:::
  :::column:::
    Per flowMinimum purchase of five flows
  :::column-end:::
  :::column:::
    Through Microsoft 365, Dynamics 365, and Power Apps.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    Allow individual users to create unlimited flows based on their unique needs.
  :::column-end:::
  :::column:::
    Implement flows with reserved capacity that serve unlimited users across an organization.
  :::column-end:::
  :::column:::
    Automate business processes and workflows for Microsoft 365, Dynamics 365, and Power Apps.

  :::column-end:::
:::row-end:::


**Additional reading.** For more information on pricing and capabilities of standalone plans, see the [Microsoft Power Apps and Power Automate Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130?azure-portal=true).<br>

There are two ways for individuals to sign up for Power Automate through the web portal:

 -  Anyone can sign up by going to [Microsoft Power Automate](https://flow.microsoft.com/?azure-portal=true), selecting **Try free**, and then completing the sign-up process.
 -  Anyone can sign up by going to Microsoft Power Automate, selecting **Sign-in**, signing in with their work, school or personal email, and accepting the Power Automate terms of use. When a user in your organization signs up for Power Automate using this option, the user will automatically be assigned a Power Automate Free license.<br>‎<br>‎The Power Automate Free Plan is only used for tracking purposes. Enabling or disabling it has no effect on a user's ability to create flows. If the Power Automate Free Plan is disabled, it becomes enabled again when a user logs in.

### Paid features of Power Automate

Individuals can gain access to the paid features of Power Automate in three different ways:

 -  They can individually sign up for a Flow Plan 1 or Flow Plan 2 trial 90 days for free.
 -  They can be assigned a Flow license within the Microsoft 365 admin center.
 -  They can be assigned a Microsoft 365 plan or a Dynamics 365 plan that includes access to the Flow service. See the [Flow pricing page](https://flow.microsoft.com/pricing/?azure-portal=true) for the list of Microsoft 365 and Dynamics 365 plans that include Flow capabilities.

Any individual can try out the paid features of Power Automate for 90 days and incur no costs. However, an organization can fully manage the assignment of its perpetual paid licenses through the Microsoft 365 admin portal. As with the free offerings, if an individual chooses to sign up for the trial, that is a direct relationship between the individual and Microsoft, which may not necessarily be endorsed by the user's company.

### Using environments within Power Automate

An environment is a space to store, manage, and share an organization’s business data, apps, and flows. It also serves as a container to separate apps that may have different roles, security requirements, or target audiences. Power Apps automatically creates a single default environment for each tenant. This environment is then shared by all users in that tenant. As a result, any user can create flows in the default environment. Administrators can use the admin center to create and manage other environments.

Environments provide the following benefits:

 -  **Data locality.** When an environment is created in different region, it's bound to that geographic location. When you create a flow in an environment, that flow is routed to all datacenters in that geographic location. This design also provides a performance benefit. If your users are in Europe, create and use the environment in the Europe region. If your users are in the United States, create and use the environment in the U.S.

    > [!IMPORTANT]
    > If an environment is deleted, then all flows within that environment are also deleted. This rule applies to any items that are created in that environment, including connections, gateways, Power Apps, and more.

 -  **Data loss prevention.** Organizations don't want flows that get data from an internal location (such as OneDrive for Business or a SharePoint list that contains salary information) to post that data publicly (such as to Twitter). To prevent this situation, an organization should use data loss prevention policies and guidelines to control which services can share data within its Power Automate deployment. For example, the SharePoint and OneDrive for Business services can be added to a business data-only policy. Any flows created in this environment can use SharePoint and OneDrive for Business services. However, they can't share data with other services that aren't included in the business data-only policy.
 -  **Isolation boundary for all resources.** Any flows, gateways, connections, custom connectors, and so on, are located in a specific environment. They don't exist in any other environment.‎
 -  **Microsoft Dataverse.** The following options are available if an organization wants to create a flow that inserts data into a service:
    
     -  Insert data into an Excel file, and store the Excel file in a cloud storage account, such as OneDrive.
     -  Create a SQL Database, and then store your data in it.
     -  Use Microsoft Dataverse to store your data.

    > [!NOTE]
    > Every environment can have a maximum of one database for your flows in Microsoft Dataverse. Access to Microsoft Dataverse depends on the license you purchased. Microsoft Dataverse isn't included with the Free license.

Although environments provide many benefits, they also introduce new limitations. The fact that environments are an isolation boundary means that an organization can never have resources that reference resources across environments. For example, you can't create a custom connector in one environment and then create a flow that uses that custom connector in a different environment.
