

With the increase in usage of Microsoft 365 groups and Microsoft Teams, administrators and users need a way to clean up unused groups and teams. A Microsoft 365 groups expiration policy can help remove inactive groups from the system and make things cleaner. The expiration is turned off by default, you have to enable the feature for your organization. 

* When a group expires, all of its associated services (the mailbox, Planner, SharePoint site, team, etc.) are also deleted.

* When a group expires, it is "soft-deleted" which means it can still be recovered for up to 30 days.

Administrators can specify an expiration period and any inactive group, including archived teams, that reach the end of that period, and is not renewed, will be deleted. The expiration period begins when the group is created, or on the date it was last renewed. Group owners will automatically be sent an email before the expiration that allows them to renew the group for another expiration interval. Teams users will see persistent notifications in Teams.

Groups that are actively in use are renewed automatically. Any of the following actions will autorenew a group:

* SharePoint - view, edit, download, move, share, or upload files. (Viewing a SharePoint page does not count as an action for automatic renewal.)
* Outlook - join group, read or write group message from the group, and like a message (Outlook on the web).
* Teams - visiting a teams channel.

## Configure Microsoft 365 groups expiration policy

1. Sign-in to Azure AD Admin Center as a global administrator. 

2. On the left pane select **Groups** section, and then select **Expiration** to open the expiration settings.  

	‎‎:::image type="content" source="../media/azure-active-directory-expiration.png" alt-text="Expiration policy in AzureAD":::  

3. Next, on the **Expiration** page, you can specify: 

	- **Group lifetime (in days)** - Set the group lifetime in days with the default of 180, 365 or custom. The custom setting requires a lifetime of at least 30 days.

	- **Email contact for groups with no owners** - Specify an email address where the renewal and expiration notifications should be sent when a group has no owner. If the group does not have an owner, the expiration emails will go to a specified administrator.

	- **Enable expiration for these Microsoft 365 Groups (All, Selected, None)** – Select the Microsoft 365 Group that you would like to configure this expiration policy for. By your preferences: you can set the policy for all of the groups within your company, only selected groups, or you can also turn it off entirely – and that is done by selecting **None**.

4. To finish the configuration, select **Save** button.  
‎

## Who can configure and use the Microsoft 365 Groups expiration policy?

Group expiration is a feature that is included in an Azure AD Premium subscription. This license is required for the administrator who needs to configure the settings and the members of the affected groups – they all need to have Azure AD Premium licenses assigned to them.

 

There are two types of roles within a company that have different privileges when it comes to expiration policies:

 

| **Role**| **What they can do** |
| - |- |
| Office 365 global admin, User administrator| Create, read, update, or delete the Microsoft 365 Groups expiration policy settings. |
| User| Renew or restore a Microsoft 365 group that they own |


 

## How expiry works with the retention policy

If you have set up a retention policy for groups in the Security and Compliance center, the expiration policy works seamlessly with retention policy. When a group expires, the group's mailbox conversations and files in the group site are retained in the retention container for the specific number of days defined in the retention policy. Users will not see the group, or its content, after expiration however.
 

## How and when a group owner learns if their groups are going to expire

Group owners will only be notified via email. If the group was created via Planner, SharePoint, or any other app, the expiration notifications will always come via email. If the group was created via Teams, the group owner will receive a notification to renew through the activity section. 

At 30 days before the group expires, the group owners (or the email addresses that you specified for groups that don't have an owner) will receive an email allowing them to easily renew the group. If they don't renew it, they'll receive another renewal email 15 days before expiration. If they still haven't renewed it, they will receive one more email notification the day before expiration.

If for some reason none of the owners or admins renew the group before it expires, the admin can still restore the group for up to 30 days after expiration.


The permissions required to restore a group can be any of the following roles:

| **Role**| **Permissions** |
| - |- |
| Global administrator, Group administrator, Partner Tier2 support, and Intune administrator| Can restore any deleted Microsoft 365 Group |
| User administrator and Partner Tier1 support| Can restore any deleted Microsoft 365 Group except those groups assigned to the Company Administrator role |
| User| Can restore any deleted Microsoft 365 Group that they own |


 

For more information, see:

* [Configure the expiration policy for Microsoft 365 Groups](/azure/active-directory/users-groups-roles/groups-lifecycle?azure-portal=true)

* [Restore a deleted Microsoft 365 Group in Azure Active Directory](/azure/active-directory/users-groups-roles/groups-restore-deleted?azure-portal=true)
