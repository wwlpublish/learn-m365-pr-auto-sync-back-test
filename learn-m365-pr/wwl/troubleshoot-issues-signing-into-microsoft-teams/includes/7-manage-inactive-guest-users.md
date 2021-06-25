You can create guest users by using the Azure Active Directory admin center. When you create a guest user, you use the **Invite user** option in. When you create a guest account this way:

- The user is sent an invitation to collaborate. 
- A user account of User type: Guest is created in Azure AD for the guest 
- The user account has the user’s own email address as a prefix to your domain suffix. Example: `james_adatum.com#EXT#@Contoso.com`

It’s important, from a security standpoint, to audit guest accounts if they’re infrequently or never used. You might decide to remove these accounts. 

It’s also important to audit invitations that haven’t been responded to. This might be an indication that the wrong user was targeted. 

## Audit invitations sent but not used 

Guest user accounts created with an invitation are marked with **Creation type: Invitation**. To determine which users were invited as guests, filter the list of displayed users in the Azure Active Directory admin center by **Creation type: Invitation**. 

To verify whether a user has accepted the invite, add the **Invitation state** column to the display. Those users that accepted their invites are displayed with an **Invitation state** of **Accepted**. Those that have not display **Pending acceptance**.

:::image type="content" source="../media/guest-invite.png" alt-text="A screenshot that displays the Azure Active Directory admin center All users page. The administrator has filtered for Creation type: guest. Three users are displayed, one of which has Invitation state: Accepted. ":::

You can now choose whether to remove the users with pending invitation states. 

## Audit inactive accounts

Inactive accounts present a security risk. You should periodically check which accounts are being unused. One approach is to review the sign-in history for a user account. You can access this information in the Azure Active Directory admin center:

1. Select the appropriate user, and then select the Sign-ins tab. 
2. Set the date to the required period (the longest period is one month). 
3. Review the activity. 

If a user hasn’t signed in over the last month, consider deleting the user account. If you’d like to go further back than one month, you’ll need to consider using Windows PowerShell or Microsoft Graph. You can find out more by reviewing the [How To: Manage inactive user accounts in Azure AD](/azure/active-directory/reports-monitoring/howto-manage-inactive-user-accounts) document.