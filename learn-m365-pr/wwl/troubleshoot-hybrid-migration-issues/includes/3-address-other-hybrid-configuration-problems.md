Hybrid deployments can make it a little more complicated to support free/busy information and public folders. Exchange fully supports both these features and access to them from both on-premises and cloud mailboxes, but you might need to troubleshoot that access.

In your digital camera manufacturing company, Exchange is a heavily used collaboration tool. Team members often check each other's calendars and use them to schedule meetings. They also regularly use public folders to manage projects and their documents. Since you've started your migration, you've noticed that mailboxes in Exchange Online can't access free/busy information for mailboxes that haven't yet been moved. Also, these mailboxes can't access several public folders, which will be moved in the final phase of your migration. You need to enable this access as quickly as possible.

Here, you'll learn how Exchange hybrid deployments support access to free/busy information and public folders from any location, in the cloud or on-premises.

## Troubleshoot free/busy information for hybrid deployments

Exchange and Outlook users are familiar with sharing their calendar and appointments within their organization so that it's easy to schedule meetings. In a hybrid deployment, this free/busy information is stored in both on-premises mailboxes and cloud mailboxes, depending on where mailboxes were created and whether they've been migrated yet.

When you use the Hybrid Configuration Wizard (HCW) to set up your Exchange hybrid deployment, it creates all the necessary objects and configurations to enable all users to check any user's calendar, regardless of where the mailbox is located. When lookups are successful, this process is entirely transparent to the user and appointments can be made without knowing whether your colleague's mailbox is on-premises or in the cloud. However, because the lookup process executed behind the scenes is complex, troubleshooting errors can be difficult

> [!TIP]
> If a free/busy lookup in a hybrid deployment fails, it's helpful to determine the direction of the lookup: If the user's mailbox is in Exchange Server, and they were adding an Exchange Online user to a meeting request when the error arose, this lookup is on-premises to cloud. If the user's mailbox is in Exchange Online, and they were adding an Exchange Server user to a meeting request when the error arose, this lookup is cloud to on-premises. 

### Federation trusts required for free/busy lookups

The HCW creates two trusts to support free/busy information sharing. The trusts are required to ensure that on-premises users can be authenticated on the cloud-based Exchange servers and that users with accounts in Azure Active Directory (Azure AD) can be authenticated on-premises:

- A federation trust between the on-premises Active Directory Forest and the Azure Authentication system.
- A federation trust between the cloud Azure Active Directory (Azure AD) system and the Azure Authentication system.

You can check the trusts that are in place by running the following PowerShell command, on the on-premises Exchange server and in Cloud Shell:

```powershell
Get-FederationTrust
```

If free/busy information stops working for all users, there might be a problem with the federation trusts. In this case, on-premises users will only be able to see free/busy information for other on-premises users and not for Exchange Online mailboxes. Exchange Online users will only be able to see free/busy information for other Exchange Online users.

You can investigate further by using the PowerShell `Test-FederationTrust` cmdlet:

```powershell
Test-FederationTrust
```

If you receive an error stating that the delegation token failed to validate, you can refresh the metadata on the federation trust to resolve the problem by using this PowerShell command:

```powershell
Get-FederationTrust | Set-FederationTrust -RefreshMetadata
```

### Mailboxes and the properties that support free/busy information

To provide a seamless lookup system, on-premises mailboxes must have corresponding objects in the cloud Exchange organization. These objects are created by the HCW and modified when you migrate a mailbox from one location to the other.

For users whose mailbox is on-premises:

- In Exchange Server, there is a mailbox object.
- In Exchange Online, there is a mail-enabled user.

Both these objects have a primary email address set to the public-facing address, such as **serena.davis@contoso.com**. They also have a secondary email address with a *.onmicrosoft.com* domain, such as **serena.davis@contoso.mail.onmicrosoft.com**. The mail-enabled user also has an external email address set to the public facing address.

In Exchange Server, you can check the mailbox addresses with this PowerShell command:

```powershell
(Get-Mailbox serena.davis@contoso.com).EmailAddresses
```

In Exchange Online, you can check the mail-enabled user addresses with this PowerShell command:

```powershell
(Get-MailUser serena.davis@contoso.com).EmailAddresses
```

For users whose mailbox is in Exchange Online:

- In Exchange Server, there is a remote mailbox object.
- In Exchange Online, there is a mailbox object.

The mailbox in Exchange Online has a primary email address set to the public-facing address, such as **serena.davis@contoso.com**. They also have a secondary email address with a *.onmicrosoft.com* domain, such as **serena.davis@contoso.mail.onmicrosoft.com**. The remote mailbox object in Exchange server, has the same primary address, but a remote mailbox target address in the *.onmicrosoft.com* domain, such as **serena.davis@contoso.mail.onmicrosoft.com**.

In Exchange Online PowerShell, you can check the mailbox addresses with this command:

```powershell
(Get-MailUser serena.davis@contoso.com).EmailAddresses
```

In Exchange Server, you can check the remote mailbox addresses with these PowerShell commands:

```powershell
Get-RemoteMailbox serena.davis@contoso.com | FT PrimarySMTPAddress,RemoteRoutingAddress
```

If any of the email addresses are not configured correctly, you can use PowerShell to correct them. For example, if the remote mailbox object has the wrong target address, you can fix it with this command:

```powershell
Set-RemoteMailbox -Identity serena.davis@contoso.com -RemoteRoutingAddress serena.davis@contoso.mail.onmicrosoft.com
```

> [!NOTE]
> For more information about free/busy information troubleshooting in Exchange hybrid deployments, see the **Demystifying Hybrid Free/Busy** links in the Learn more section below.

## Troubleshoot access to public folders in hybrid deployments

Public folders are locations where Outlook users can take part in public discussions or view shared content within their Exchange hierarchy. Public folders are supported in both Exchange Server on-premises and Exchange Online, but they are not automatically synchronized in a hybrid deployment. After completing the HCW, Exchange Server users will only be able to access on-premises public folders and Exchange Online users will only be able to access cloud-based public folders.

The method you use to troubleshoot access to public folders in a hybrid deployment depends on the direction of that access: on-premises to cloud or cloud to on-premises.

### Troubleshoot access to on-premises public folder from Exchange Online

When you run the HCW, Azure AD Connect is configured to synchronize mail-enabled public folders to Exchange Online so that cloud users can send emails to those public folders. To check this synchronization, first list the public folders by running this PowerShell command on the Exchange Server on-premises:

```powershell
Get-Mailbox -PublicFolder
```

Azure AD Connect creates a mail enabled user in Azure AD for each of those public folders. This command, run in Exchange Online PowerShell, should show a **MailUser** object for each public folder:

```powershell
GetMailUser
```

Public folder synchronization is configured by downloading and executing a PowerShell script named **Sync-ModernMailPublicFolders.ps1**. You can download this script from the link in the **Learn more** section below. Execute the script with this command:

```powershell
.\Sync-ModernMailPublicFolders.ps1 -Credential (Get-Credential) -CsvSummaryFile:sync_summary.csv
```

The script creates a comma separated log file at the location that you specified in the `-CsvSummaryFile` parameter. If Exchange Online users can't access public folders, you can begin your investigations by examining this file to see what happened during the synchronization. The script should be executed once a day to keep public folders synchronized.

Even when public folders have been synchronized, Exchange Online users will only be able to access those folders if they have a corresponding MailUser object in the on-premises Exchange Server organization. You can find out which users don't have such an object by running this command in Exchange Online PowerShell:

```powershell
Get-Mailbox | ?{$_.IsDirSynced -eq $false}
```

Finally, you can check whether the Exchange Online organization is configured to access on-premises public folders. Execute this command in Exchange Online PowerShell:

```powershell
Get-OrganizationConfig | FL PublicFoldersEnabled
```

The command should return `Remote` for the `PublicFoldersEnabled` value. If it returns Local then Exchange Online users will not be able to see on-premises public folders.

To fix the problem, execute the command below and include all your public folders in the list at the end:

```powershell
Set-OrganizationConfig -PublicFoldersEnabled Remote -RemotePublicFolderMailboxes PFMailbox1,PFMailbox2,PFMailbox3
```

### Troubleshoot access to cloud public folders from Exchange Server

If you have public folders in Exchange Online, and want them to be accessible for on-premises users, you must run PowerShell scripts to create corresponding objects in Active Directory and Exchange Server. You can download these scripts from the link in the **Learn more** section below

The first script, called **Sync-MailPublicFoldersCloudToOnPrem.ps1**, creates an object in the on-premises Active Directory to represent each public folder in Exchange Online:

```powershell
Sync-MailPublicFoldersCloudToOnprem.ps1 -Credential (Get-Credential)
```

The second script, called **Import-PublicFolderMailboxes.ps1**, configures the imported objects as remote public folders:

```powershell
Import-PublicFolderMailboxes.ps1 -Credential (Get-Credential)
```

These scripts should be run daily to maintain synchronization.

Finally, you must configure remote public folder mode in your Exchange Server on-premises organization:

```powershell
Set-OrganizationConfig -PublicFoldersEnabled Remote
```

### Resolve Naming Conflicts

When you run the `Sync-ModernMailPublicFolders.ps1` script, as described above, you might get the following error message:

```powershell
Active Directory operation failed on PU1PR04A03DC006.APCPR04A003.prod.outlook.com. 
The object 'CN=Marketing,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange Hosted Organizations,DC=APCPR04A003,DC=prod,DC=outlook,DC=com' already exists.
```

This error shows that there is an object with the same name as the public folder already in Exchange Online. To diagnose which object is in conflict, run this command with the distinguish name reported in the above error:

```powershell
Get-Recipient 'CN=Marketing,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange Hosted Organizations,DC=APCPR04A003,DC=prod,DC=outlook,DC=com'
```

Make a note of the name of this object. To resolve the error, rename the on-premises object by running this command on the Exchange Server:

```powershell
Get-MailPublicFolder \Marketing | Set-MailPublicFolder -Name Marketing_PF
```

## Learn more

- [Demystifying Hybrid Free/Busy: what are the moving parts?](https://techcommunity.microsoft.com/t5/exchange-team-blog/demystifying-hybrid-free-busy-what-are-the-moving-parts/ba-p/607704)
- [Demystifying Hybrid Free/Busy: Finding errors and troubleshooting](https://techcommunity.microsoft.com/t5/exchange-team-blog/demystifying-hybrid-free-busy-finding-errors-and-troubleshooting/ba-p/607727)
- [Free/busy lookups stop working in a cross-premises environment or in an Exchange Server hybrid deployment](/exchange/troubleshoot/calendars/freebusy-lookups-stop-working)
- [Exchange 2013/2016 Public Folders Migration Scripts](https://www.microsoft.com/download/details.aspx?id=54855)
- [Configure Exchange Server public folders for a hybrid deployment](/exchange/hybrid-deployment/set-up-modern-hybrid-public-folders)
- [Mail-enabled Public Folders - directory sync from EXO to On-Prem script](https://www.microsoft.com/download/details.aspx?id=52037)
- [How to configure Exchange Online public folders for a hybrid deployment](/exchange/hybrid-deployment/set-up-exo-hybrid-public-folders)
- [Troubleshooting mail enabled public folder synchronization failures when using PowerShell script](/exchange/troubleshoot/public-folders/mepf-sync-failures-script)