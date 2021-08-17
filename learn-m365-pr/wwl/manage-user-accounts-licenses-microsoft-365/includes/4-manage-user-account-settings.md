Managing user accounts involves managing several account settings, such as:

 -  Assigning administrator roles
 -  Setting users’ sign-in status
 -  Specifying user location settings
 -  Assigning licenses

The same method doesn't have to be used to maintain this information that was used to originally provision the user accounts. These user settings can be managed through the Microsoft 365 admin center or by using Windows PowerShell cmdlets.

The Microsoft 365 admin center can be used to edit single or multiple users. Complete the following steps to edit a user account:

1.  On the Microsoft 365 admin center, in the left-hand navigation pane, select **Users** and then select **Active Users**.
2.  In the list of active user accounts, select the user that you want to edit to open the user's account pane. The user's account information has been separated into the following tabs:
    
     -  In the **Account** tab, you can modify the user name and aliases, email addresses, group membership, roles, and Office activations. You can also manage multifactor authentication for this user.
     -  In the **Licenses and Apps** tab, you can modify the license assigned to the user. You can also set the user location. Microsoft needs to know the location of each user who uses its Microsoft 365 services so that it only offers permitted services to that user. Finally, you can customize the list of apps available to the user.
     -  In the **Devices** tab, you can view the devices the user has enrolled in Intune.
     -  In the **Mail** tab, you can modify mailbox permissions, email forwarding, automatic replies, and email apps.
     -  In the **OneDrive** tab, you can obtain access to the user’s files, view the storage quota, and force a sign-out from all Microsoft 365 sessions.
