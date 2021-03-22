Azure Active Directory Single Sign-On (Azure AD SSO) automatically signs in users when they are on their corporate devices connected to their corporate network. When enabled, users don't need to type in their passwords to sign in to Azure AD; in fact, they usually don’t even need to type in their usernames. This feature provides users with easy access to their organization’s cloud-based applications without needing any extra on-premises components.

SSO can be combined with either the Password Hash Synchronization or Pass-through Authentication sign-in methods.

:::image type="content" source="../media/aad-sso-for-contoso-fa78179b.png" alt-text="graphic of Azure Active Directory Seamless Single Sign-On for Contoso":::

Azure AD SSO creates Azure AD Connect trace log files, which can contain personal data. User privacy for Seamless SSO can be improved in two ways:

 *  Upon request, extract data for a person and remove data from that person from the installations.
 *  Ensure no data is retained beyond 48 hours.

The second option is recommended as it's easier to implement and maintain. To ensure that no data is retained beyond 48 hours, check the contents of the %ProgramData%\\AADConnect folder and delete the trace log contents (trace-\*.log files) of this folder within 48 hours of installing or upgrading Azure AD Connect or modifying Seamless SSO configuration.

> [!IMPORTANT]
> Do **NOT** delete the **PersistedState.xml** file in this folder. This file is used to maintain the state of the previous installation of Azure AD Connect and is used when an upgrade installation is performed. This file will never contain any data about a person and should never be deleted.

You can either review and delete these trace log files using Windows Explorer, or you can use the following PowerShell script to perform the necessary actions:

```
Copy

    $Files = ((Get-Item -Path "$env:programdata\aadconnect\trace-*.log").VersionInfo).FileName

    Foreach ($file in $Files) {

    {Remove-Item -Path $File -Force}

    }
```

Save the script in a file with the ".ps1" extension and then run the script as needed.

**Additional reading.** For more information, see the following article on [User privacy and Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-gdpr?azure-portal=true).

If audit logging is enabled, this product may generate security logs for your Domain Controllers. For more information, see the following article about [Configuring Audit Policies](https://technet.microsoft.com/library/dd277403.aspx?azure-portal=true).
