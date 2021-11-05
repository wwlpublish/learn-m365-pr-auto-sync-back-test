An organization's Exchange environment includes built-in management role groups. It also includes default role assignment policies and built-in user roles for managing end-user activities within Exchange.

The following table identifies the built-in user roles that are available in RBAC to support an organization's Exchange environment.

| **User role**                                                                                | **What end-users can do**                                                                       | **Enabled by default** |
|:-------------------------------------------------------------------------------------------- |:----------------------------------------------------------------------------------------------- |:----------------------:|
| MyContactInformation<br>MyAddressInformation<br>MyMobileInformation<br>MyPersonalInformation | Modify their contact information. Edit address, mobile, and personal information.               |          Yes           |
| MyProfileInformation<br>MyDisplayNam<br>eMyName                                              | Change their name and display name.                                                             |           No           |
| MyDistributionGroups                                                                         | Create, modify, and view distribution groups, and manage members of groups they own.            |           No           |
| MyDistributionGroupMembership                                                                | View and modify their membership in distribution groups, such as by joining or leaving a group. |          Yes           |
| MyCustomApps                                                                                 | View and modify their custom apps.                                                              |          Yes           |
| MyMarketplaceApps                                                                            | View and modify their marketplace apps.                                                         |          Yes           |
| My ReadWriteMailbox Apps                                                                     | This role will allow users to install apps with ReadWriteMailbox permissions.                   |          Yes           |
| MyBaseOptions                                                                                | View and modify basic configuration and access settings for Outlook on the web.                 |          Yes           |
| MyRetentionPolicies                                                                          | View and modify retention tags and retention tag settings.                                      |           No           |
| MyTextMessaging                                                                              | Manage options for text messaging.                                                              |          Yes           |
| MyVoiceMail                                                                                  | Manage options for voice mail.                                                                  |          Yes           |
| MyDiagnostics                                                                                | Complete basic diagnostics on their mailbox.                                                    |           No           |
| MyMailboxDelegation                                                                          | This role enables administrators to delegate mailbox permissions.                               |           No           |
| MyTeamMailboxes                                                                              | Create site mailboxes and connect them to Microsoft SharePoint Services sites.                  |          Yes           |

You can use the EAC to assign default roles to a role assignment policy. To view all user roles available in your organization, you should run the following command in the Exchange Management Shell:

```powershell
Get-ManagementRole | where { $_.IsEndUserRole -eq $true }
```

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.