With Co-management, an organization's Windows 10 devices are managed by Configuration Manager and Intune at the same time. To configure Co-management, an organization's infrastructure must meet the prerequisites outlined in the following sections.

### Licensing

Co-management requires the following licenses:

 -  **Azure AD Premium.** An Enterprise Mobility + Security (EMS) subscription includes both Azure Active Directory Premium and Microsoft Intune.
 -  **Intune.** At least one Intune license for you as the administrator to access the Intune portal. An Intune license must be assigned to the account that you use to sign in to your tenant. Otherwise, sign in will fail.
    
    You may not need to purchase and assign individual Intune or EMS licenses to your users. For more information, see the [Product and licensing FAQ](https://docs.microsoft.com/mem/configmgr/core/understand/product-and-licensing-faq#what-changes-with-licensing-for-co-management-in-microsoft-endpoint-manager-?azure-portal=true).

### Configuration Manager

Co-management requires Configuration Manager version 1710 or later. Starting in Configuration Manager version 1806, you can connect multiple Configuration Manager instances to a single Intune tenant.

### Azure AD

Windows 10 devices must be connected to Azure AD. They can be either of the following types:

 -  **Hybrid Azure AD-joined.** If your environment has an on-premises AD footprint and you also want to benefit from the capabilities provided by Azure Active Directory, you can implement hybrid Azure AD joined devices. These devices are devices that are joined to your on-premises Active Directory and registered with your Azure Active Directory.
 -  **Azure AD-joined only.** Azure AD join allows you to join devices directly to Azure AD without the need to join to on-premises Active Directory. This design still keeps your users productive and secure. This type is sometimes referred to as "cloud domain-joined".

> [!TIP]
> Microsoft constantly talks with its customers that use Microsoft Endpoint Manager to deploy, manage, and secure their client devices. In these conversations, customers often ask questions about co-managing devices and hybrid Azure AD joined devices. Many customers confuse these two services. To help clarify this situation, remember this one fact: Co-management is a management option, while Azure AD is an identity option.<br>

**Additional reading.** For more information that examines hybrid Azure AD join and co-management, how they work together, but aren't the same thing, see [Understanding hybrid Azure AD and co-management scenarios](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201?azure-portal=true).

### Intune

There are two prerequisites to using Intune - setting it up and enabling Windows 10 automatic enrollment. For detailed information on the steps involved in these tasks, see the following links:

 -  [Set up Intune](/intune/setup-steps).<br>
 -  [Enable Windows 10 automatic enrollment](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment?azure-portal=true).

### Windows 10

Upgrade your devices to Windows 10, version 1709 or later. For more information, see [Adopting Windows as a service](https://docs.microsoft.com/mem/configmgr/core/understand/configuration-manager-and-windows-as-service#key-articles-about-adopting-windows-as-a-service?azure-portal=true).

> [!IMPORTANT]
> Windows 10 mobile devices don't support co-management.<br>

For devices that are running Windows 7 or Windows 8.1, it's recommended to upgrade them to Windows 10. Android, Mac, and iOS devices cannot be managed by Configuration Manager alone. Instead, you can manage them with Configuration Manager if it's connected to Intune or by Intune standalone.

### Permissions and roles

:::row:::
  :::column:::
    **Action**
  :::column-end:::
  :::column:::
    **Role needed**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Set up a cloud management gateway in Configuration Manager
  :::column-end:::
  :::column:::
    Azure Subscription Manager
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Create Azure AD apps from Configuration Manager
  :::column-end:::
  :::column:::
    Azure AD Global Administrator
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Import Azure apps in Configuration Manager
  :::column-end:::
  :::column:::
    Configuration Manager Full Administrator
No other Azure roles needed
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Enable co-management in Configuration Manager
  :::column-end:::
  :::column:::
    An Azure AD user
Configuration Manager Full Administrator with All scope rights.
  :::column-end:::
:::row-end:::


**Additional reading.** For more information about Azure roles, see [Understand the different roles](/azure/role-based-access-control/rbac-and-directory-admin-roles). For more information about Configuration Manager roles, see [Fundamentals of role-based administration](/mem/configmgr/core/understand/fundamentals-of-role-based-administration).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”