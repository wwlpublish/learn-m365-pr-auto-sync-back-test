Before you can set up co-management, you must set up or already have the following prerequisites:

- The correct licensing for Microsoft Intune and Azure Active Directory Premium
- A current version of Configuration Manager
- Windows client devices that are running Windows 10 or later
- Azure AD for your Windows client devices
- Windows 10 (or later) automatic enrollment with Intune
- Proper permissions and roles

Each of these requirements are presented in the following sections.

## Licensing

You will need licenses for the following products:
- Microsoft Intune
- Azure AD Premium

A Microsoft Intune license is created for you when you sign up for the Intune free trial. As part of this trial, you'll also have a trial Enterprise Mobility + Security (EMS) subscription. An Enterprise Mobility + Security (EMS) subscription includes both Azure Active Directory Premium and Microsoft Intune.

> [!NOTE]
> If you are unable to access this portal using the step below, or if you don't have an Intune license, you can sign up now for the [Intune free trial](/mem/intune/fundamentals/free-trial-sign-up). When setting up Intune, you can give an administrators access to Microsoft Endpoint Manager [without them requiring an Intune license](/mem/intune/fundamentals/unlicensed-admins).

To confirm your Microsoft Intune license or trial, use the following steps:

1. Sign in to [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** > **Tenant status**.<br>
   Under the **Tenant details** tab, you will see the **MDM authority**, the **Total licenses users**, and the **Total Intune licenses**.
3. Select **Tenant administration** > **Roles** > **My permissions**.
4. Confirm you are an **administrator** with **full** permissions to **all** Intune resources.

> [!NOTE]
> For more in-depth information about Microsoft Intune, see the learning module: [Set up Microsoft Intune](/learn/modules/set-up-microsoft-intune?azure-portal=true).

To check on your Azure AD Premium license, use the following steps:

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **Azure Active Directory**. Under **Basic information**, view your license.

If you don't have a license for Azure AD Premium, see [Sign up for Azure Active Directory Premium editions](/azure/active-directory/fundamentals/active-directory-get-started-premium).

  > [!Tip]
  > You may not need to purchase and assign individual Intune or EMS licenses to your users. For more information, see the [Product and licensing FAQ](/mem/configmgr/core/understand/product-and-licensing-faq.md#what-changes-with-licensing-for-co-management-in-microsoft-endpoint-manager-).

## Microsoft Endpoint Configuration Manager

Enabling co-management itself doesn't require that you onboard your site with Azure AD. Internet-based Configuration Manager clients require the [cloud management gateway](/mem/configmgr/core/clients/manage/cmg/overview) (CMG). The CMG requires the site is [onboarded to Azure AD for cloud management](/mem/configmgr/core/servers/deploy/configure/azure-services-wizard.md).

To check the version of Configuration Manager:

1. Open the Configuration Manager console.<br>
   For specific details about connecting and working with the Configuration Manager console, see [How to use the Configuration Manager console](/mem/configmgr/core/servers/manage/admin-console).
2. In the console, go to **About Configuration Manager** at the top-left corner of the console.<br>
   This dialog displays the site and console versions. For more information, see [Updates and servicing for Configuration Manager](/mem/configmgr/core/servers/manage/updates).
3. Confirm the version of Configuration Manager is a [supported version](/mem/configmgr/core/servers/manage/updates#supported-versions).

## Azure Active Directory (Azure AD)

[Azure AD](/azure/active-directory/fundamentals/active-directory-whatis) is Microsoft’s cloud-based identity and access management service, which helps the people at your organization sign in and access resources. Your on-premises Windows 10 or later devices must be connected to Azure AD to use co-management. You can choose either of the following types:  

  - [Hybrid Azure AD-joined](/azure/active-directory/devices/concept-azure-ad-join-hybrid), where the device is joined to your on-premises Active Directory and registered with your cloud-based Azure Active Directory.
  - [Azure AD-joined](/azure/active-directory/devices/azureadjoin-plan) only. This type is sometimes referred to as "cloud domain-joined".  

> [!TIP]
> It's important to understand the difference between co-managed devices and hybrid Azure Active Directory (Azure AD) joined devices. Co-management is a management option, while Azure AD is an identity option. For more information about these differences and how they work together, see [Understanding hybrid Azure AD and co-management scenarios](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201).

## Microsoft Intune

Intune, which is required for co-management, is a cloud-based service that focuses on mobile device management (MDM) and mobile application management (MAM). You control how your organization’s devices are used, including mobile phones, tablets, and laptops. You can also configure specific policies to control applications.

As mentioned above, Intune is part of Microsoft's [Enterprise Mobility + Security (EMS) suite](https://www.microsoft.com/microsoft-365/enterprise-mobility-security). Intune integrates with Azure Active Directory (Azure AD) to control who has access, and what they can access. It also integrates with Azure Information Protection for data protection. In addition, Intune can be used with the Microsoft 365 suite of products.

You can access Intune using the Microsoft Endpoint Manager admin center. If you are unable to access Intune using the step below, confirm that you have an Intune license (see above).

If you are uncertain whether you have a Microsoft Intune license, you can confirm access using the following steps:

1. Sign in to the [**Azure AD admin center**](https://aad.portal.azure.com).

    > [!NOTE]
    > To access and manage licenses, the admin account must be a license administrator, user administrator, or global administrator. 

2. Select **Azure Active Directory** > **Licenses** > **All products** to see all licensable products that you have available for your organization.

For additional information about Microsoft Intune, see [Set up Microsoft Intune](/learn/modules/set-up-microsoft-intune).

### Enable Windows 10 or Windows 11 automatic enrollment

Windows 10/11 automatic enrollment, which is also required for co-management, lets users enroll their Windows 10/11 devices in Intune. To enroll, users add their work account to their personally owned devices or join corporate-owned devices to Azure Active Directory. In the background, the device registers and joins Azure Active Directory. Once registered, the device is managed with Intune.

For more information, see [Enable Windows 10 automatic enrollment](/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment).

## Windows 10 or Windows 11

To enable co-management, end users must upgrade their devices to a supported version of Windows 10 or Windows 11. For more information, see [Adopting Windows as a service](/windows/deployment/update/waas-overview).

## Permissions and roles

To enable co-management in Configuration Manager, the administrator must be assigned the Full Administrator role. For more information about Configuration Manager roles, see [Fundamentals of role-based administration](/mem/configmgr/core/understand/fundamentals-of-role-based-administration).
