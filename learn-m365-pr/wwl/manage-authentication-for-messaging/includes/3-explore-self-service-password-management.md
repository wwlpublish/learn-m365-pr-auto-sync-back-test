In most companies, users occasionally forget their passwords and then send a request to administrators for password reset. In Microsoft 365, you can configure self-service password reset (SSPR) so that users can reset their own passwords.

SSPR is especially useful in medium and enterprise-sized organizations, where the number of password reset requests can be large. While self-service password reset can also be configured in hybrid environments, it isn't available in Exchange Server on-premises environments.

SSPR is configured in the Azure Active Directory admin center.

 -  For cloud-only accounts, it's included with Microsoft 365 enterprise and business subscriptions.
 -  For synchronized accounts, a subscription to Azure AD Premium Plan 1 is required for each user.

:::image type="content" source="../media/password-reset-81f7db9c.png" alt-text="Screenshot of the Azure AD admin center showing the users and groups page":::


On the **Properties** page of the Azure Active Directory admin center, select **All** to enable it for everyone in your business, and then select **Save**.

:::image type="content" source="../media/enable-password-reset-ab6be175.png" alt-text="Screenshot of the Azure AD admin center showing the users and groups Properties page":::


When users sign in to Microsoft 365, they'll be prompted to enter other contact information to help them reset their password in the future. The following steps describe the workflow logic used of the password reset page:

1.  The user selects the "**Can't access your account"** link or goes directly to the **Password reset** page.
2.  The user enters a user ID and passes a captcha.
3.  Azure AD runs the following checks to verify the user can use this feature:

 -  Verifies the user has this feature enabled and has an Azure AD license assigned.
 -  Verifies the user has the right authentication methods defined on their account that follow administrative policy.
 -  Verifies whether the user’s password is managed on-premises (federated, pass-through authentication, or password hash synchronized), or if writeback is deployed and the user’s password is managed on-premises.

4.  If it's determined that the user can successfully reset their password, they're guided through the reset process.
5.  If the checks aren't validated, the user is advised to contact their administrator to reset their password.

### Authentication methods

If SSPR is enabled, you must select at least one of the following options for the authentication methods, sometimes referred to as "gates":

 -  Mobile app notification
 -  Mobile app code
 -  Email
 -  Mobile phone
 -  Office phone
 -  Security questions

> [!NOTE]
> It's highly recommended that you choose two or more authentication methods. This design provides your users with more flexibility in case they're unable to access one when they need it.

Users can only reset their password if they have data present in the authentication methods the administrator has enabled.

### Number of authentication methods required

This option determines the minimum number of the available authentication methods a user must go through to reset or unlock their password. It can be set to either one or two.

### Registration

Enabling this option requires a user to complete the password reset registration if they sign into any applications using Azure AD. This feature includes the following applications:

 -  Microsoft 365
 -  Azure portal
 -  Access Panel
 -  Federated applications
 -  Custom applications using Azure AD

### Set the number of days before users are asked to reconfirm their authentication information

This option determines the period of time between setting and reconfirming authentication information and is available only if you enable the **Require users to register when signing in** option.

Valid values are 0 to 730 days, with "0" meaning users are never asked to reconfirm their authentication information.

### Notifications

The following notifications can be configured during password reset:

 -  **Notify users on password resets**. If this option is set to **Yes**, then users resetting their password will receive an email notifying them that their password has been changed. The email is sent through the SSPR portal to their primary and alternate email addresses that are on file in Azure AD. No one else is notified of the reset event.
 -  **Notify all admins when other admins reset their passwords**. If this option is set to **Yes**, then all administrators receive an email that's sent to their primary email address on file in Azure AD. The email notifies them that another administrator has changed their password by using SSPR.

### Write back passwords to your on-premises directory

This control determines whether password writeback is enabled for this directory. If writeback is on, it indicates the status of the on-premises writeback service. This setting is useful if you want to temporarily disable password writeback without having to reconfigure Azure AD Connect.

### Allow users to unlock accounts without resetting their password

This control determines whether users who visit the password reset portal should be given the option of unlocking their on-premises Active Directory accounts without having to reset their password. By default, Azure AD unlocks accounts when it completes a password reset. You use this setting to separate those two operations.

 -  If set to **Yes**, then users are given the option to reset their password and unlock the account, or to unlock their account without having to reset the password.
 -  If set to **No**, then users can only complete a combined password reset and account unlock operation.
