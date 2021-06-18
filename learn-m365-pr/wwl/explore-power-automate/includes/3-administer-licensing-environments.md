General purpose Power Automate capabilities are licensed on a standalone basis. Limited Power Automate capabilities are also included within Power Apps, Microsoft 365, and Dynamics 365 licenses.

Customers that need full-fledged, general purpose workflow/business process automation capabilities should consider purchasing standalone Power Automate licenses. Licensing is supported on both a “per user” basis and a “per flow” basis. Both standalone licenses include the full capabilities on Power Automate.

:::row:::
  :::column:::
    Power Automate
  :::column-end:::
  :::column:::
    Per user
  :::column-end:::
  :::column:::
    Per flow
  :::column-end:::
  :::column:::
    Seeded Flow
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
    

Per flow

Minimum purchase of 5 flows


  :::column-end:::
  :::column:::
    Through Microsoft 365, Dynamics 365, and Power Apps
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    **Description**
  :::column-end:::
  :::column:::
    Allow individual users to create unlimited flows based on their unique needs
  :::column-end:::
  :::column:::
    Implement flows with reserved capacity that serve unlimited users across an organization
  :::column-end:::
  :::column:::
    Automate business processes and workflows for Microsoft 365, Dynamics 365 , and Power Apps

  :::column-end:::
:::row-end:::


**Additional reading.** For more information on pricing and capabilities of standalone plans, see the [Microsoft Power Apps and Power Automate Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2085130?azure-portal=true).


There are two ways for individuals to sign up for Power Automate through the web portal:

 *  Anyone can sign up by going to [Microsoft Power Automate](https://flow.microsoft.com/?azure-portal=true), selecting **Try free**, and then completing the sign-up process.
 *  Anyone can sign up by going to Microsoft Power Automate, selecting **Sign-in**, signing in with their work, school or personal email, and accepting the Power Automate terms of use. When a user in your organization signs up for Power Automate using this option, the user will automatically be assigned a Power Automate Free license.
    ‎
    ‎The Power Automate Free Plan is only used for tracking purposes. Enabling or disabling it has no effect on a user's ability to create flows. If you disable the Power Automate Free Plan, it becomes enabled again when a user logs in.

### Paid features of Power Automate

Individuals can gain access to the paid features of Power Automate in three different ways:

 *  They can individually sign up for a Flow Plan 1 or Flow Plan 2 trial 90 days for free.
 *  You can assign a Flow license to them within the Microsoft 365 admin center.
 *  The user has been assigned a Microsoft 365 plan or a Dynamics 365 plan that includes access to the Flow service. See the [Flow pricing page](https://flow.microsoft.com/pricing/?azure-portal=true) for the list of Microsoft 365 and Dynamics 365 plans that include Flow capabilities.

Any individual can try out the paid features of Power Automate for 90 days and incur no costs. However, you can fully manage the assignment of the perpetual paid licenses in your organization through the Microsoft 365 admin portal. As with the free offerings, if an individual chooses to sign up for the trial, that is a direct relationship between the individual and Microsoft, which may not necessarily be endorsed by your company.

### Using environments within Power Automate

An environment is a space to store, manage, and share your organization’s business data, apps, and flows. It also serves as a container to separate apps that may have different roles, security requirements, or target audiences. Power Apps automatically creates a single default environment for each tenant. This environment is then shared by all users in that tenant. As a result, any user can create flows in the default environment. Administrators can use the admin center to create and manage other environments.

Environments provide the following benefits:

 *  **Data locality.** When an environment is created in different region, it's bound to that geographic location. When you create a flow in an environment, that flow is routed to all datacenters in that geographic location. This design also provides a performance benefit. If your users are in Europe, create and use the environment in the Europe region. If your users are in the United States, create and use the environment in the U.S.
 *  **Data loss prevention.** As an Administrator, you don't want flows that get data from an internal location (such as OneDrive for Business or a SharePoint list that contains salary information) to post that data publicly (such as to Twitter). Use data loss prevention to control which services can share data within your Power Automate deployment. For example, you can add the SharePoint and OneDrive for Business services to a business data only policy. Any flows created in this environment can use SharePoint and OneDrive for Business services. However, they can't share data with other services that aren't included in the business data only policy.
 *  **Isolation boundary for all resources.** Any flows, gateways, connections, custom connectors, and so on, reside in a specific environment. They don't exist in any other environment.
    ‎
 *  **Common Data Service.** The following options are available if you want to create a flow that inserts data into a service:
    
     *  Insert data into an Excel file, and store the Excel file in a cloud storage account, such as OneDrive.
     *  Create a SQL Database, and then store your data in it.
     *  Use the Common Data Service to store your data.

Although environments provide many benefits, they also introduce new limitations. The fact that environments are an isolation boundary means that you can never have resources that reference resources across environments. For example, you may not create a custom connector in one environment and then create a flow that uses that custom connector in a different environment.
