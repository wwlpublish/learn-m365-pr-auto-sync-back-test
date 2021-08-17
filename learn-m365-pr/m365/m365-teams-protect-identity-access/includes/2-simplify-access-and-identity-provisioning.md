Microsoft Teams uses Azure Active Directory (Azure AD) features to support advanced methods for positively identifying users. Let's examine some of the ways you can fortify authentication.

## What is modern authentication

Modern authentication is a method of identity management that offers more secure user authentication and authorization between client and server. Modern authentication brings Active Directory Authentication Library (ADAL)-based sign-in to Office client applications like Microsoft Teams. This method enables sign-in features such as multifactor authentication, SAML-based third-party identity providers, and smart card and certificate-based authentication. Modern authentication is the default sign-in protocol for Teams.

## How modern authentication works in Teams

Modern authentication is a process where users who have already entered their credentials (such as email and password) elsewhere on the computer won't need to do so again in Teams. The experience will vary depending on whether users are working in Windows or on a Mac and whether your organization has enabled single-factor authentication or multifactor authentication. Multifactor authentication usually involves verifying credentials via a phone, providing a unique code, entering a PIN, or presenting a thumbprint. The following is a rundown of each modern authentication scenario.

### Windows users

* If users have already signed into Windows or other Office apps with their work or school account, they're taken directly to the app when they start Teams. There's no need to enter their credentials.
* Microsoft recommends using Windows 10 version 1903 or later for the best single sign-on (SSO) experience.
* If users aren't signed in to their Microsoft work or school account anywhere else, and they then start Teams, they're asked to provide either single-factor or multifactor authentication, depending on what your organization decides.
* If users are signed into a domain-joined computer when they start Teams, they might be asked to go through one more authentication step. It depends on whether your organization opted to require multifactor authentication, or if the computer already needs multifactor authentication to sign in. If the user's computer has already asked for multifactor authentication to sign in, the Teams app starts automatically when they open it.
* On domain-joined PCs, when SSO isn't possible, Teams may prefill its login screen with the user principal name (UPN). There are times when you might not want this, especially if your organization uses different UPNs on-premises and in Azure Active Directory. If that's the case, you can use the following Windows registry key to turn off prepopulation of the UPN:

  **Computer\HKEY_CURRENT_USER\Software\Microsoft\Office\Teams
  SkipUpnPrefill(REG_DWORD)
  0x00000001 (1)**

> [!NOTE]
> Skipping or ignoring username prefill for usernames that end in ".local" or ".corp" is on by default. You don't need to set a registry key to turn these off.

### Mac users

On macOS, Teams will prompt users to enter their username credentials and might request multifactor authentication, depending on your organization's settings. After users enter their credentials, they won't be required to provide them again. From that point, Teams automatically starts whenever they're working on the same computer.

### Teams for iOS and Android users

On sign-in, mobile users will see a list of all the Microsoft 365 accounts that are either currently signed in or were previously signed in on their device. Users can tap on any of the accounts to sign in. There are two scenarios for mobile sign-in:

* If the selected account is currently signed into other Office 365 or Microsoft 365 apps, then the user will be taken straight to Teams. There's no need to enter credentials.
* If the user isn't signed in to their Microsoft 365 account anywhere else, they'll be asked to provide single-factor or multifactor authentication, depending on what your organization has configured for mobile sign-in policies.

> [!NOTE]
> For users to have the sign-in experience as described in this section, their devices must be running Teams for iOS version 2.0.13 (build 2020061704) or later, or Teams for Android version 1416/1.0.0.2020061702 or later.

## Adding multiple accounts to Teams

Teams for iOS and Android supports adding multiple accounts from a single device, as shown in the following images:

:::image type="content" source="../media/2-add-multiple-accounts.png" alt-text="Adding multiple accounts":::

## Use enterprise mobility management to control which accounts can sign in to Teams

IT administrators need the ability to push configurations to Microsoft 365 accounts for iOS and Android users. This capability works with any mobile device management (MDM) provider who uses the Managed App Configuration channel for iOS or the Android Enterprise channel for Android. For more information, see **Managed App Configuration channel for iOS and Android Enterprise channel for Android** in the **Learn more** section below.
For users enrolled in Microsoft Intune, you can deploy the account configuration settings using Intune in the Azure portal.
The account setup is configured in the MDM provider, and the user enrolls their device. Then, on the login page, Teams for iOS and Android will only show the allowed accounts that the user can tap to sign in.
Set the following configuration parameters in the Azure Intune portal for managed devices.

| Platform | Key | Value |
| --- | --- | --- |
| iOS | **IntuneMAMAllowedAccountsOnly** | **Enabled**: The only account allowed is the managed user account defined by the IntuneMAMUPN key. **Disabled**: Any account is allowed. |
| iOS | **IntuneMAMUPN** | UPN of the account allowed to sign in to Teams. For Intune enrolled devices, the {{userprincipalname}} token may be used to represent the enrolled user account. |
| Android  | **com.microsoft.intune.mam. AllowedAccountUPNs** | Only account(s) allowed are the managed user account(s) defined by this key. One or more semicolon-delimited UPNs. For Intune enrolled devices, the {{userprincipalname}} token may be used to represent the enrolled user account. |
| | |

When the account setup configuration has been set, Teams will restrict the ability to sign in so that only allowed accounts on enrolled devices will be granted access.

## Switching accounts after completing modern authentication

If users are working on a domain-joined computer (for example, if their tenant has enabled Kerberos), they can't switch user accounts after completing modern authentication. Users who aren't working on a domain-joined computer can switch accounts.

## Signing out of Teams after completing modern authentication

To sign out of Teams, users select their profile picture at the top of the app, and then select **Sign out**. Users can also select and hold the app icon in their taskbar, and then select **Sign out**. After signing out of Teams, users must enter their credentials again to launch the app.

## Signing out of Teams for iOS and Android

Mobile users sign out of Teams by going to the **applications menu** > **Settings** > **Sign out**. After signing out, users will need to reenter their credentials the next time they launch the app.

> [!NOTE]
> Teams for Android uses single sign-on (SSO) to simplify the sign-in experience. Users should log out of all Microsoft apps and Teams to log out of the Android platform.

## URLs and IP address ranges

Teams requires an internet connection. To understand endpoints that should be reachable for customers using Teams in Office 365 plans, government and other clouds, read **Office 365 URLs and IP address ranges**, in the **Learn more** section below.

## Troubleshooting modern authentication

Modern authentication is available for every organization that uses Teams. If users can't complete the process, there might be something wrong with your domain or your organization's Microsoft work or school account. For troubleshooting information, see **Why am I having trouble signing in to Microsoft Teams?** in the **Learn more** section below.

## Learn more

- [Managed App Configuration channel for iOS](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html)
- [Add app configuration policies for managed iOS/iPadOS devices](/mem/intune/apps/app-configuration-policies-use-ios)
- [Add app configuration policies for managed Android devices](/mem/intune/apps/app-configuration-policies-use-android)
- [Office 365 URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges)
- [Why am I having trouble signing in to Microsoft Teams?](https://support.office.com/article/why-am-i-having-trouble-signing-in-to-microsoft-teams-a02f683b-61a3-4008-9447-ee60c5593b0f)
