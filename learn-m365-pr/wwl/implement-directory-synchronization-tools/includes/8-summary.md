In this module, you examined the prerequisites and installation requirements for the two directory synchronization tools - Azure AD Connect and Azure AD Connect Cloud Sync.

For Azure AD Connect, you examined the options for installing and configuring the tool, and how to monitor the synchronization services using Azure AD Connect Health. You learned about the following requirements and prerequisites for Azure AD Connect that Enterprise admins must consider before they install and configure it in their environments:

 -  Microsoft 365 Tenant requirements
 -  Domain and forest requirements
 -  Operating system and supporting software requirements
 -  Permissions and accounts
 -  Database requirements

You learned that during installation of Azure AD Connect, you can choose to install it using either Express Setup or Custom Setup. This module examined the features found in both the Express and Custom setup options and how they can benefit an organization.

This module also focused on how Azure AD Connect Health helps you monitor and gain insight into your on-premises identity infrastructure. You also learned how Azure AD Connect Health offers you the ability to view alerts, performance, usage patterns, and configuration settings. It also enables you to maintain a reliable connection to Microsoft 365 by using an agent that's installed on the targeted servers.

For Azure AD Connect Cloud Sync, you examined the following prerequisites that must be completed:

 -  Create the Azure AD Connect Cloud Sync gMSA (group Managed Service Account) to run the agent service.
 -  Create a hybrid identity administrator account for your Azure AD tenant that isn't a guest user.
 -  Identify an on-premises server for the provisioning agent with Windows 2016 or later.
 -  Establish high availability that enables the Azure AD Connect Cloud Sync to operate continuously without failure for a long time.
 -  Complete on-premises firewall configurations.

You then learned how to configure Azure AD Connect Cloud Sync by completing the following steps:

1.  Install the Azure AD Connect provisioning agent.
2.  Verify the agent is installed.<br>
3.  Verify the agent is running.
4.  Configure Azure AD Connect Cloud Sync provisioning.
