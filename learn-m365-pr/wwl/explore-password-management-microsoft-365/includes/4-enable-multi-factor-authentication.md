Multi-factor Authentication (MFA) in Microsoft 365 helps increase security by requesting users to provide a user name and a password while signing in and then use a second authentication method. The second authentication method might be acknowledging a phone call, text message, or an app notification on their smartphone. If the user names, passwords, and second authentication method are verified, the users can sign in to Microsoft 365. You can also enable users who authenticate from a federated, on-premises directory for multi-factor authentication.

An Enterprise Administrator can enable MFA for users in the Microsoft 365 admin center by completing the following steps:

1.  In the Microsoft 365 admin center, in the left-hand navigation pane select **Settings** and then select **Org settings.**
2.  On the **Org settings** page, under the **Services** tab (which is displayed by default) select **Multi-factor authentication**.
3.  In the **Multi-factor authentication** pane that appears, select **Configure multi-factor authentication**.
4.  On the **multi-factor authentication** page, select the users to be enabled for multi-factor authentication, and then in the right-hand pane select **Enable**.<br>

MFA can also be enabled for a user through Windows PowerShell. Use the **Set-MsolUser** cmdlet and the **-StrongAuthenticationRequriement** parameter, as seen in the following example:

```
$st = New-Object -TypeName Microsoft.Online.Administration.StrongAuthenticationRequirement$st.RelyingParty = "*"$st.State = “Enabled”$sta = @($st)Set-MsolUser -UserPrincipalName StellaC@adatum.onmicrosoft.com -StrongAuthenticationRequirements $sta
```

After the administrator enables users for multi-factor authentication, they must configure their second authentication factor at their next sign-in. You can use the following options as the second authentication factor:

 *  **Call to phone.** Users receive a phone call with instructions for the users to press the pound key. After they press the pound key, users are signed in.
 *  **Text message to phone.** Users receive a text message containing a six-digit code that they must enter into the Office 365 portal.
 *  **Notification through mobile app.** Users configure a smartphone app that receives a notification that users need to confirm to sign in to Microsoft 365. Smartphone apps are available for Windows phone, iPhone, and Android devices.
 *  **Verification code from mobile app.** Users configure a smartphone app and enter the six-digit code from the app into the portal.

The multi-factor authentication methods can be configured in the service settings of the Microsoft 365 admin center. The following graphic shows the difference between the different authentication factors:

 *  Something the user knows (Password)
 *  Something the user owns (Device)
 *  Something the user is (Biometrics)

:::image type="content" source="../media/difference-between-auth-factors-685e0450.jpg" alt-text="graphic depicts the difference between the different authentication factors":::


**Additional reading.** For more information, see [How it works: Azure AD Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks?azure-portal=true).
