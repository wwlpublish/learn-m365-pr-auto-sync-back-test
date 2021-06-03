**Search-UnifiedAuditLog** is the underlying cmdlet used to search the audit log within the Microsoft 365 compliance center. Administrators who prefer using Windows PowerShell can use it to search the Microsoft 365 audit log. They can use this cmdlet instead of using the Audit log search page in the Microsoft 365 compliance center.

> [!TIP]
> Because **Search-UnifiedAuditLog** is an Exchange Online cmdlet, it must be run in a remote PowerShell session that's connected to your Exchange Online organization.

Although **Search-UnifiedAuditLog** is an Exchange Online cmdlet, it can still search for events from SharePoint Online, OneDrive for Business, Azure Active Directory, and other Microsoft 365 services. It can be used to search for all events in a specified date range. You can also filter the results based on specific criteria, such as the user who completed the action, the action, or the target object.

Organizations can programmatically download data from the Microsoft 365 audit log. In doing so, it's recommended that they use the Microsoft 365 Management Activity API instead of using a PowerShell script. The Microsoft 365 Management Activity API is a REST web service that can be used to develop operations, security, and compliance monitoring solutions for an organization.

**Additional reading.** For more information, see [Microsoft 365 Management Activity API](https://msdn.microsoft.com/office-365/office-365-management-activity-api-reference?azure-portal=true).
