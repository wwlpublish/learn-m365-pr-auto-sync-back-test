All group membership must be managed in your on-premises Active Directory once you use Azure AD Connect to implement directory synchronization between your on-premises AD and Azure AD.

Directory synchronization of both users and groups in Microsoft 365 is similar. As with users, groups and their membership in Active Directory are synchronized from on-premises AD to Azure AD. And similar to the user writeback feature, group writeback also writes Microsoft 365 groups from Azure AD back to on-premises AD. Group writeback is included as an optional feature in Azure AD Connect.

To enable group writeback, you must complete the following steps:

 *  Run Exchange 2013 CU8 or later, or Exchange 2016 to recognize this new group type.
 *  Create the OU and appropriate permissions required for group writeback in Active Directory. To complete this task, Azure AD Connect has a built-in cmdlet, **Initialize-ADSyncGroupWriteBack**, which automatically prepares Active Directory.

After the synchronization completes, Microsoft 365 groups will appear in the on-premises container that you selected during the configuration. They'll also be represented as distribution groups in the on-premises Active Directory.

> [!NOTE]
> The Group writeback feature doesn't involve security groups or distribution groups.

The synchronized groups won't immediately show up in your on-premises Exchange Global Address List. However, you can use either of the following cmdlets to quickly make them available:

 *  Run the **Update-Recipient** cmdlet.
 *  Run either the **Update-AddressList** or **Update-GlobalAddressList** cmdlet to force the synchronized groups to appear; however, these cmdlets will require more cycles on the servers running Exchange Server.

When groups are synchronized from Azure AD to on-premises Active Directory, their group membership is also synchronized if the user accounts were created in the on-premises AD. User accounts created in Azure AD aren't included. The name attribute of the synchronized groups is filled with the ObjectGUID attribute instead of a humanly readable name.

**Additional reading.** For more information, see the following article on [Azure AD Connect group writeback](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-group-writeback?azure-portal=true).

The following graphic shows that new Office 365 groups receive a distribution list on-premises for routing purposes whenever group writeback is activated.

:::image type="content" source="../media/m365-group-receives-dist-list-during-group-writeback-c8b76b1f.jpg" alt-text="graphic shows that when group writeback is activated new Microsoft 365 groups receive a distribution list on-premises for routing purposes.":::
