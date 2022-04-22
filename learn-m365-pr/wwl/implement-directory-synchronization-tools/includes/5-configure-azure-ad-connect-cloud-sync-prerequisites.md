Organizations must complete the following prerequisites before installing Azure AD Connect Cloud Sync:

 -  Create the Azure AD Connect Cloud Sync gMSA (group Managed Service Account) to run the agent service.
 -  Create a hybrid identity administrator account for your Azure AD tenant that isn't a guest user.
 -  Identify an on-premises server for the provisioning agent with Windows 2016 or later. This server should be a tier 0 server based on the Active Directory administrative tier model. Installing the agent on a domain controller is supported.
 -  Establish high availability that enables the Azure AD Connect Cloud Sync to operate continuously without failure for a long time. By having multiple active agents installed and running, Azure AD Connect Cloud Sync can continue to function even if one agent should fail. Microsoft recommends having three active agents installed for high availability.
 -  Complete on-premises firewall configurations.

The key components of these prerequisites are outlined in the following sections.

### Group managed service account (gMSA)

A gMSA is a managed domain account that provides automatic password management, simplified service principal name (SPN) management, and the ability to delegate the management to other administrators. It also extends this functionality over multiple servers. Azure AD Connect Cloud Sync supports and uses a gMSA for running the lightweight Cloud Sync agent. You'll be prompted for administrative credentials during setup when you create this account. The account will appear as domain\\provAgentgMSA$.

You must complete the following steps to create a gMSA account:

1.  The Active Directory schema in the gMSA domain's forest must be updated to Windows Server 2012 or later.
2.  Modules for [PowerShell Remote Server Administration Tools](/windows-server/remote/remote-server-administration-tools?azure-portal=true) should be installed on a domain controller. RSAT lets IT admins manage Windows Server roles and features from a Windows 10 PC. RSAT includes Server Manager, Microsoft Management Console (mmc) snap-ins, consoles, Windows PowerShell cmdlets and providers, and some command-line tools for managing roles and features that run on Windows Server.
3.  At least one domain controller in the domain must be running Windows Server 2012 or later.
4.  A domain joined server where the agent is being installed needs to be either Windows Server 2016 or later.

### Hybrid identity administrator account

One of the Azure AD Connect Cloud Sync prerequisites requires that you create a cloud-only hybrid identity administrator account for your Azure AD tenant. This account can't be a guest user. Creating this account includes the following steps:

1.  Create a user account in the Azure AD portal. This account must be assigned hybrid identity administrator permissions on your Azure AD tenant. This way, you can manage the configuration of your tenant if your on-premises services fail or become unavailable. Completing this step is critical to ensure that you don't get locked out of your tenant.
2.  Add one or more custom domain names to your Azure AD tenant. Your users can sign in with one of these domain names.

### Domain-joined server for the provisioning agent

Complete the following steps to identify an on-premises server for the provisioning agent with Windows 2016 or later:

1.  Identify a domain-joined host server running Windows Server 2016 or greater with a minimum of 4-GB RAM and .NET 4.7.1+ runtime.<br>
2.  The PowerShell execution policy on the local server must be set to Undefined or RemoteSigned.<br>
3.  If there's a firewall between your servers and Azure AD, see the following section on **Firewall and proxy requirements**.<br>

### Firewall and proxy requirements

If there's a firewall between your servers and Azure AD, you must configure the following items:

 -  Ensure that agents can make *outbound* requests to Azure AD over the following ports:
    
    :::row:::
      :::column:::
        **Port number**
      :::column-end:::
      :::column:::
        **How it's used**
      :::column-end:::
    :::row-end:::
    :::row:::
      :::column:::
        80
      :::column-end:::
      :::column:::
        Downloads the certificate revocation lists (CRLs) while validating the TLS/SSL certificate.
      :::column-end:::
    :::row-end:::
    :::row:::
      :::column:::
        443
      :::column-end:::
      :::column:::
        Handles all outbound communication with the service.
      :::column-end:::
    :::row-end:::
    :::row:::
      :::column:::
        8080 (optional)
      :::column-end:::
      :::column:::
        Agents report their status every 10 minutes over port 8080, if port 443 is unavailable. This status is displayed in the Azure AD port.
      :::column-end:::
    :::row-end:::
    
 -  If your firewall enforces rules according to the originating users, open these ports for traffic from Windows services that run as a network service.

### Other considerations

Other issues that you should consider when completing the Azure AD Cloud Sync prerequisites include:

 -  **NTLM requirement**. You shouldn't enable NTLM on the Windows Server that's running the Azure AD Connect Provisioning Agent. If NTLM is enabled, you must disable it.
 -  **Delta synchronization**. Known limitations with delta synchronization include:
    
     -  Group scope filtering for delta sync doesn't support more than 50,000 members.
     -  When you delete a group that's used as part of a group scoping filter, users who are members of the group don't get deleted.
     -  When you rename the OU or group that's in scope, delta sync won't remove the users.
 -  **Provisioning logs**. Provisioning logs don't clearly differentiate between create and update operations. You may see a create operation for an update operation and an update operation for a create operation.
 -  **Group renaming or OU renaming**. If you rename a group or OU in AD that's in scope for a given configuration, the cloud sync job won't recognize the name change in AD. As a result, the job won't go into quarantine and will remain healthy.
 -  **Scoping filter**. When using an OU scoping filter:
    
     -  You can only sync up to 59 separate OUs for a given configuration.
     -  Nested OUs are supported. In other words, you can sync an OU that has 130 nested OUs, but you can't sync 60 separate OUs in the same configuration.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”