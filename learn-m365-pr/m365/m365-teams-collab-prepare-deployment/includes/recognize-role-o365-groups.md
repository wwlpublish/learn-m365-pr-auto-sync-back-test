When you create a team in Microsoft Teams, you’re creating an Office 365 group and the associated SharePoint document library and OneNote notebook. You're also creating ties into other Office 365 cloud applications.
 
If the person creating the team is an owner of an existing Office 365 public or private group, they can add Teams functionality to the group if it has fewer than 5,000 people and has never been added to Teams. This creates one default General channel in which chat messages, documents, OneNote, and other objects reside.
 
You can add or remove group members just as you would any other group-based security object in Active Directory. Group features and capabilities for your users depend on where you drive membership from. For example, if you remove a member of a team, they are removed from the Office 365 group as well. Removal from the group immediately removes the team and channels from the Teams client. If you remove a person from a group using the Microsoft 365 admin center, they will no longer have access to the other collaborative aspects such as SharePoint Online document library, Yammer groups, or shared OneNote. However, they will still have access to the team’s chat functionality for approximately two hours.

![Interconnections of Teams and Office 365 groups](../media/o365-groups-new-group.png)

## What group types are in Teams?

You can designate a group as either public or private. A public group can be seen or joined by anybody in your organization. A private group’s content can only be seen by the group members, and membership in a private group must be approved by a group owner.

Neither public nor private groups can be accessed by people outside of the organization, unless specifically invited as guests.

## What roles are in Office 365 Groups?

There are three roles in Office 365 Groups:

- **Owners** can perform administrative tasks such as adding or removing group members from the group, moderating shared conversations, and changing group settings. Teams administrators in Office 365 have access to system-wide settings in the Microsoft Teams admin center.
- **Members** are regular users who collaborate within a group. Members have access to all shared features but can’t change group settings. Group members automatically become members of the associated SharePoint site.
- **Guests** are participants from outside your organization who’ve been granted access to the group by an administrator.

You can add or remove team members and perform other team-management tasks within the Teams client itself, or outside Teams by using the Microsoft 365 admin center, Microsoft Azure Active Directory (AD), or the Microsoft Exchange Online PowerShell module.

![Manage Teams administrator view](../media/o365-groups-manage-admin.png)