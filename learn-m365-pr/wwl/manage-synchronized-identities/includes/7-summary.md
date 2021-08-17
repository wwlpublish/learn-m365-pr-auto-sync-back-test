This module focused on post-synchronization maintenance of users and groups once you implemented Azure AD Connect. You learned that following the synchronization of your on-premises Active Directory objects with Microsoft 365, you can no longer manage those objects using the Microsoft 365 admin center or the Exchange Online admin center (EAC). The reason for this restriction is that all synchronized attributes aren't synchronized back to your on-premises environment.

In this module, you learned that all group membership must be managed in your on-premises Active Directory once you use Azure AD Connect to implement directory synchronization between your on-premises AD and Azure AD. Directory synchronization of both users and groups in Microsoft 365 is similar. You learned that groups and their membership in Active Directory are synchronized from on-premises AD to Azure AD. And similar to the user writeback feature, you learned that group writeback also writes Microsoft 365 groups from Azure AD back to on-premises AD.

Finally, you learned that Azure AD Connect automatically creates Azure AD Connect Sync Security Groups to:

 -  delegate control in Azure AD Connect to other users
 -  assign a user temporary permission to run a manual synchronization
 -  troubleshoot directory synchronization issues using Azure AD Connect

The module concluded with a discussion on troubleshooting directory synchronization. You learned that when troubleshooting directory synchronization issues, Enterprise Administrators must analyze logs for errors and remediate synchronization errors with the Azure AD Connect tool itself.
