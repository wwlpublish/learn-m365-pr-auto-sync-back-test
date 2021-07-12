Connectors are what make Azure AD Application Proxy possible. They're lightweight agents that sit on-premises and support the outbound connection to the Application Proxy service. Connectors must be installed on a Windows Server that has access to the backend application. Connectors can be organized into connector groups, with each group handling traffic to specific applications. Connectors load-balance automatically, and they can help to optimize an organization's network structure.

To deploy Application Proxy successfully, at least one connector is needed, but two or more are recommended for greater resiliency. Install the connector on a Windows Server 2012 R2 or 2016 machine. The connector must communicate with the Application Proxy service and the on-premises applications that are published.

The rest of this unit examines how to:

 -  Install and register a connector.
 -  Verify that the connector installed correctly.
 -  Maintain connectors.
 -  Create connector groups.

### Install and register a connector

Complete the following steps to install and register a connector:

1.  Sign in as an administrator in the [Azure portal](https://portal.azure.com/?azure-portal=true).
2.  Your current directory appears under your username in the top-right corner. If you must change directories, select that icon.
3.  Go to **Azure Active Directory** &gt; **Application Proxy**.
4.  Select **Download Connector**.
5.  Run **exe** on the server that was prepared according to the prerequisites.
6.  Follow the instructions in the wizard to install the connector. During installation, you're prompted to register the connector with the Application Proxy of your Azure AD tenant.
    
     -  Provide your Azure AD global administrator credentials. Your global administrator tenant may be different from your Microsoft Azure credentials.
     -  Make sure the admin who registers the connector is in the same directory where you enabled the Application Proxy service. For example, if the tenant domain is contoso.com, the admin should be admin@contoso.com or any other alias on that domain.
     -  If **IE Enhanced Security Configuration** is set to **On** on the server where you're installing the connector, you may not see the registration screen. To get access, follow the instructions in the error message. Make sure that Internet Explorer Enhanced Security is turned.

> [!IMPORTANT]
> For high availability purposes, at least two connectors should be deployed. Each connector must be registered separately.

### Verify that the connector installed correctly

An organization can confirm that a new connector installed correctly by checking for it in either the Azure portal or on its server.

In the Azure portal, sign in to the organization's tenant and navigate to **Azure Active Directory** &gt; **Application Proxy**. All of the organization's connectors and connector groups appear on this page. Select a connector to see its details or move it into a different connector group.

On the organization's server, check the list of active services for the connector and the connector updater. If the following services don't immediately start, then turn them on:

 -  **Microsoft AAD Application Proxy Connector** enables connectivity.
 -  **Microsoft AAD Application Proxy Connector Updater** is an automated update service. The updater checks for new versions of the connector and updates the connector as needed.

**Additional reading.** For information about connectors and how they stay up to date, see [Understand Azure AD Application Proxy connectors](/azure/active-directory/manage-apps/application-proxy-connectors).

### Maintain connectors

The connectors and the service take care of all the high availability tasks. They can be added or removed dynamically. Each time a new request arrives it's routed to one of the connectors that's currently available. If a connector is temporarily unavailable, it won't respond to this traffic.

The connectors are stateless and have no configuration data on the machine. The only data they store are the settings for connecting the service and its authentication certificate. When they connect to the service, they pull all the required configuration data and refresh it every couple of minutes. Connectors also poll the server to find out whether there's a newer version of the connector. If one is found, the connectors update themselves.

Connectors can be monitored from the machine they're running on using either the event log or performance counters. Their status can also be viewed from the **Application Proxy** page of the Azure portal.

Connectors that are unused don't have to be manually deleted. When a connector is running, it remains active as it connects to the service. Unused connectors are tagged as *inactive* and are removed after 10 days of inactivity. To uninstall a connector, uninstall both the Connector service and the Updater service from the server. Restart the computer to fully remove the service.

### Create connector groups

Connector groups enable an organization to assign specific connectors to serve specific applications. Several connectors can be grouped together, and then each application can be assigned to a group.

Connector groups make it easier to manage large deployments. Because location-based connector groups can be created to serve only local applications, they can improve latency for tenants that have applications hosted in different regions.
