The following list describes the various on-premises and Azure Active Directory (Azure AD) topologies that support Azure AD Connect Cloud Sync:

 -  **Single forest, single Azure AD tenant**. The simplest topology is a single on-premises forest, with one or multiple domains, and a single Azure AD tenant. For an example of this scenario, see [Tutorial: A single forest with a single Azure AD tenant](/azure/active-directory/cloud-sync/tutorial-single-forest?azure-portal=true).
 -  **Multi-forest, single Azure AD tenant**. A common topology includes multiple AD forests, with one or multiple domains, and a single Azure AD tenant.
 -  **Existing forest with Azure AD Connect, new forest with cloud provisioning**. This scenario is similar to the multi-forest scenario; however. this one involves an existing Azure AD Connect environment and then bringing on a new forest using Azure AD Connect Cloud Sync. For an example of this scenario, see [Tutorial: An existing forest with a single Azure AD tenant](/azure/active-directory/cloud-sync/tutorial-existing-forest?azure-portal=true)
 -  **Piloting Azure AD Connect Cloud Sync in an existing hybrid AD forest**. The piloting scenario involves the existence of both Azure AD Connect and Azure AD Connect Cloud Sync in the same forest. In this scenario, an object should be in scope in only one of the tools. For an example of this scenario, see [Tutorial: Pilot Azure AD Connect cloud sync in an existing synced AD forest](/azure/active-directory/cloud-sync/tutorial-pilot-aadc-aadccp?azure-portal=true).

Organizations should keep the following information in mind when considering these topologies:<br>

 -  Users and groups must be uniquely identified across all forests.
 -  Matching across forests doesn't occur with Azure AD Connect Cloud Sync.
 -  A user or group must be represented only once across all forests.
 -  The source anchor for objects is chosen automatically. It uses ms-DS-ConsistencyGuid if present; otherwise, ObjectGUID is used.
 -  You can't change the attribute that's used for the source anchor.

> [!CAUTION]
> Microsoft doesn't support modifying or operating Azure AD Connect Cloud Sync outside the configurations or actions that are formally documented. Any of these unapproved configurations or actions may result in an inconsistent or unsupported state of Azure AD Connect Cloud Sync. As a result, Microsoft can't provide technical support for such deployments.

### Prerequisites for Azure AD Connect cloud sync

Organizations need the following to use Azure AD Connect Cloud Sync:

 -  A group Managed Service Account (gMSA). Azure AD Connect Cloud Sync supports and uses a gMSA for running the lightweight Cloud Sync agent. A gMSA is a managed domain account that:
    
     -  provides automatic password management.
     -  provides simplified service principal name (SPN) management.
     -  delegates the management to other administrators.
     -  extends this functionality over multiple servers.
 -  Domain Administrator or Enterprise Administrator credentials to create the Azure AD Connect Cloud Sync gMSA (group Managed Service Account) to run the agent service.
 -  A hybrid identity administrator account for your Azure AD tenant that's not a guest user.
 -  An on-premises server for the Cloud Sync agent with Windows 2016 or later. This server should be a tier 0 server based on the [Active Directory administrative tier model](/windows-server/identity/securing-privileged-access/securing-privileged-access-reference-material?azure-portal=true). Installing the Cloud Sync agent on a domain controller is supported.
 -  High availability refers to the Azure AD Connect Cloud Sync's ability to operate continuously without failure for a long time. By having multiple active Cloud Sync agents installed and running, Azure AD Connect Cloud Sync can continue to function even if one agent should fail. It's recommended that organizations have three active agents installed for high availability.
 -  On-premises firewall configurations.
