This module focuses on managing users and groups when implementing directory synchronization. You'll learn that following the synchronization of your on-premises Active Directory objects with Microsoft 365, you can no longer manage those objects using the Microsoft 365 admin center or the Exchange Online admin center (EAC). The reason for this restriction is that all synchronized attributes aren't synchronized back to your on-premises environment.

You'll also learn that all group membership must be managed in your on-premises Active Directory following directory synchronization. Directory synchronization of both users and groups in Microsoft 365 is similar. This module shows that groups and their membership in Active Directory are synchronized from on-premises AD to Azure AD. And similar to the user writeback feature, you'll learn that group writeback also writes Microsoft 365 groups from Azure AD back to on-premises AD.

This module also examines how Azure AD Connect automatically creates Azure AD Connect Sync Security Groups to:

 -  delegate control in Azure AD Connect to other users
 -  assign a user temporary permission to run a manual synchronization
 -  troubleshoot directory synchronization issues using Azure AD Connect

The module concludes with a discussion on troubleshooting directory synchronization. When Enterprise Administrators troubleshoot directory synchronization issues, they must analyze logs for errors and remediate synchronization errors with their directory synchronization tool.

After completing this module, you'll be able to:

 -  Ensure your users and groups synchronize efficiently.
 -  Use Azure AD Connect Sync Security Groups to help maintain directory synchronization.
 -  Troubleshoot directory synchronization using various troubleshooting tasks and tools.
