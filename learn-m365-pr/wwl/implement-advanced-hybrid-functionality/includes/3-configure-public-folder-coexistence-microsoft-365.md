A hybrid Exchange deployment also supports coexistence with on-premises Public Folders. Coexistence enables Messaging administrators to configure their cloud mailboxes to access Public Folders located on their local Exchange servers. This design is required during migration if an organization uses Public Folders. There are two types of public folders:

 -  **Legacy Public Folders.** Public Folders on Exchange Server 2007 or 2010 that are located in a Public Folder database.
 -  **Modern Public Folders.** Public Folders on Exchange Server 2013 or later that are located in a Public Folder mailbox.

For Public Folder coexistence with Microsoft 365, an organization must configure Exchange Online to access its on-premises Public Folders that are located on its Exchange servers. Outlook clients with mailboxes located in Exchange Online can access the on-premises Public Folders using the local Autodiscovery process and the Outlook Anywhere protocol.<br>

The Public Folder proxy mailbox SMTP addresses will be returned by Exchange Online to the Outlook client. The client then uses the Autodiscover process to find and establish a direct connection to Public Folders hosted in the on-premises Exchange environment.

### Prerequisites for Public Folder coexistence

An organization must satisfy the following requirements to configure Public Folder coexistence with Microsoft 365:<br>

 -  Azure AD Connect must provide directory synchronization between the organization's on-premises environment and Microsoft 365.
 -  A hybrid Exchange deployment is required to enable email forwarding between on-premises Exchange Server and Exchange Online, and for all other functionality.
 -  The DNS records used for Autodiscover (for example, autodiscover.adatum.com) must reference an on-premises end point.
 -  Outlook Anywhere must be enabled and functional on the on-premises Exchange servers.
 -  Implementing Public Folder coexistence may require you to fix conflicts during the import procedure. Conflicts can occur for various reasons, such as non-routable email addresses assigned to mail-enabled Public Folders, conflicts with other users and groups in Microsoft 365, and other attributes.
 -  In Exchange 2010, Messaging administrators must be a member of the Organization Management or Server Management role groups. These roles enable Messaging administrators to create and configure mailbox databases and mailboxes.
 -  In Exchange Online, Messaging administrators must be a member of the Organization Management role group.
 -  If your Public Folders are on Exchange 2010, then you must install the Client Access Server role on all mailbox servers that have a Public Folder database. Doing so starts the Microsoft Exchange RpcClientAccess service, which allows for all clients to access Public Folders.

### Prerequisites for legacy Public Folder coexistence

When planning for legacy Public Folder coexistence for Exchange Server 2010, you should consider the following items:

 -  Each server that hosts a Public Folder database requires the Client Access services (CAS) role to be installed. You must verify if other resources, such as memory or CPUs, are needed.
 -  You must create one mailbox database per Exchange server that holds Public Folder databases (that is one proxy Public Folder mailbox per Public Folder database server).

If an organization's on-premises Exchange environment uses modern Public Folders, it doesn't need to plan for these extra steps.

### Configuration steps for Public Folder coexistence<br>

Once the prerequisites are satisfied, Public Folder coexistence can be configured by completing the following steps:

> [!NOTE]
> If you use Public Folders on Exchange 2013 or later, skip to Step 5. If you host Public Folders on Exchange 2010, start with Step 1.

1.  Create an empty mailbox database on each Public Folder server by running the following PowerShell command:
    
    ```powershell
    New-MailboxDatabase -Server <pfservername> -Name <newdbforpf> -IsExcludedFromProvisioning $true
    ```
    
    This command excludes the mailbox database from the mailbox provisioning load balancer, and it prevents new mailboxes from automatically being added to this database.
2.  Enable AutoDiscover to return the proxy Public Folder mailboxes by running the following PowerShell command:
    
    ```powershell
    Set-MailboxDatabase <newdbforpfs> -RPCClientAccessServer <PFServer-Name_with_CASRole>
    ```
3.  Create a proxy mailbox within the new mailbox database and hide the mailbox from the address book by running the following PowerShell commands:
    
    ```powershell
    New-Mailbox -Name <pfmailbox1> -Database <newdbforpf>
    Set-Mailbox -Identity <pfmailbox1> -HiddenFromAddressListsEnabled $true
    ```
    
    The SMTP of this mailbox is returned by AutoDiscover as the DefaultPublicFolderMailbox SMTP, so that when you resolve, the SMTP client can reach the legacy exchange server for Public Folder access.
4.  Repeat the preceding steps for every Public Folder server in your organization.<br>
5.  The final step in this procedure is to configure the Exchange Online organization and to allow access to the legacy on-premises Public Folders. It's important that the previously created proxy Public Folder mailboxes have been synchronized to Exchange Online by directory synchronization.<br><br>To enable the Exchange Online organization to access the on-premises Public Folders, you must point to all the proxy Public Folder mailboxes that you created for Exchange Server 2010, or to your Public Folder mailboxes located on Exchange 2013 or later. You should run the following PowerShell command in Exchange Online to complete this task:
    
    ```powershell
    Set-OrganizationConfig -PublicFoldersEnabled Remote -RemotePublicFolderMailboxes PFMailbox1, PFMailbox2 ,…
    ```

### Synchronize mail-enabled Public Folders

Because AADSync doesn't synchronize mail-enabled Public Folders to Exchange Online, all email enabled Public Folders must be synchronized manually using the [Sync-MailPublicFolders.ps1 script](https://www.microsoft.com/download/details.aspx?id=46381).
