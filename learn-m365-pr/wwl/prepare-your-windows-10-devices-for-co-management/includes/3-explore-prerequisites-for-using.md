With Co-management, an organization's Windows 10 and later devices are managed by Configuration Manager and Intune at the same time. To configure Co-management, an organization's infrastructure must meet the prerequisites outlined in the following sections.

### Licensing

Co-management requires the following licenses:

 -  **Azure Active Directory Premium.** An Enterprise Mobility + Security (EMS) subscription includes both Azure Active Directory Premium and Microsoft Intune.
 -  **Intune.** At least one Intune license is needed for an administrator to access the Intune portal. An Intune license must be assigned to the account the administrator uses to sign in to the company's tenant. Otherwise, sign in will fail.

> [!NOTE]
> An organization may not need to purchase and assign individual Intune or EMS licenses to its users. For more information, see the [Product and licensing FAQ](/mem/configmgr/core/understand/product-and-licensing-faq#what-changes-with-licensing-for-co-management-in-microsoft-endpoint-manager-?azure-portal=true).

### Configuration Manager

Co-management requires Configuration Manager version 1710 or later. Organizations that have Configuration Manager version 1806 or later can connect multiple Configuration Manager instances to a single Intune tenant.

### Azure Active Directory

Windows 10 and later devices must be connected to Azure AD using either of the following connections:

 -  **Hybrid Azure AD-joined**. An organization that has an on-premises AD footprint can still benefit from the capabilities provided by Azure Active Directory. To do so, it must implement hybrid Azure AD joined devices. These devices are joined to an organization's on-premises Active Directory and registered with its Azure Active Directory.
 -  **Azure AD-joined only.** Azure AD join enables an organization to join devices directly to Azure AD without the need to join to on-premises Active Directory. This design still keeps the organization's users productive and secure. This type of connectivity is sometimes referred to as "cloud domain-joined".

> [!TIP]
> Microsoft constantly talks with its customers that use Microsoft Endpoint Manager to deploy, manage, and secure their client devices. In these conversations, customers often ask questions about co-managing devices and hybrid Azure AD joined devices. Many customers confuse these two services. To help clarify this situation, remember this one fact: **Co-management is a management option, while Azure AD is an identity option.**

**Additional reading.** For more information that examines hybrid Azure AD join and co-management, how they work together, but aren't the same thing, see [Understanding hybrid Azure AD and co-management scenarios](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201?azure-portal=true).

### Microsoft Intune

There are two prerequisites to using Intune:

 -  setting it up.
 -  enabling Windows 10 automatic enrollment.

**Additional reading**. For more information on the steps involved in these tasks, see the following links:

 -  [Set up Intune](/intune/setup-steps?azure-portal=true).
 -  [Enable Windows automatic enrollment](/intune/windows-enroll#enable-windows-10-automatic-enrollment?azure-portal=true).

### Windows devices

Upgrade your devices to Windows 10, version 1709 or later. For more information, see [Adopting Windows as a service](/mem/configmgr/core/understand/configuration-manager-and-windows-as-service#key-articles-about-adopting-windows-as-a-service?azure-portal=true).

> [!IMPORTANT]
> Windows 10 mobile devices don't support co-management.

For devices that run Windows 7 or Windows 8.1, it's recommended to upgrade them to Windows 10 or later. Android, Mac, and iOS devices can't be managed by Configuration Manager alone. Instead, you can manage them with Configuration Manager if it's connected to Intune or by Intune standalone.

### Permissions and roles

| **Action**                                                 | **Role needed**                                                                     |
| ---------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| Set up a cloud management gateway in Configuration Manager | Azure Subscription Manager                                                          |
| Create Azure AD apps from Configuration Manager            | Azure AD Global Administrator                                                       |
| Import Azure apps in Configuration Manager                 | Configuration Manager Full Administrator<br>No other Azure roles needed             |
| Enable co-management in Configuration Manager              | An Azure AD user<br>Configuration Manager Full Administrator with All scope rights. |

**Additional reading.** For more information about Azure roles, see [Understand the different roles](/azure/role-based-access-control/rbac-and-directory-admin-roles?azure-portal=true). For more information about Configuration Manager roles, see [Fundamentals of role-based administration](/mem/configmgr/core/understand/fundamentals-of-role-based-administration?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”