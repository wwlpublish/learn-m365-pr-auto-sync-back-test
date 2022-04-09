Search admins can't resolve oversharing issues on their own. Implementing solutions to help prevent it will likely require Global, Compliance, or Security admin access. To learn more, see [Manage access to files and sites](/microsoftsearch/manage-access-files-sites).

Also, we recommend an internal campaign to educate your users about how to properly secure, label, and permission their sites and files.

## Label and limit public sites

**Create custom labels scoped to a security group** to restrict file access to members of a specific group, like executives. When a security group member applies the label, it automatically restricts access to the group. To learn more about custom labels, see [Create and configure sensitivity labels and their policies](/microsoft-365/compliance/create-sensitivity-labels) and [Restrict access to content by using sensitivity labels to apply encryption](/microsoft-365/compliance/encryption-sensitivity-labels).

**Set a default label policy** and require users to label documents and emails. For more information, see [Require users to apply a label to their email and documents](/microsoft-365/compliance/sensitivity-labels-office-apps#require-users-to-apply-a-label-to-their-email-and-documents).

**Define and apply data classifications** that restrict access to all files classified as business sensitive. Sample data will need to be collected to help train new classifiers. For details about prerequisites and permissions, see [Learn about data classification](/microsoft-365/compliance/data-classification-overview).

**Use information barrier policies** to restrict file and site sharing between groups. For example, a finance team that manages confidential projects with a marketing team. These barriers also prevent other aspects of communication and collaboration in Microsoft Teams, SharePoint, and OneDrive. For details, see [Learn about information barriers in Microsoft 365](/microsoft-365/compliance/information-barriers).

**Prevent recent files from appearing** in a user’s profile to minimize file oversharing. Recent files can be disabled on an individual, group (executives or HR, for example), or organization level. To learn more, see [Customizing item insights privacy in Microsoft Graph](/graph/insights-customize-item-insights-privacy) and [Control access to Delve](/sharepoint/delve-for-office-365-admins#control-access-to-delve).

## Manage access at the user level

If you decide not to manage access on an organization or group level, your users can individually manage access to their own files and folders. For more info, see [who a file is shared with in OneDrive or SharePoint](https://support.microsoft.com/office/see-who-a-file-is-shared-with-in-onedrive-or-sharepoint-51bb79a9-b696-410d-a7a7-c320e541272d) and [Can I turn off Delve](https://support.microsoft.com/office/are-my-documents-safe-in-delve-f5f409a2-37ed-4452-8f61-681e5e1836f3#bkmk_optout).

## Manage external sharing

If your users collaborate with people outside of your organization, your SharePoint admin can configure external sharing settings. Depending on your organization's needs and the sensitivity of your data, you can:

- Turn off sharing with people outside your organization
- Require people outside your organization to authenticate
- Restrict sharing to specified domains

For more information, see [Manage sharing settings](/sharepoint/turn-external-sharing-on-or-off).
