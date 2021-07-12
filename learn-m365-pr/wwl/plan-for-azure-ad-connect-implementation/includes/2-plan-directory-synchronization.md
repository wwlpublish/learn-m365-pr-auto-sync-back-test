Before an organization deploys directory synchronization to synchronize its on-premises Active Directory objects to Azure AD, it must prepare its environment by analyzing the following features:

 -  Active Directory preparation
 -  UPN suffixes
 -  Microsoft 365 readiness checks
 -  Microsoft 365 IdFix tool

Consider activating directory synchronization as a long-term commitment. After directory synchronization has been activated, synchronized objects can only be edited by using on-premises Active Directory management tools.

### Active Directory preparation

When preparing for deployment of directory synchronization, an organization's project plan should include Active Directory preparation, and the requirements and functionality of Azure AD. To prepare Active Directory for directory synchronization, an organization must:

 -  identify the source of authority
 -  clean-up Active Directory
 -  set up auditing

#### Source of authority

For directory synchronization, source of authority refers to the location where Active Directory service objects, such as users and groups, are mastered (an original source that defines copies of an object) in a cross-premises deployment. The source of authority can be changed for an object by using one of these scenarios:

 -  activate
 -  deactivate
 -  reactivate directory synchronization from within Microsoft 365 or with Windows PowerShell

> [!NOTE]
> Source of authority transfers from Microsoft 365 to an organization's on-premises directory service after the object is synchronized.

#### Active Directory cleanup

To help ensure a smooth transition to Microsoft 365 by using directory synchronization, an organization should prepare its Active Directory forest before it begins its Microsoft 365 directory synchronization deployment.

An organization's directory remediation efforts should focus on the following tasks:

 -  Remove duplicate **proxyAddresses** and **userPrincipalName**
 -  Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName**
 -  Remove invalid and questionable characters in the following attributes:
    
     -  givenName
     -  surname (sn)
     -  sAMAccountName
     -  displayName
     -  mail
     -  proxyAddresses
     -  mailNickname
     -  userPrincipalName

### UPN suffixes

Before deploying directory synchronization, an organization should verify that its on-premises user objects in Active Directory have a UPN suffix configured, and that the value is correct for both the Active Directory domain and Microsoft 365. The UPN suffix is the part of a UPN to the right of the @ character; for example, **@adatum.com**.

When an Internet routable domain is used as the UPN, then this domain should be the UPN suffix. In doing so, the users' principal names should be in the form **user@domain**. If the on-premises UPN suffix doesn't contain an Internet routable DNS domain (such as adatum.local), the default routing domain (for example, adatum.onmicrosoft.com) is used for the UPN suffix in Microsoft 365.

As a best practice, it's recommended that the primary SMTP email address of each user be used as their UPN. The reason for this recommendation is that several applications, such as Skype for Business, ask for the email address in their sign-in window. Since they technically require the UPN sign-in name, using the primary SMTP email as their UPN address can reduce confusion.

If the UPN suffix must be changed in the on-premises Active Directory, it's important to check for any applications that may be dependent on a specific UPN.

If directory synchronization has already been deployed, the user’s UPN for Microsoft 365 may not match the user’s on-premises UPN defined in Active Directory. This mismatch can occur if the user was assigned a Microsoft 365 subscription license before the domain was verified. To resolve this issue, Windows PowerShell can be used to update users’ UPNs in Microsoft 365. This resolution will ensure each user's Microsoft 365 UPN matches their corporate user name and domain in the on-premises Active Directory.

### Microsoft 365 readiness checks

The Microsoft 365 readiness checks (formerly the Microsoft 365 OnRamp tool) run automatic checks against a current on-premises environment and assess its readiness to deploy Microsoft 365. These checks are read-only and don't make permanent changes to the on-premises environment. They also identify the configuration steps that an organization must complete to deploy its Microsoft 365 tenant.

Depending on the type of Microsoft 365 deployment required, the Microsoft 365 readiness checks will validate the following objects:

 -  **Credentials.** Determines whether there are valid credentials available in the local environment, including necessary administrator rights in Exchange Server 2013 or later if migrating to Exchange Online. It also determines whether there are valid tenant administrator credentials for any existing trial accounts with Microsoft 365.
 -  **Network.** Determines whether there's network connectivity to Microsoft 365 and checks for availability of required ports.
 -  **Domains.** Determines the on-premises domain suffixes and identifies whether any domains are already verified with Microsoft 365. Appropriate DNS records are also checked.
 -  **Users and groups.** Determines whether the on-premises Active Directory is ready for directory synchronization and SSO. User and group objects are also checked to ensure they meet the requirements for successful synchronization with Microsoft 365.
 -  **Email.** Evaluates messaging integration with the on-premises environment and the readiness for email migration.
 -  **SharePoint sites.** Determines whether the on-premises AD environment can support the deployment of Microsoft SharePoint Online.
 -  **Skype for Business.** Identifies any current integration with Skype for Business Server 2016 or Lync Server.
 -  **User software.** Determines whether domain-joined computers meet the service and identity requirements for the required Microsoft 365 deployment.

To view service health, in the Microsoft 365 admin center, go to **Health &gt; Service health**, or select the **Service health** card on the **Home** dashboard. The dashboard card indicates whether there's an active service issue and links to the detailed **Service health** page.

### Microsoft 365 IdFix tool

While the Microsoft 365 readiness checks provide valuable information about an organization's environment, they don't resolve any issues identified by the tool. Instead, it's the job of the IdFix DirSync Error Remediation tool to resolve these issues. The IdFix tool identifies and fixes most of the object synchronization errors in Active Directory forests in preparation for deployment to Microsoft 365. This remediation enables an organization to successfully synchronize users, contacts, and groups from its on-premises Active Directory into Microsoft 365.

The IdFix tool queries all the Active Directory domains in the currently authenticated forest and displays object attribute values that would be reported as errors by the directory synchronization tool. The IdFix tool displays these object attribute values in a data grid, which supports the ability to scroll, sort, and edit the objects. Depending on the method of use, the Microsoft 365 IdFix tool provides:

 -  **Confirmation that each change is enforced.** Only the objects that are selected to be updated will be changed.
 -  **Transaction rollback.** Confirmed updates to object attributes applied to the forest can be undone.
 -  **Well-known exclusions.** Not all Active Directory objects should be made available for editing as some could cause harm to the source environment, such as critical system objects. These objects are excluded from the Microsoft 365 IdFix data grid.
 -  **Save to File.** Data is exported into CSV or LDF format for offline editing or investigation.
 -  **Import of CSV.** Data is imported from a CSV file. Because this function relies upon the **distinguishedName** attribute to determine the value to update, the recommended method to use this feature is to export from a query, such as the **Save to File**. Keep the other columns as they were and don't introduce escape characters into the values.
 -  **Verbose logging.** Because the Microsoft 365 IdFix tool makes changes in an organization's environment, verbose logging is enabled by default.
 -  **Support for multi-tenant and dedicated Microsoft 365 tenants.** Depending on an organization's environment, the Microsoft 365 IdFix tool supports validation of multiple or dedicated Microsoft 365 tenants.

> [!WARNING]
> The IdFix tool must be used with caution because it enables changes to bulk-update objects.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”