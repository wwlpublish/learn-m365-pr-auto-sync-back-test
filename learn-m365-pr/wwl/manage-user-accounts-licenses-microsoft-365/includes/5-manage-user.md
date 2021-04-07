One of the most basic tasks for Microsoft 365 Enterprise Administrators is user management, and to manage users you need to understand how to manage their licenses. Your organization’s users need licenses to use Microsoft 365 services such as Microsoft Outlook and Microsoft SharePoint Online. When you assign a license to a user, the service is automatically set up for that user. For example, when you assign a license for SharePoint Online, the user is assigned edit permissions on the default team site.

Only members of the Microsoft 365 Global admin and User Management admin roles can assign or remove licenses. You can assign or remove a license for single or multiple users.

> [!IMPORTANT]
> When you remove a license from one of your users, any service data that is associated with that user is deleted. You then have a 30-day grace period in which you can recover that data, but after the grace period, the data is not recoverable.

### Assigning a license

To assign a license, you can use the Microsoft 365 admin center or Windows PowerShell. The prior unit provided instruction on how you can edit the license(s) for an individual user. However, you can also maintain products licenses for multiple users at one time. To assign or remove licenses for multiple users in the Microsoft 365 admin center, you should perform the following steps:

1.  In the Microsoft 365 admin center, in the left-hand navigation pane, select **Users** and then select **Active users**.
2.  Select the users that you want to assign or remove licenses, and then in the menu bar, select the **ellipsis (More actions)** icon. In the drop-down menu that appears, select **Manage product licenses**.
3.  On the **Manage product licenses** page, you must first specify whether to replace or add to existing licenses, and then you can change the user location and select the services that you want to modify.

If you prefer to use Windows PowerShell, the **Set-MsolUserLicense** cmdlet enables you to add user licenses, remove user licenses, and update licensing options. To add a license to a user, at the command prompt, type the following command, and then press Enter:

```
Set-MsolUserLicense -UserPrincipalName username@domainname –AddLicenses “license”
```

For example, to add an Enterprise Premium license for Patti Fernandez at Adatum Corp., you would run the following command:

```
Set-MsolUserLicense –UserPrincipalName PattiF@Adatum.onmicrosoft.com –AddLicenses "Adatum:ENTERPRISEPREMIUM"
```

### View license information

You can use the Microsoft 365 admin center to view important information about your users’ license usage, such as how many licenses you have used, how many are remaining, and which users are currently unlicensed.

To view the number of licenses remaining:

1.  In the Microsoft 365 admin center, on the left-hand navigation pane, select **Billing** and then select **Licenses**.
2.  In the **Subscriptions** tab, note how many licenses are available for each subscription and how many licenses have been assigned.

To view any unlicensed users:

1.  In the Microsoft 365 admin center, on the left-hand navigation pane, select **Users** and then select **Active users**.
2.  In the menu bar, select **Filter**.
3.  In the drop-down menu that appears, note all the various options that you can select to view the users with these respective properties. To view unlicensed users, select **Unlicensed users**.

Using Windows PowerShell, you can use the **Get-MsolAccountSku** cmdlet to view the current licensing information for your Microsoft 365 tenant, which includes the number of licenses that are currently available and how many are in use. You can use the **Get-MsolUser** cmdlet with the **-UnlicensedUsersOnly** switch to view a list of users who currently do not have a license.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”