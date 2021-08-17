Azure AD Connect Health helps an organization monitor and gain insight into its on-premises identity infrastructure and the synchronization services available through Azure AD Connect. It enables an organization to view alerts, performance, usage patterns, and configuration settings. Azure AD Connect Health also enables an organization to maintain a reliable connection to Microsoft 365 by using an agent that's installed on the targeted servers.

:::image type="content" source="../media/using-aad-connect-health-5e38e9c1.png" alt-text="graphic showing an organization with on-premises AD DS and AD FS using Azure AD Connect to monitor its on-premises infrastructure using Azure AD Connect Health":::


The Azure AD Connect Health portal presents the information retrieved from the agent. Using the Azure AD Connect Health portal, an organization can view alerts, performance monitoring, and usage analytics. This information is in one easy-to-use place for your convenience.

While Azure AD Connect Health for AD FS monitors an organization's on-premises AD FS environment, Azure AD Connect Health for Sync monitors and provides information on the synchronizations that occur between the on-premises Active Directory and Azure AD.

Azure AD Connect Health for Sync provides the following set of key capabilities:

 -  View and act on alerts to ensure reliable synchronizations between the on-premises infrastructure and Azure AD.
 -  Email notifications for critical alerts.
 -  View performance data.

To get started with Azure AD Connect Health, an organization should access the [Azure Active Directory Connect Health portal](https://aka.ms/aadconnecthealth?azure-portal=true).

> [!NOTE]
> Azure AD Connect Health is part of Azure AD Premium and requires the necessary licenses to be available.

When Azure AD Connect Health is first accessed, the **Quick Start** page will be displayed. This page enables you to download the appropriate Azure AD Connect Health agent in the **Get tools** section, access documentation, and provide feedback. From the **Quick Start** page, the following information can be accessed:

 -  **Azure Active Directory Connect (Sync).** This option represents the Azure AD Connect servers that are currently monitored by Azure AD Connect Health.
 -  **Active Directory Federation Services.** This option represents all the AD FS services that Azure AD Connect Health is currently monitoring if AD FS is configured. By selecting one of the instances, a window opens with information about that service’s instance. This information includes an overview, properties, alerts, monitoring, and usage analytics.
 -  **Active Directory Domain Services.** This option displays all the Active Directory forests that Azure AD Connect Health is currently monitoring. Different forests can be selected to display information about each forest, such as alerts, monitoring, and the replication status.
 -  **Configure.** This option enables the following settings to be turned On or Off:
    
     -  **Auto update to automatically update the Azure AD Connect Health agent to the latest version.** This option automatically updates the agent on the organization's server to the latest version of the Azure AD Connect Health Agent when they become available. If this option isn't enabled, it should be enabled to automatically install Azure AD Connect updates.
     -  **Allow Microsoft access to your Azure AD directory’s health data for troubleshooting purposes only.** When this option is enabled, Microsoft can see the same data that the organization is seeing. This option, which can help with troubleshooting and assistance with issues, is disabled by default.

**Additional reading.** For more information, see [Monitor your on-premises identity infrastructure and synchronization services in the cloud](https://aka.ms/dqaaps?azure-portal=true).
