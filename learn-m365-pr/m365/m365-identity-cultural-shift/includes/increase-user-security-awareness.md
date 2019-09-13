You can help users follow organization policies while elevating awareness of identity security best practices. Here are three methods for accomplishing this goal:

- Enable user self-service password reset.
- Prevent users from choosing weak passwords.
- Transition to passwordless authentication.

## Enable user self-service password reset

Azure AD self-service password reset (SSPR) enables users to unlock their passwords or accounts without helpdesk intervention. SSPR tracks when users reset their passwords and alerts you of any misuse.

SSPR has these capabilities:

- **Self-service password reset/change** enables users to change or reset their expired or non-expired passwords without contacting an administrator or the helpdesk for support.
- **Password Writeback** enables you to manage on-premises passwords and resolve account lockout though the cloud.
- **Password management activity reports** give administrators insights into password reset and registration activity.

## Prevent users from choosing weak passwords

Use Azure AD password protection to guide users towards choosing more secure passwords. You can customize the default banned password list to ensure that users exclude the organization’s name, location, products, branding, or other terms from their passwords.

For example, when Christina creates a new password, Azure AD password protection automatically prevents her from picking commonly used weak or compromised passwords, such as **Contoso123**. You can add words to the banned password list. This helps Christina comply with the organization’s best practices when she resets her password.

![Screenshot of banned password list in Azure AD password protection.](../media/authentication-methods-password-protection.png)
*Screenshot of banned password list in Azure AD password protection*

## Transition to passwordless authentication

Research shows that almost every password rule you impose on users results in a degradation of password quality. That's because in general, users value productivity over security.

With passwordless authentication, you can shift users toward a simple and secure sign-on experience. For example, by using the Microsoft Authenticator app, users won’t need to enter a password to sign in to any Azure AD-synced account on their mobile devices.

![Accounts displayed in the Microsoft Authenticator app](../media/auth-app-accounts.png)

## Learn more

- [How it works: Azure AD self-service password reset](https://docs.microsoft.com/azure/active-directory/authentication/concept-sspr-howitworks)
- [Eliminate bad passwords in your organization](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad)
- [What is passwordless?](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless#microsoft-authenticator-app)


