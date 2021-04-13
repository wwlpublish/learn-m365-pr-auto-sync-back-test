Microsoft 365 helps provide secure access by requiring users to sign in with a password. It also includes various password management features, including setting password expiration, changing passwords, and resetting passwords. These features are examined in the following sections.

### Setting password expiration

The default password expiration policy in Microsoft 365 includes the following settings:

 *  Users’ passwords expire after 90 days.
 *  Users receive notification of impending password expiration 14 days before it occurs.

The Microsoft 365 admin center enables the Enterprise Administrator to change both of these settings for their organization. To change the password expiration policy, complete the following steps:

1.  Log in to the Microsoft 365 admin center, navigate to the **Settings** menu, and then select the **Security &amp; privacy** tab.
2.  In the **Security &amp; privacy** page, select **Password expiration policy**.
3.  Select **Set user passwords to expire after a number of days** and specify the number of days between 14 and 730 for password expiration.
4.  Specify the number of days between 1 and 30 for the notification warning of password expiration.
5.  Save your settings.

If a user doesn't change their password before the expiration time has elapsed, they can still change it by using the Password update page that appears the next time they sign in. Instead, you can reset their password for them.

You also have the option on the Password update page to set user passwords to never expire. This setting disables password expiration for all users. However, disabling password expiration for all your users isn't recommended because of the potential that a password will be hacked or leaked over time.

To disable password expiration for single users using PowerShell, you need to use the **Set-MsolUser** cmdlet with the **-PasswordNeverExpires** parameter.

### Resetting user passwords

If necessary, you can reset a password for one or more users on the Active users page. You have the following options to choose from: assign a new, randomly generated password or a password of your choice, or select whether users need to change their password at their next login.

### Resetting admin passwords

If you forget your own administrator password, the two available options are:

 *  **Ask another administrator to reset it for you.** In this case, the other administrator must be a global admin, a user management admin, or a password admin. However, if your account is a global admin account, you must get another administrator with a global admin account to reset it for you.
 *  **Reset the password yourself.** On the sign-in page for Microsoft 365, the **Can’t access your account?** link enables you to reset your password. When you follow the instructions provided by the link, you're sent an email with a link that enables you to reset your password.

To reset the password yourself, you must have previously supplied an alternative email address in your account settings. The email address can't be your Microsoft 365 email address. Additionally, if you use a custom domain name or you're using directory synchronization, you must have supplied a phone number in your account details that can receive text notifications. An automatically generated code will be sent in a text message to your mobile phone. Once you receive the message, you must enter this code on the mobile phone verification page.

> [!WARNING]
> When resetting the password yourself, you must complete the entire admin password reset process within 10 minutes; otherwise, you must start the process over.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”