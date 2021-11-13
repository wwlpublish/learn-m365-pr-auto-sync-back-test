Microsoft 365 stores all user and admin activities in its unified audit log. Need to find if a deleted a file has been shared from OneDrive? You can search the unified audit log in the Microsoft 365 Defender portal. The unified audit log includes user and admin activity for all Microsoft 365 services such as SharePoint Online, Exchange Online, Azure AD, OneDrive, and more. When audit logging is turned on, user and admin activity from your organization is recorded in the audit log and retained for 90 days to one year depending on the license assigned to users.

The length of time that an audit record is retained and searchable depends on your Office 365 or Microsoft 365 enterprise subscription, and specifically the type of license that is assigned to a specific user.

- **Office 365 E3 or Microsoft 365 E3:** Audit records are retained for 90 days.
- **Office 365 E5 or Microsoft 365 E5 or users with a Microsoft 365 E5 Compliance add-on license:** Audit records for Azure Active Directory, Exchange, and SharePoint (OneDrive) activity are retained for one year by default

## Searching

You search the audit log through the Microsoft 365 Defender portal UI. (Options to use PowerShell and the Office 365 Management Activity API are also available.)

:::image type="content" source="../media/audit-log-search.png" alt-text="Screenshot audit log through the Microsoft 365 Defender portal UI." lightbox="../media/audit-log-search.png":::

When searching the audit log, you can:

- Select specific activities or a group of activities to search.
- Pick a start and end date within the maximum searchable date range of 90 days.
- Select one or more users or leave the box blank to return entries for all users.
- Enter a file, folder, or site.

Search results are loaded in increments of 150 events and if more than 5,000 events meet the search criteria, the most recent 5,000 events are displayed.

:::image type="content" source="../media/results.png" alt-text="Screenshot displays Search results are loaded in increments of 150 events up to 5,000 events" lightbox="../media/results.png":::

To see all results, take them offline, or filter them, you can export them to a comma-separated value (CSV) file on your local computer. 50,000 entries total can be downloaded.

## Common OneDrive audit activities

Activities when searching audit logs commonly involve files, folders, sharing, and syncing. There are many activities for each but the main ones are.

- When a file is accessed.
- When a file is copied.
- When a file is deleted.
- When a file is downloaded.
- When a user shares a resource in OneDrive with a user who isn't in your organization's directory.
- When a user creates an anonymous link to a resource.

## Learn more

- [Search the audit log in the Microsoft 365 Defender portal](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance?azure-portal=true)
- [Turn audit log search on or off](/microsoft-365/compliance/turn-audit-log-search-on-or-off?azure-portal=true)
- [Manage audit log retention policies](/microsoft-365/compliance/audit-log-retention-policies?azure-portal=true)
