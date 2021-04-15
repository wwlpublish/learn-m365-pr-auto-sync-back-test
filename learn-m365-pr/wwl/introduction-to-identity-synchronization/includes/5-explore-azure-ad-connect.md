The Azure Active Directory Connect (Azure AD Connect) tool, formerly known as Windows Azure Active Directory Synchronization or DirSync, is the officially recommended directory synchronization tool for Microsoft 365. Azure AD Connect is a software-based tool that you configure once, and it automatically runs in the background without user interaction. For Microsoft 365, the purpose of the tool is to enable coexistence between your on-premises Active Directory environment and Microsoft 365 in the cloud.

Azure AD Connect is made up of three parts - the synchronization services, the optional Active Directory Federation Services piece, and the monitoring piece, which is done using Azure AD Connect Health.

### Using Azure AD Connect for directory synchronization

Azure AD Connect provides synchronization of objects between Active Directory and Azure AD, the directory for Microsoft 365.

When using Azure AD Connect for directory synchronization:

 *  New user, group, and contact objects in on-premises Active Directory are added to Microsoft 365; however, Microsoft 365 licenses aren't automatically assigned to these objects.
 *  Attributes of existing user, group, and contact objects that are modified in on-premises Active Directory are modified in Microsoft 365; however, not all on-premises Active Directory attributes are synchronized to Microsoft 365.
 *  Existing user, group, and contact objects that are deleted from on-premises Active Directory are then deleted from Microsoft 365.
 *  Existing user objects that are disabled on-premises are then disabled in Microsoft 365; however, licenses aren't automatically unassigned.

Azure AD Connect supports the following scenarios:

 *  Multiple Active Directory forest environments.
 *  Multiple Exchange organizations to one Microsoft 365 tenant.

Azure AD requires a single source of authority for every object. As such, in the scenario in which you have deployed Azure AD Connect for Active Directory synchronization, there are two things that are important to understand:

 *  The source of authority is the on-premises Active Directory.
 *  You're mastering objects from within your on-premises Active Directory by using whatever management tools you're using today, such as Active Directory Users and Computers or Windows PowerShell.

In this scenario, after the first synchronization cycle has completed, the source of authority is transferred from the cloud to the on-premises Active Directory. All later changes to cloud objects (except for licensing) are mastered from the on-premises Active Directory tools. The corresponding cloud objects are read-only, and Microsoft 365 administrators can't edit cloud objects if the source of authority is on-premises.

The following graphic show that Azure AD Connect reads user objects from the on-premises Active Directory, and it then creates exact copies in Azure AD with the same Active Directory attributes, but non-writable/write protected.

:::image type="content" source="../media/aad-connect-writing-objects-to-aad-bd871e3e.jpg" alt-text="graphic shows that Azure AD Connect reads user objects from the on-premises Active Directory and it then creates exact copies in Azure AD with the same Active Directory attributes":::


### Azure AD Connect features

Azure AD Connect comes with several features you can optionally turn on or are enabled by default:

 *  **Exchange hybrid deployment.** Used to implement an Exchange hybrid deployment with one or multiple on-premises Exchange organizations.
 *  **Exchange mail-enabled public folders.** Synchronizes mail-enabled public folder objects from on-premises Active Directory to Azure AD. These objects include public folder addresses in Directory-Based Edge Blocking. This option doesn't create the public folder objects in Exchange Online; to do so requires running a Windows PowerShell script.
 *  **Azure AD app and object filtering.** Is used when you want to limit which objects are synchronized to Azure AD. By default, all users, contacts, groups, and Windows 10 computers are synchronized. You can change the filtering based on domains, OUs, or attributes.
 *  **Password hash synchronization.** Synchronizes the password hash in Active Directory to Azure AD. The end user can use the same password on-premises and in the cloud but only manage it in one location by default. Since it uses your on-premises Active Directory as the authority, you can also use your own password policy (Note: You can enable self-service password reset through the Azure console).
 *  **Password passthrough authentication.** This configuration validates users’ passwords directly against your on-premises Active Directory using an encrypted public key between Azure and the on-premises Active Directory environment without sending password hashes to Microsoft 365. For more information, see the following article on [Azure Active Directory Passthrough Authentication](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-how-it-works?azure-portal=true).
 *  **Password writeback.** Will allow your users to change and reset their passwords in the cloud and have your on-premises password policy applied.
 *  **Group writeback.** Allows all Microsoft 365 groups to be synchronized to your Active Directory.
 *  **Device writeback.** Will allow a device registered in Azure AD to be written back to on-premises Active Directory so it can be used for conditional access.
 *  **Directory extension attribute sync.** Directory extensions enable you to extend the schema in Azure AD with your own attributes from on-premises Active Directory.
 *  **Prevent accidental deletes.** Is turned on by default and protects your cloud directory from many deletes at the same time. By default, it allows 500 deletes per run. You can change this setting depending on your organization size.
 *  **Automatic upgrade.** Is enabled by default for express settings installations and ensures your Azure AD Connect is always up to date with the latest release.
 *  **SSO using AD FS.** Configures an Active Directory Federated Services environment to support single-sign on (SSO) in Microsoft 365.
 *  **Seamless single sign-on (SSO) using Pass-through authentication (PTA).** Allows sign in to Azure AD by directly validating the users’ passwords directly against on-premises Active Directory.

> [!TIP]
> As Azure AD Connect features continuously improve and change, it's important to regularly visit the [Azure AD Connect: Version release history](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-version-history?azure-portal=true) site for information on recent changes.
