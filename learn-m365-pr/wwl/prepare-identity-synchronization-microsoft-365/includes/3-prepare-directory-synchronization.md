Today, businesses are often becoming a mixture of on-premises and cloud applications. Users require access to applications both on-premises and in the cloud. This design requires the need to have a single identity across these various on-premises and cloud applications.

Provisioning is the process of:

 -  Creating an object based on certain conditions.
 -  Keeping the object up to date.
 -  Deleting the object when conditions are no longer met.

For example, when a new user joins an organization, the user is entered into the company's Human Resources (HR) system. At that point, provisioning can create a corresponding user account in the cloud (Azure AD), in on-premises Active Directory, and different applications the user needs access to. Identity provisioning enables the user to start work and have access to the applications and systems they need on day one.

:::image type="content" source="../media/identity-provisioning-a1ab3a24.png" alt-text="diagram showing how identity provisioning includes HR provisioning, directory provisioning, and app provisioning.":::


On-premises identity provisioning involves provisioning from on-premises sources (like Active Directory) to Azure AD. The most common scenario occurs when a user in on-premises Active Directory is provisioned into Azure AD. Identity provisioning is accomplished through directory synchronization using either Azure AD Connect sync or Azure AD Connect Cloud Sync.

Before an organization deploys directory synchronization to synchronize its on-premises Active Directory objects to Azure AD, it must prepare its environment by analyzing the following features:

 -  Active Directory preparation
 -  UPN suffixes
 -  Microsoft 365 IdFix tool

Consider activating directory synchronization as a long-term commitment. After directory synchronization has been activated, synchronized objects can only be edited by using on-premises Active Directory management tools.

### Active Directory preparation

When an organization prepares to deploy directory synchronization, it must first prepare its on-premises Active Directory. To prepare Active Directory for directory synchronization, an organization must:

 -  identify the source of authority
 -  clean-up Active Directory
 -  set up auditing

#### Source of authority

For directory synchronization, source of authority refers to the location where Active Directory service objects, such as users and groups, are mastered (an original source that defines copies of an object) in a cross-premises deployment. The source of authority can be changed for an object by using one of these scenarios:

 -  activate
 -  deactivate
 -  reactivate directory synchronization from within Microsoft 365 or with Windows PowerShell

> [!NOTE]
> Once an object is synchronized, its source of authority transfers from Microsoft 365 to the organization's on-premises directory service.

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

Before an organization deploys directory synchronization, it should verify that:

 -  Its on-premises user objects in Active Directory have a UPN suffix configured. The UPN suffix is the part of a UPN to the right of the @ character; for example, **@adatum.com** and **@contoso.com**.
 -  The UPN suffix value is correct for both the Active Directory domain and Microsoft 365.

When an Internet routable domain is used as the UPN, then this domain should be the UPN suffix. In doing so, the users' principal names should be in the form **user@domain**. If the on-premises UPN suffix doesn't contain an Internet routable DNS domain (such as adatum.local), the default routing domain (for example, adatum.onmicrosoft.com) is used for the UPN suffix in Microsoft 365.

> [!TIP]
> As a best practice, it's recommended that the primary SMTP email address of each user be used as their UPN. The reason for this recommendation is that several applications, such as Skype for Business, ask for the email address in their sign-in window. Since they technically require the UPN sign-in name, using the primary SMTP email as their UPN address can reduce confusion.

If the UPN suffix must be changed in the on-premises Active Directory, it's important to check for any applications that may be dependent on a specific UPN.

If directory synchronization has already been deployed, the user’s UPN for Microsoft 365 may not match the user’s on-premises UPN defined in Active Directory. This mismatch can occur if the user was assigned a Microsoft 365 subscription license before the domain was verified. To resolve this issue, Windows PowerShell can be used to update users’ UPNs in Microsoft 365. This resolution will ensure each user's Microsoft 365 UPN matches their corporate user name and domain in the on-premises Active Directory.

### Microsoft 365 IdFix tool

The IdFix DirSync Error Remediation tool identifies and fixes most of the object synchronization errors in Active Directory forests. Organizations should run this tool in preparation for identity synchronization to Microsoft 365. This remediation enables an organization to successfully synchronize users, contacts, and groups from its on-premises Active Directory into Microsoft 365.

The IdFix tool queries all the Active Directory domains in the currently authenticated forest. It then displays object attribute values that would be reported as errors by the directory synchronization tool. The IdFix tool displays these object attribute values in a data grid. This design supports the ability to scroll, sort, and edit the objects.

Depending on the method of use, the Microsoft 365 IdFix tool provides:

 -  **Confirmation that each change is enforced.** The IdFix tool displays a list of objects that have potential errors. An admin should review the list and select the objects they want the IdFix tool to fix. The IdFix tool will only change the selected objects.
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