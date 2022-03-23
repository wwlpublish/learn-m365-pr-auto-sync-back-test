Depending on business needs, technical requirements, or both, directory synchronization is the most common provisioning choice for enterprise customers who are moving to Microsoft 365. Directory synchronization enables identities to be managed in the on-premises Active Directory, and all updates to those identities are synchronized to Microsoft 365. The benefits of directory synchronization for an organization include:

 -  Reducing the administrative programs in the organization
 -  Optionally enabling single sign-on scenario
 -  Automating account changes in Microsoft 365

However, directory synchronization requires planning and preparation to ensure that your Active Directory Domain Services (AD DS) synchronizes to the Azure AD tenant of your Microsoft 365 subscription with a minimum of errors. There are a couple of things to keep in mind when planning an implementation of directory synchronization, including directory preparation, and the requirements and functionality of the Azure Active Directory.

Directory preparation covers quite a few areas, including attribute updates, auditing, and planning domain controller placement. Planning requirements and functionality include determining the permissions that are required, planning for multi-forest/directory scenarios, capacity planning, and two-way synchronization. This unit explores two common tasks in preparing an AD forest for directory synchronization - cleaning up your AD by running IdFix, and preparing a non-routable domain for directory synchronization.

### Use IdFix to clean up your Active Directory

When an organization cleans up its Active Directory, it should focus on the following tasks:<br>

 -  Remove duplicate proxyAddress and userPrincipalName attributes.
 -  Update blank and invalid userPrincipalName attributes with valid userPrincipalName attributes.
 -  Remove invalid and questionable characters in the givenName, surname (sn), sAMAccountName, displayName, mail, proxyAddresses, mailNickname, and userPrincipalName attributes. For details about preparing attributes, see the [List of attributes that are synced by the Azure Active Directory Sync Tool](https://social.technet.microsoft.com/wiki/contents/articles/19901.dirsync-list-of-attributes-that-are-synced-by-the-azure-active-directory-sync-tool.aspx?azure-portal=true).

To help ensure a smooth transition to Microsoft 365 by using synchronization, it's highly recommended that organizations run the IdFix utility. IdFix will help to prepare an organization's Active Directory forest before it begins its Microsoft 365 directory synchronization deployment.

Microsoft is continually working to reduce the time required to remediate identity issues when onboarding to Microsoft 365. A portion of this effort is intended to address the time involved in remediating the Windows Server Active Directory (Windows Server AD) errors reported by Microsoft's directory synchronization tools, Azure AD Connect sync and Azure AD Connect Cloud Sync. IdFix is designed to enable organizations to accomplish this task in a simple, expedient fashion.

The IdFix tool provides organizations with the ability to query, identify, and remediate most object synchronization errors in their Window’s Server AD forests in preparation for deployment to Microsoft 365. The utility doesn't fix all errors, but it does find and fix most of them. This remediation enables organizations to successfully synchronize their users, contacts, and groups from on-premises Active Directory into Microsoft 365.

IdFix may identify errors beyond those issues that emerge during synchronization. The most common example is compliance with [Request for Comments (RFC) 2822](https://www.rfc-wiki.org/wiki/RFC2822?azure-portal=true) for SMTP addresses. Although invalid attribute values can be synchronized to the cloud, it's recommended that these errors be corrected.

IdFix queries all domains in the currently authenticated forest and displays object attribute values that would be reported as errors by the supported directory synchronization tool. The DataGrid view supports the ability to scroll, sort, and edit those objects in a resulting table to produce compliant values. Confirmed values can then be applied to the forest with the ability to undo updates. Transaction rollback is also supported.

When IdFix encounters invalid characters, a suggested “fix” is displayed where it can be determined from the existing value. Changes are applied only to records for which you have set an ACTION value. Confirmation of each change is enforced.

Suggested values for formatting errors start with the removal of invalid characters. The organization must then update the value. It's beyond the scope of this utility to determine what an organization wants when a mistake in formatting is detected.

Data can be exported into CSV or LDF format for offline editing or investigation. Save to File is also supported.

Because IdFix makes changes in an organization's on-premises environment, logging is included. Verbose logging is enabled by default.

### Prepare a non-routable domain for directory synchronization

When you synchronize your on-premises directory with Microsoft 365, you must have a verified domain in Azure Active Directory (Azure AD). Only the User Principal Names (UPNs) that are associated with the on-premises Active Directory Domain Services (AD DS) domain are synchronized. However, any UPN that contains a non-routable domain, such as ".local" (example: holly@contoso.local), will be synchronized to an .onmicrosoft.com domain (example: holly@contoso.onmicrosoft.com).

If you currently use a ".local" domain for your user accounts in AD DS, it's recommended that you change them to use a verified domain, such as holly@contoso.com, to properly synchronize with your Microsoft 365 domain.

Both of Microsoft's directory synchronization tools - Azure AD Connect sync and Azure AD Connect Cloud Sync - are used for synchronizing your AD DS to the Azure AD tenant of your Microsoft 365 tenant. These tools synchronize your users' UPN and password so that users can sign in with the same credentials they use on-premises.

However, the directory synchronization tools only synchronize users to domains that are verified by Microsoft 365. This design means the domain is also verified by Azure AD, because Microsoft 365 identities are managed by Azure AD. In other words, the domain has to be a valid Internet domain (such as, .com, .org, .edu, and so on). If your internal AD DS only uses a non-routable domain (for example, ".local"), it can't possibly match the verified domain you have for your Microsoft 365 tenant. You can fix this issue by either changing your primary domain in your on-premises AD DS, or by adding one or more UPN suffixes.

 -  **Change your primary domain**. This option enables an organization to change its primary domain to a domain it's verified in Microsoft 365; for example, contoso.com. In this example, every user that has the domain contoso.local will be updated to contoso.com.
 -  **Add UPN suffixes and update your users to them**. The process of changing your primary domain, as described in the prior item, can be quite involved. An easier solution is to add UPN suffixes and update your users to them. You can solve the ".local" problem by registering a new UPN suffix or suffixes in AD DS to match the domain (or domains) you verified in Microsoft 365. After you register the new suffix, you must update the user UPNs to replace the ".local" with the new domain name, so that a user account looks like holly@contoso.com. After you've updated the UPNs to use the verified domain, you're ready to synchronize your on-premises AD DS with Microsoft 365.
