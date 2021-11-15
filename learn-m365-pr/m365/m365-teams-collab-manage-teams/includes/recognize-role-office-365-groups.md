When you create a team in Microsoft Teams, on the back end, you're creating a Microsoft 365 Group, the associated SharePoint document library, and a OneNote notebook, along with ties into other Microsoft 365 cloud applications.

If the creator of a team is an owner of an existing public or private group, they can add Teams functionality to the group if it has fewer than 10,000 people and has never been added to Teams. This creates one default General channel in which chat messages, documents, OneNote, and other objects reside.

:::image type="content" source="../media/office-365-groups-new-group.png" alt-text="Screenshot showing how Teams, Azure Active Directory and Microsoft 365 Groups all interconnect." lightbox="../media/office-365-groups-new-group.png":::

> [!NOTE]
> Teams in Government GCC deployments can accomodate up to 25,000 members, and are not subject to the usual 10,000 user limit. However, you can't use @ channel mentions with GCC groups larger than 10,000 members.

Members of Microsoft 365 Groups fall into three roles:

- **Owners** can perform administrative tasks such as adding or removing group members and changing group settings.
- **Members** are regular users who collaborate within a group.
- **Guests** are participants from outside your organization who've been granted access to the group by an administrator.

> [!NOTE]
> Guest users have access to the inviting organization's teams or team resources, but users granted external access do not have access to the inviting organization's teams or team resources.

You can add or remove team members and perform other team-management tasks within the Teams client itself, or outside Teams by using the Microsoft 365 admin center, Microsoft Azure Active Directory (Azure AD), or the Microsoft Teams PowerShell module.

:::image type="content" source="../media/office-365-groups-manage-admin.png" alt-text="Screenshot showing the Manage Teams Administrator area within the Admin Center." lightbox="../media/office-365-groups-manage-admin.png":::

## Learn more

When you're done with a link, use the **Back** arrow in your browser to come back to this page.

- [Microsoft 365 Groups and Microsoft Teams](/microsoftteams/office-365-groups)
