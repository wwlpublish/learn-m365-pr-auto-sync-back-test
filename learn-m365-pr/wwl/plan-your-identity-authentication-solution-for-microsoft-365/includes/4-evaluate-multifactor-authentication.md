Multi-factor authentication (MFA) is a method of authentication that requires the use of more than one verification method. By doing so, it adds a second layer of security to user sign-ins and transactions. MFA works by requiring any two or more of the following verification methods:

 -  A randomly generated pass code
 -  A phone call
 -  A phone Short Message Service (SMS)
 -  A smart card (virtual or physical)
 -  A biometric device

### Multi-factor authentication in Microsoft 365

Microsoft 365 uses multi-factor authentication to provide the extra security. MFA in Microsoft 365 is managed from the Microsoft 365 admin center. Microsoft 365 offers the following subset of Azure Active Directory Multi-Factor Authentication capabilities as a part of the subscription:

 -  The ability to enable and enforce multi-factor authentication for end users.
 -  The use of a mobile app (online and one-time password \[OTP\]) as a second authentication factor.
 -  The use of a phone call as a second authentication factor.
 -  The use of a Short Message Service (SMS) message as a second authentication factor.
 -  Application passwords for non-browser clients (for example, the Microsoft Lync 2013 communications software).
 -  Default Microsoft greetings that are provided during authentication phone calls.

For the full list of added features, see [Features and licenses for Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/concept-mfa-licensing?azure-portal=true). You can always get the full functionality by purchasing the Azure Active Directory Multi-Factor Authentication service.

Organizations get a different subset of capabilities depending on whether they have a cloud-only deployment for Microsoft 365 or a hybrid setup with single sign-on and Active Directory Federation Services (AD FS).

:::row:::
  :::column:::
    **Where do you manage your Microsoft 365 tenant?**
  :::column-end:::
  :::column:::
    **MFA second factor options**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Cloud only
  :::column-end:::
  :::column:::
    Azure Active Directory MFA (text, phone call, or App)
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Hybrid setup, managed on-premises
  :::column-end:::
  :::column:::
    If you manage user identity on-premises, you have the following choices:

 -  Physical or virtual smart card (AD FS)
 -  [Azure AD Multi-Factor Authentication](/windows-server/identity/ad-fs/operations/configure-ad-fs-and-azure-mfa?azure-portal=true) (module for AD FS)
 -  [Azure AD MFA](/azure/active-directory/authentication/concept-mfa-howitworks?azure-portal=true)


  :::column-end:::
:::row-end:::


You can also use any other MFA solutions that are offered with your on-premises directory. For example, the [Azure AD federation compatibility list](/azure/active-directory/hybrid/how-to-connect-fed-compatibility?azure-portal=true) might offer MFA solutions that you can manage according to the identity provider's specifications.

The Office 2013 device apps support multi-factor authentication by using the [Active Directory Authentication Library](https://microsoft.sharepoint.com/sites/knowledgecenter/SitePages/AD-Authentication-Library.aspx?azure-portal=true). Azure AD hosts a webpage where users can sign in. The identity provider can be Azure AD or a federated identity provider like AD FS. The authentication for federated users follows these steps:

1.  Azure AD redirects the user to the sign-in web page that's hosted by the identity provider of record for the Microsoft 365 tenant. The identity provider is determined by the domain specified in the user’s sign-in name.
2.  The user signs in on the sign-in web page on their device.
3.  The identity provider returns a token to Azure AD when the user is successfully signed in.
4.  Azure AD returns a JSON Web Token (JWT) to the Office device app, and the device app is authenticated by using a JWT with Microsoft 365.

The following figure shows how the updated Office 2019 device apps (on Windows) enable users to sign in with MFA.

:::image type="content" source="../media/mfa-login-with-office2019-apps-e1814b0a.png" alt-text="graphic shows how the updated Office 2013 device apps (on Windows) enable users to sign in with MFA":::


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”