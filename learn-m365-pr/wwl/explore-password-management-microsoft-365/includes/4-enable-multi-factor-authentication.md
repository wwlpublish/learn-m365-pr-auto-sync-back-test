Multifactor authentication (MFA) in Microsoft 365 helps increase security by requesting users to provide a user name and a password while signing in and then use a second authentication method. The second authentication method may be acknowledging a phone call, text message, or an app notification on their mobile phone. If the user name, password, and second authentication method are verified, the user can sign in to Microsoft 365. Users can also be enabled who authenticate from a federated, on-premises directory for multifactor authentication.

An Enterprise Administrator can enable MFA for users in the Microsoft 365 admin center by completing the following steps:

1.  In the Microsoft 365 admin center, in the left-hand navigation pane select **Settings** and then select **Org settings.**
2.  On the **Org settings** page, under the **Services** tab (which is displayed by default) select **Multifactor authentication**.
3.  In the **Multifactor authentication** pane that appears, select **Configure multifactor authentication**.
4.  On the **multifactor authentication** page, select the users to be enabled for multifactor authentication, and then in the right-hand pane select **Enable**.<br>

MFA can also be enabled for a user through Windows PowerShell. Use the **Set-MsolUser** cmdlet and the **-StrongAuthenticationRequriement** parameter, as seen in the following example:

```
$st = New-Object -TypeName Microsoft.Online.Administration.StrongAuthenticationRequirement$st.RelyingParty = "*"$st.State = “Enabled”$sta = @($st)Set-MsolUser -UserPrincipalName StellaC@adatum.onmicrosoft.com -StrongAuthenticationRequirements $sta
```

After the administrator enables users for multifactor authentication, they must configure their second authentication factor at their next sign-in. The following options can be used as the second authentication factor:

 -  **Call to phone.** Users receive a phone call with instructions for the users to press the pound key. After they press the pound key, users are signed in.
 -  **Text message to phone.** Users receive a text message containing a six-digit code that they must enter into the Microsoft 365 portal.
 -  **Notification through mobile app.** Users configure a smartphone app that receives a notification that users need to confirm to sign in to Microsoft 365. Smartphone apps are available for Windows phone, iPhone, and Android devices.
 -  **Verification code from mobile app.** Users configure a smartphone app and enter the six-digit code from the app into the portal.

The multifactor authentication methods can be configured in the service settings of the Microsoft 365 admin center. The following graphic shows the difference between the different authentication factors:

 -  Something the user knows (Password)
 -  Something the user owns (Device)
 -  Something the user is (Biometrics)

:::image type="content" source="../media/difference-between-auth-factors-685e0450.jpg" alt-text="graphic depicts the difference between the different authentication factors":::


**Additional reading.** For more information, see [How it works: Azure AD Multifactor Authentication](/azure/active-directory/authentication/concept-mfa-howitworks).
