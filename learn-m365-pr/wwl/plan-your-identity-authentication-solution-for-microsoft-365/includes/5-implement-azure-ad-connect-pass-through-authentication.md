Pass-through authentication (PTA) provides a simple password validation for Azure AD authentication services. Pass-through uses a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory. With PTA, enables users to sign in to both on-premises and Microsoft 365 resources and applications using their on-premises account and password.

This configuration validates users’ passwords directly against your on-premises Active Directory without sending password hashes to Microsoft 365. Companies with a security requirement to immediately enforce on-premises user account states, password policies, and sign in hours would use this authentication method. With single sign-on, users are automatically signed in to Azure AD when they are on their corporate devices and connected to your corporate network.

When planning for Azure AD Connect Pass-through Authentication, you should keep in mind the following considerations:

 -  Key benefits
 -  Feature highlights
 -  Supported scenarios
 -  Unsupported scenarios

### Key benefits of using Azure AD Pass-Through Authentication

Key benefits of using Azure AD Pass-through Authentication include:

 -  User benefits
    
     -  Users use the same passwords to sign into both on-premises and cloud-based applications.
     -  Users spend less time talking to the IT helpdesk resolving password-related issues.
 -  Administrator benefits
    
     -  No need for complex on-premises deployments or network configuration.
     -  Needs just a lightweight agent to be installed on-premises.
     -  No management overhead. The agent automatically receives improvements and bug fixes.
 -  Security benefits
    
     -  On-premises passwords are never stored in the cloud in any form.
     -  The agent only makes outbound connections from within your network. As such, there's no requirement to install the agent in a perimeter network.
     -  Protects your user accounts by working seamlessly with [Azure AD Conditional Access policies](/azure/active-directory/active-directory-conditional-access-azure-portal), including multifactor authentication (MFA), and by [filtering out brute force password attacks](/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-smart-lockout).
 -  Sign-In benefits
    
     -  Extra agents can be installed on multiple on-premises servers to provide high availability of sign-in requests.

### Feature highlights

Key features of Azure AD Pass-through Authentication include:

 -  Support for user sign-in into all web browser-based applications and into Microsoft Office client applications that use [modern authentication](https://www.microsoft.com/microsoft-365/blog/2015/11/19/updated-office-365-modern-authentication-public-preview/?azure-portal=true).
 -  Sign-in usernames can be either the on-premises default username (userPrincipalName) or another attribute configured in Azure AD Connect (known as Alternate ID).
 -  It works seamlessly with [conditional access](/azure/active-directory/active-directory-conditional-access-azure-portal) features such as multifactor authentication to help secure your users.
 -  It's integrated with cloud-based [self-service password management](/azure/active-directory/authentication/active-directory-passwords-overview), including password writeback to on-premises Active Directory and password protection by banning commonly used passwords.
 -  Multi-forest environments are supported if there are forest trusts between your AD forests and if name suffix routing is correctly configured.
 -  It's a free feature, and you don't need any paid editions of Azure AD to use it.
 -  It can be enabled through [Azure AD Connect](/azure/active-directory/connect/active-directory-aadconnect).
 -  It uses a lightweight on-premises agent that listens for and responds to password validation requests.
 -  Installing multiple agents provides high availability of sign-in requests.
 -  It uses [Azure Active Directory Smart Lockout](/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-smart-lockout) to protect on-premises accounts against brute force password attacks in the cloud.

### Supported scenarios

The following scenarios are fully supported:

 -  User sign-ins to all web browser-based applications.
 -  User sign-ins to Office applications that support [modern authentication](https://www.microsoft.com/microsoft-365/blog/2015/11/19/updated-office-365-modern-authentication-public-preview/?azure-portal=true): Office 2016, and Office 2013 *with* modern authentication.
 -  User sign-ins to Outlook clients using legacy protocols such as Exchange ActiveSync, SMTP, POP, and IMAP.
 -  User sign-ins to Skype for Business that support modern authentication, including online and hybrid topologies. Learn more about supported topologies [here](https://technet.microsoft.com/library/mt803262.aspx?azure-portal=true).
 -  Azure AD domain joins for Windows 10 devices.
 -  App passwords for multifactor authentication.

### Unsupported scenarios

The following scenarios aren't supported:

 -  User sign-ins to legacy Office client applications, excluding Outlook (see **Supported scenarios** above): Office 2010, and Office 2013 *without* modern authentication. Organizations are encouraged to switch to modern authentication, if possible. Modern authentication allows for Pass-through Authentication support. It also helps you secure your user accounts by using [conditional access](/azure/active-directory/active-directory-conditional-access-azure-portal) features, such as Azure Active Directory Multifactor authentication.
 -  Access to calendar sharing and free/busy information in Exchange hybrid environments on Office 2010 only.
 -  User sign-ins to Skype for Business client applications *without* modern authentication.
 -  User sign-ins to PowerShell version 1.0. We recommended that you use PowerShell version 2.0.
 -  Detection of users with [leaked credentials](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-risk-events#leaked-credentials?azure-portal=true).
 -  Azure AD Domain Services needs Password Hash Synchronization to be enabled on the tenant. For tenants that use Pass-through Authentication only, PTA won't work in scenarios that require Azure AD Domain Services.
 -  Pass-through Authentication isn't integrated with [Azure AD Connect Health](/azure/active-directory/connect-health/active-directory-aadconnect-health).
 -  The Apple Device Enrollment Program (Apple DEP) using the iOS Setup Assistant doesn't support modern authentication. This service will fail to enroll Apple DEP devices into Intune for managed domains using Pass-through Authentication. Consider using the [Company Portal app](https://blogs.technet.microsoft.com/intunesupport/2018/02/08/support-for-multi-token-dep-and-authentication-with-company-portal/?azure-portal=true) as an alternative.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”