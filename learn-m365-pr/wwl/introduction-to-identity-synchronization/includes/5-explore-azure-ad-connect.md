The Azure Active Directory Connect (Azure AD Connect) tool, formerly known as Windows Azure Active Directory Synchronization or DirSync, is the officially recommended directory synchronization tool for Microsoft 365. Azure AD Connect is a software-based tool that an organization configures once, and it automatically runs in the background without user interaction. For Microsoft 365, the purpose of the tool is to enable coexistence between an organization's on-premises Active Directory environment and its Microsoft 365 tenant in the cloud.

Azure AD Connect is made up of three parts:

 -  The synchronization services.
 -  The optional Active Directory Federation Services piece.
 -  The monitoring piece, which is done using Azure AD Connect Health.

### Using Azure AD Connect for directory synchronization

Azure AD Connect provides synchronization of objects between Active Directory and Azure AD, the directory for Microsoft 365.

When using Azure AD Connect for directory synchronization:

 -  New user, group, and contact objects in on-premises Active Directory are added to Microsoft 365. However, Microsoft 365 licenses aren't automatically assigned to these objects.
 -  Attributes of existing user, group, and contact objects that are modified in on-premises Active Directory are modified in Microsoft 365. However, not all on-premises Active Directory attributes are synchronized to Microsoft 365.
 -  Existing user, group, and contact objects that are deleted from on-premises Active Directory are then deleted from Microsoft 365.
 -  Existing user objects that are disabled on-premises are then disabled in Microsoft 365. However, licenses aren't automatically unassigned.

Azure AD Connect supports the following scenarios:

 -  Multiple Active Directory forest environments.
 -  Multiple Exchange organizations to one Microsoft 365 tenant.

Azure AD requires a single source of authority for every object. As such, when an organization has deployed Azure AD Connect for Active Directory synchronization, there are two things that are important to understand:

 -  The source of authority is the on-premises Active Directory.
 -  Objects are mastered from within the on-premises Active Directory by using whatever management tools the organization currently uses, such as Active Directory Users and Computers or Windows PowerShell.

In this scenario, after the first synchronization cycle has completed, the source of authority is transferred from the cloud to the on-premises Active Directory. All later changes to cloud objects (except for licensing) are mastered from the on-premises Active Directory tools. The corresponding cloud objects are read-only, and Microsoft 365 administrators can't edit cloud objects if the source of authority is on-premises.

The following graphic show that Azure AD Connect reads user objects from the on-premises Active Directory, and it then creates exact copies in Azure AD with the same Active Directory attributes, but non-writable/write protected.

:::image type="content" source="../media/aad-connect-writing-objects-to-aad-bd871e3e.jpg" alt-text="graphic shows that Azure AD Connect reads user objects from the on-premises Active Directory and it then creates exact copies in Azure AD with the same Active Directory attributes":::


### Azure AD Connect features

Azure AD Connect comes with several features that can either be turned on or are enabled by default:

 -  **Exchange hybrid deployment.** Used to implement an Exchange hybrid deployment with one or multiple on-premises Exchange organizations.
 -  **Exchange mail-enabled public folders.** Synchronizes mail-enabled public folder objects from on-premises Active Directory to Azure AD. These objects include public folder addresses in Directory-Based Edge Blocking. This option doesn't create the public folder objects in Exchange Online. Creating these objects requires running a Windows PowerShell script.
 -  **Azure AD app and object filtering.** This feature is used when an organization wants to limit which objects are synchronized to Azure AD. By default, all users, contacts, groups, and Windows 10 computers are synchronized. The filtering can be changed based on domains, OUs, or attributes.
 -  **Password hash synchronization.** Synchronizes the Active Directory password hashes to Azure AD. The end user can use the same password on-premises and in the cloud but only manage it in one location by default. Since password hash synchronization uses an organization's on-premises Active Directory as the authority, the organization can also use its own password policy.

    > [!NOTE]
    > Self-service password reset can be enabled through the Azure console.

 -  **Password passthrough authentication.** This configuration validates users’ passwords directly against an organization's on-premises Active Directory using an encrypted public key. This validation occurs between Azure and the on-premises Active Directory environment without sending password hashes to Microsoft 365. For more information, see [Azure Active Directory Passthrough Authentication](/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-how-it-works).
 -  **Password writeback.** Users can change and reset their passwords in the cloud and have their organization's on-premises password policy applied.
 -  **Group writeback.** Allows all Microsoft 365 groups to be synchronized to their organization's Active Directory.
 -  **Device writeback.** A device registered in Azure AD can be written back to on-premises Active Directory so that it can be used for Conditional Access.
 -  **Directory extension attribute sync.** Directory extensions enable an organization to extend the schema in Azure AD with the attributes from its on-premises Active Directory.
 -  **Prevent accidental deletes.** This feature is turned on by default and protects an organization's cloud directory from many deletes at the same time. By default, it allows 500 deletes per run. This setting can be changed depending on the organization's size.
 -  **Automatic upgrade.** This feature is enabled by default for express settings installations. It ensures that an organization's version of Azure AD Connect is always up to date with the latest release.
 -  **SSO using AD FS.** Configures an Active Directory Federated Services environment to support single-sign on (SSO) in Microsoft 365.
 -  **Seamless single sign-on (SSO) using Pass-through authentication (PTA).** Allows sign in to Azure AD by directly validating the users’ passwords directly against on-premises Active Directory.

> [!TIP]
> As Azure AD Connect features continuously improve and change, it's important to regularly visit the [Azure AD Connect: Version release history](/azure/active-directory/connect/active-directory-aadconnect-version-history) site for information on recent changes.
