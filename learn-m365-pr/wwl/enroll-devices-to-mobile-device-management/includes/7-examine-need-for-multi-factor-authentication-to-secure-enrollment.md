By default, a user must authenticate with a username and password when they want to enroll a device to MDM. In an environment where stronger authentication is required, organizations can include multifactor authentication (MFA). MFA is two-step verification process that requires that a user pass two or more of the following authentication methods:

 -  Something they know (typically a password)
 -  Something they have (a trusted device that's not easily duplicated, like a phone)
 -  Something they are (biometrics)

:::image type="content" source="../media/different-forms-of-authentication-6c7f95b4.png" alt-text="graphic showing different forms of authentication":::


For Microsoft 365, Azure Multifactor Authentication (MFA) helps safeguard access to data and applications. Because MFA is turned off by default, organizations must enable it as an optional step. MFA can be enabled in the Azure portal or in the Microsoft 365 admin portal. It's recommended that organizations turn on MFA for all privileged users. In fact, it's not uncommon for MFA to be turned on for all users.

MFA provides organizations with extra security. It also requires that the user has their trusted device when signing in. Many other settings can be configured for MFA. For example:

 -  MFA can be required only when a user wants to authenticate from an untrusted network.
 -  MFA can be configured to be valid for just a certain period of time (for example, one hour). During that time, a second form of authentication isn't required, even if a user has to authenticate multiple times.

MFA helps secure the sign-in to Microsoft 365 or Intune for mobile device enrollment by requiring a second form of authentication. Users are required to respond to either a phone call, text message, or app notification on their trusted mobile device after correctly entering their account password. They can only enroll their device after this second form of authentication is completed. After a user's devices are enrolled in Intune or Basic Mobility and Security, the user can access resources such as Exchange Online.

**Additional reading.** For more information, see the following resources:

 -  [Setting up MFA in the Azure portal](/azure/active-directory/authentication/howto-mfa-mfasettings?azure-portal=true)
 -  [Setting up MFA for Office 365 users](https://support.office.com/article/set-up-multi-factor-authentication-for-office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6?azure-portal=true)
