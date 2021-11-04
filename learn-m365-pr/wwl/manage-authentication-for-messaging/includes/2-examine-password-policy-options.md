Setting password policy for users in your organization is one of the key responsibilities for administrators in a Microsoft 365 organization. The primary goal of a more secure password system is password diversity. You want your password policy to contain many different and hard-to-guess passwords. Here are a few recommendations for keeping your organization as secure as possible:

 -  Maintain an eight character minimum length requirement for passwords (longer passwords aren't necessarily better).
 -  Don't require character composition requirements within passwords, such as \* &amp; ^ % $.
 -  Don't require mandatory periodic password resets for user accounts.
 -  Ban common passwords to keep the most vulnerable passwords out of your system.
 -  Educate your users to not reuse their organization passwords for non-work-related purposes.
 -  Enforce registration for multifactor authentication.
 -  Enable risk-based multifactor authentication challenges.

Password policies control password properties for users in your organization, such as password complexity and expiration date. Some organizations also mandate password expiry and changes to follow auditing requirements. In Microsoft 365, password policy configuration enables you to set user passwords to expire after some days or set passwords to never expire. To configure password policy in Microsoft 365, you must be assigned a Microsoft 365 Global Administrator role.

:::image type="content" source="../media/password-policy-588061dc.png" alt-text="Screenshot of the EAC and the Security and Privacy page":::


Complete the following steps to configure password expiration in Microsoft 365:

1.  Go to the Microsoft 365 admin center.
2.  In the **Microsoft 365 admin center**, select **Show all** in the left-hand navigation pane, select **Settings,** and then **Org settings**.
3.  On the **Org settings** page, select the **Security & privacy** tab and then select **Password expiration policy**.
4.  In the **Password expiration policy** pane that appears, you must update the **Set user passwords to expire after a number of days** check box depending on whether you want to force users to change their passwords.
    
     -  If you don't want user passwords to expire, then leave this check box blank and close the window.
     -  If you want user passwords to expire, then complete the following steps:
        
        1.  Select the **Set user passwords to expire after a number of days** check box.
        2.  In the **Days before passwords expire** box, enter the number of days before passwords expire. Enter a number from **14** to **730** (days).
        3.  In the **Days before a user is notified about expiration** box, enter the number of days before users' passwords are set to expire when users are notified that their password will expire. Enter a number from **1** to **30** (days).
        4.  Select **Save**.

When passwords are set to expire and the current date falls within the notification period for a user, a notification will appear in the lower right corner of the user’s screen. If a user doesn’t change their password and it eventually expires, the user will receive a similar notification.

In Exchange Online deployments, you can use Azure Active Directory to configure other password policy settings, such as password length and complexity. These policies will apply to:

 -  Cloud-only accounts.
 -  Administrator accounts responsible for replying to emergencies in enterprise environments.
 -  Smaller organizations that don’t use Azure AD Connect to synchronize Active Directory.

### Configure complex passwords for Active Directory

Password policies are configured in Active Directory in on-premises environments, including those deployments that synchronize Active Directory to Azure AD. In these cases, the password policy applied to on-premises accounts will also apply to Azure AD accounts. This design includes scenarios involving Password Hash Synchronization, Pass Through Authentication, and Active Directory Federation Services (AD FS).

To configure password policies in AD, edit the **Default Domain Policy** in the Group Policy Management Console (GPMC). In the left-hand navigation pane, navigate to **Computer Configuration** &gt; **Policies** &gt; **Windows Settings** &gt; **Security Settings** &gt; **Account Policies** &gt; **Password Policy**.

:::image type="content" source="../media/password-policy-588061dc.png" alt-text="Screenshot of the Group Policy Management Console showing account policies and the password policy group":::


**Additional reading.** For more information, see [Password and account lockout policies on managed domains](/azure/active-directory-domain-services/password-policy?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select **Check your answers**.