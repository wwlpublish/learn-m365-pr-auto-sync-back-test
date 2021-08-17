Self-service password reset (SSPR) enables users to reset their own password without requiring intervention by an administrator. SSPR isn't enabled by default. Instead, the Microsoft 365 Enterprise Administrator must enable SSPR for all users or for specific groups.

To reset a password, users must first authenticate their identity. The following verification methods are available:

 -  Send email to alternate email address
 -  Call office phone
 -  Call mobile phone
 -  Text mobile phone
 -  Answer security questions

If users forget their passwords, they can reset them by selecting the link titled **Can’t access your account?** on the Microsoft 365 Sign-in page. To reset their passwords, users must first enter their alternate personal information. If they haven't entered this information, they'll have to contact the Enterprise Administrator to reset their password for them. Microsoft Support can't reset forgotten passwords.

Administrators that want to use SSPR must use two verification methods, and they're not able to use security questions.

Self-service password reset is only available for Microsoft 365 users with cloud identities that have passwords that aren't linked to the on-premises AD DS. This limitation is because a password from Microsoft 365 can't be synchronized back to on-premises AD DS without using other synchronization services.

The following graphic shows how a user can do a self-service password reset. Once a password is changed, the new password is synchronized over Azure AD Connect, although it doesn't follow the same scheduler. To reflect this scenario, the graphic shows the blue dotted line with the key passing the same way, but it doesn't end in the bubble; instead, it goes all the way to the Windows Server AD.

:::image type="content" source="../media/self-service-password-reset-49907434.jpg" alt-text="graphic depicts how a user can do a self-service password reset, at which point the new password is synchronized over Azure AD Connect, although it does not follow the same scheduler":::


### Password writeback

Paid subscriptions for Microsoft 365 store user information in Azure AD Basic. Azure AD Basic is unable to write back a password change from Azure AD to on-premises AD DS. Azure AD Premium includes the ability to write back passwords. This feature enables organizations to implement self-service password reset for synchronized identities and federated identities. It also enhances AD DS by providing a portal for password reset.

**Additional reading.** For more information about SSPR, see [Resetting your work or school password](/azure/active-directory/active-directory-passwords).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”