Microsoft 365 helps provide secure access by requiring users to sign in with a password. It also includes various password management features, including setting password expiration, changing passwords, and resetting passwords. These features are examined in the following sections.

### Setting password expiration

The default password expiration policy in Microsoft 365 includes the following settings:

 -  Users’ passwords expire after 90 days.
 -  Users receive notification of impending password expiration 14 days before it occurs.

The Microsoft 365 admin center enables the Enterprise Administrator to change both of these settings for their organization. To change the password expiration policy, complete the following steps:

1.  Log in to the Microsoft 365 admin center, navigate to the **Settings** menu, and then select the **Security &amp; privacy** tab.
2.  In the **Security &amp; privacy** page, select **Password expiration policy**.
3.  Select **Set user passwords to expire after a number of days** and specify the number of days between 14 and 730 for password expiration.
4.  Specify the number of days between 1 and 30 for the notification warning of password expiration.
5.  Save your settings.

If a user doesn't change their password before the expiration time has elapsed, they can still change it by using the **Password update** page that appears the next time they sign in. Instead, their password can be reset for them.

The **Password update** page also includes an option to set user passwords to never expire. This setting disables password expiration for all users. However, disabling password expiration for all users isn't recommended because of the potential that a password will be hacked or leaked over time.

To disable password expiration for single users using PowerShell, use the **Set-MsolUser** cmdlet with the **-PasswordNeverExpires** parameter.

### Resetting user passwords

If necessary, a password can be reset for one or more users on the **Active users** page. You can choose from the following options: assign a new, randomly generated password or a password of your choice, or select whether users need to change their password at their next login.

### Resetting admin passwords

If an administrator forgets their own password, the two available options are:

 -  **Ask another administrator to reset it for you.** In this case, the other administrator must be either a Global admin, a User Management admin, or a Password admin. However, if the administrator who forgot their password is a Global admin, another Global administrator must reset it for them.
 -  **Reset the password yourself.** On the sign-in page for Microsoft 365, the "**Can’t access your account?"** link enables a user to reset their own password. After following the instructions provided in the link, an email is sent with a link that enables the user to reset their password.

    For a user to reset their own password, they must have previously supplied an alternative email address in their account settings. The email address can't be their Microsoft 365 email address. Additionally, if the organization uses a custom domain name or it uses directory synchronization, the user must have supplied a phone number in their account details that can receive text notifications. An automatically generated code will be sent in a text message to their mobile phone. Once they receive the message, they must enter this code on the mobile phone verification page.

> [!WARNING]
> When resetting the password yourself, the entire admin password reset process must be completed within 10 minutes; otherwise, you must start the process over.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”