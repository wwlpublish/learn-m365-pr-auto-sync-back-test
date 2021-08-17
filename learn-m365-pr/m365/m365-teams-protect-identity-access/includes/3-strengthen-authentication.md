To ensure that common attacks can't compromise your user accounts, you need users to provide more credentials, such as user certificates or time-limited codes. Let's examine how to configure these methods.

## Multifactor authentication

Microsoft 365 plans support multifactor authentication to increase the security of user logins to services. Users have to acknowledge a phone call, text message, or an app notification on their smartphone after correctly entering their password. Only after this second authentication factor has been satisfied, can a user sign in.
Multi-factor authentication is supported with any Microsoft 365 plan that includes Microsoft Teams.
The next time a user signs in after enrolling for multifactor authentication, they'll see a message asking them to set up a second authentication factor. Supported authentication methods are:

| Tenant type | Available MFA second factor options | Notes |
| --- | --- | --- |
| **Cloud only** | MFA for Microsoft 365 Phone Call Text Message Mobile App Notification Mobile App Verification Code | |
| **Hybrid setup (Synchronized or Federated Identity model)** | MFA for Microsoft 365 Azure MFA module (ADFS integrated) physical or virtual smart card (ADFS integrated) | Additional MFA solutions are available in the link **Azure AD Identity Provider Compatibility Docs** in the Summary |
| | |

## Certificate-based authentication

With a client certificate on a Windows, Android, or iOS device, certificate-based authentication enables you to be authenticated by Azure Active Directory when connecting your Exchange online account to:

* Mobile applications such as Microsoft Outlook and Microsoft Word
* Exchange ActiveSync (EAS) clients

Configuring this feature means you don't need to enter a username and password combination into certain mail and Microsoft Office applications on your mobile device.

This topic:

* Provides the steps to configure and use certificate-based authentication for users of tenants in Microsoft 365 Enterprise, Business, Education, and US Government plans. This feature is available in preview in Microsoft 365 China, US Government Defense, and US Government Federal plans.
* Assumes that you already have a public key infrastructure (PKI) and AD FS configured.

### Requirements

To configure certificate-based authentication, the following statements must be true:

* Certificate-based authentication (CBA) is only supported for federated environments for browser applications, native clients using modern authentication (ADAL), or MSAL libraries. The one exception is Exchange Active Sync (EAS) for Exchange Online (EXO), which can be used for federated and managed accounts.
* The root certificate authority and any intermediate certificate authorities must be configured in Azure Active Directory.
* Each certificate authority must have a certificate revocation list (CRL) that can be referenced via an internet-facing URL.
* You must have at least one certificate authority configured in Azure Active Directory.
* For Exchange ActiveSync clients, the client certificate must have the user's routable email address in Exchange online, in either the Principal Name or the RFC822 Name value of the Subject Alternative Name field. Azure Active Directory maps the RFC822 value to the Proxy Address attribute in the directory.
* Your client device must have access to at least one certificate authority that issues client certificates.
* A client certificate for client authentication must have been issued.

> [!IMPORTANT]
> The maximum size of a CRL for Azure Active Directory to successfully download and cache is 20 MB, and the time required to download it must not exceed 10 seconds. If Azure Active Directory can't download a CRL, certificate-based authentications using certificates issued by the corresponding CA will fail. To ensure CRL files are within size constraints, best practice is to keep certificate lifetimes to within reasonable limits, and to clean up expired certificates.

### Step 1: Select your device platform

As a first step, for the device platform you're working with, you need to review the following items:

* The Office mobile applications support
* The specific implementation requirements

For information about Android and iOS devices, check out the following topics in the **Learn more** section below:

* **Azure Active Directory certificate-based authentication on Android**
* **Azure Active Directory certificate-based authentication on iOS**

### Step 2: Configure the certificate authorities

To configure your certificate authorities in Azure Active Directory, upload the following items for each one:

* The public portion of the certificate in a .cer format
* The internet-facing URLs where the CRLs reside

This is how the schema for a certificate authority looks:

``` csharp
class TrustedCAsForPasswordlessAuth
{
    CertificateAuthorityInformation[] certificateAuthorities;
}

class CertificateAuthorityInformation

{
    CertAuthorityType authorityType;
    X509Certificate trustedCertificate;
    string crlDistributionPoint;
    string deltaCrlDistributionPoint;
    string trustedIssuer;
    string trustedIssuerSKI;
}

enum CertAuthorityType
{
    RootAuthority = 0,
    IntermediateAuthority = 1
}
```

For the configuration, you can use Azure Active Directory PowerShell Version 2:

1. Start Windows PowerShell with administrator privileges.
1. Install the Azure AD module version 2.0.0.33 or higher.

``` PowerShell
   Install-Module -Name AzureAD –RequiredVersion 2.0.0.33
   ```

You need to establish a connection with your tenant. As soon as that connection exists, you can review, add, delete, and modify the trusted certificate authorities that are defined in your directory.

To establish a connection with your tenant, use the **Connect-AzureAD** cmdlet:

``` PowerShell
Connect-AzureAD
```

To retrieve the trusted certificate authorities defined in your directory, use the **Get-AzureADTrustedCertificateAuthority** cmdlet:

``` PowerShell
Get-AzureADTrustedCertificateAuthority
```

To create a trusted certificate authority, use the **New-AzureADTrustedCertificateAuthority** cmdlet and set the **crlDistributionPoint** attribute to a correct value:

``` PowerShell
$cert=Get-Content -Encoding byte "[LOCATION OF THE CER FILE]"
$new_ca=New-Object -TypeName Microsoft.Open.AzureAD.Model.CertificateAuthorityInformation
$new_ca.AuthorityType=0
$new_ca.TrustedCertificate=$cert
$new_ca.crlDistributionPoint="<CRL Distribution URL>"
New-AzureADTrustedCertificateAuthority -CertificateAuthorityInformation $new_ca
```

To remove a trusted certificate authority, use the **Remove-AzureADTrustedCertificateAuthority** cmdlet:

``` PowerShell
$c=Get-AzureADTrustedCertificateAuthority
Remove-AzureADTrustedCertificateAuthority -CertificateAuthorityInformation $c[2]
```

To modify a trusted certificate authority, use the **Set-AzureADTrustedCertificateAuthority** cmdlet:

``` PowerShell
$c = Get-AzureADTrustedCertificateAuthority
$c[0].AuthorityType = 1
Set-AzureADTrustedCertificateAuthority -CertificateAuthorityInformation $c[0]
```

### Step 3: Configure revocation

To revoke a client certificate, Azure Active Directory fetches the CRL from the URLs uploaded as part of the certificate authority information and caches it. The last publish timestamp (**Effective Date** property) in the CRL is used to ensure it's still valid. The CRL is periodically referenced to revoke access to certificates that are part of the list.
If a more instant revocation is required (for example, if a user loses a device), the user's authorization token can be invalidated. To invalidate the authorization token, you use Windows PowerShell to set the **StsRefreshTokenValidFrom** field for this user. You must update the **StsRefreshTokenValidFrom** field for each user for whom you want to revoke access.

To ensure that the revocation persists, you must set the **Effective Date** of the CRL to a date after the value set by **StsRefreshTokenValidFrom**, and ensure the certificate in question is in the CRL.

The following steps outline the process for updating and invalidating the authorization token by setting the **StsRefreshTokenValidFrom** field.

1. To configure revocation, use admin credentials to connect to the MSOL service:

   ``` PowerShell
   $msolcred = get-credential
   connect-msolservice -credential $msolcred
   ```

1. Retrieve the current **StsRefreshTokensValidFrom** value for a user:

    ``` PowerShell
    $user = Get-MsolUser -UserPrincipalName test@yourdomain.com`
    $user.StsRefreshTokensValidFrom
    ```

1. Configure a new **StsRefreshTokensValidFrom** value for the user equal to the current timestamp:

    ``` PowerShell
    Set-MsolUser -UserPrincipalName test@yourdomain.com -StsRefreshTokensValidFrom ("03/05/2016")
    ```

The date you set must be in the future. If that isn't the case, the **StsRefreshTokensValidFrom** property isn't set. If the date is in the future, **StsRefreshTokensValidFrom** is set to the current time, not the date indicated by `Set-MsolUser` command.

### Step 4: Test your configuration

As a first configuration test, try to sign in to Outlook Web Access or SharePoint Online using your **on-device browser**.

If the sign-in succeeds, then you know that:

* The user certificate has been provisioned to your test device.
* AD FS is configured correctly.

To test certificate-based authentication on your mobile Office application:

1. On your test device, install an Office mobile application such as OneDrive.
1. Launch the application.
1. Enter your username, and then select the user certificate you want to use.

You should be successfully signed in.

To access Exchange ActiveSync (EAS) through certificate-based authentication, an EAS profile containing the client certificate must be available to the application.

The EAS profile should contain the following information:

* The user certificate to be used for authentication.
* The EAS endpoint (for example, outlook.office365.com).

An EAS profile can be configured and placed on the device using mobile device management (MDM) such as Intune or by manually placing the certificate in the EAS profile on the device.

To test certificate authentication in Android:

1. Configure an EAS profile in the application that satisfies the requirements in the prior section.
1. Open the application and verify that mail is synchronizing.

## Learn more

- [Azure Active Directory certificate-based authentication on Android](/azure/active-directory/authentication/active-directory-certificate-based-authentication-android)
- [Azure Active Directory certificate-based authentication on iOS](/azure/active-directory/authentication/active-directory-certificate-based-authentication-ios)
- [Additional information about certificate-based authentication on Android devices](/azure/active-directory/authentication/active-directory-certificate-based-authentication-android)
- [Additional information about certificate-based authentication on iOS devices](/azure/active-directory/)
