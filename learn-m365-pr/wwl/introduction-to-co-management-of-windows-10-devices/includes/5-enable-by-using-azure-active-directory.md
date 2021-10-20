The landscape of devices from which users can sign in to corporate networks is expanding. Organizations may provide desktops, laptops, phones, tablets, and other devices. Your users may bring their own array of devices, and access information from varied locations. In this environment, your job as an administrator is to keep your organizational resources secure across all devices.

Azure AD enables your organization to meet these goals with device identity management. You can now get your devices in Azure AD and control them from a central location in the Azure portal. This design provides a unified experience, enhanced security, and reduces the time needed to configure a new device.

### Co-managing devices using Azure AD

Organizations that want to enable co-management must be using Azure AD. Organizations that are already using Microsoft 365 or Intune are already using Azure AD, although they may not be aware of it. Azure AD is a standalone cloud identity and access control solution. However, most companies integrate it with their on-premises AD DS. By doing so, the same users (called identities) can access on-premises and cloud resources.

Azure Active Directory (Azure AD) is Microsoft’s cloud-based identity and access management service. It helps an organization's employees sign in and access resources in:

 -  External resources, such as Microsoft 365, the Azure portal, and thousands of other SaaS applications.
 -  Internal resources, such as apps on your corporate network and intranet, along with any cloud apps developed by your own organization.

Azure AD combines core directory services, application access management, and identity protection into a single solution. It also offers a rich, standards-based platform. This platform enables developers to deliver access control to their applications, based on centralized policy and rules.

:::image type="content" source="../media/azure-ad-network-configuration-ecf7702e.jpg" alt-text="network configuration diagram showing Azure AD in relationship with on-premises and the cloud":::


The key benefits of giving your devices an Azure AD identity include:<br>

 -  **Increase productivity.** With Azure AD, users can do [seamless sign-on (SSO)](/azure/active-directory/devices/azuread-join-sso) to their organizations' on-premises and cloud resources, which enable them to be productive wherever they are.
 -  **Increase security.** Azure AD devices enable you to apply [Conditional Access policies](/azure/active-directory/conditional-access/require-managed-devices) to resources based on the identity of the device or user. Conditional Access policies can offer extra protection using [Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection). Joining a device to Azure AD is a prerequisite for increasing your security with a [Passwordless Authentication](/azure/active-directory/authentication/concept-authentication-passwordless) strategy.
 -  **Improve user experience.** With device identities in Azure AD, you can provide your users with easy access to your organization’s cloud-based resources from both personal and corporate devices. Administrators can enable [Enterprise State Roaming](/azure/active-directory/devices/enterprise-state-roaming-overview) for a unified experience across all Windows devices.
 -  **Simplify deployment and management.** Device identity management simplifies the process of bringing devices to Azure AD with [Windows Autopilot](/windows/deployment/windows-autopilot/windows-10-autopilot), [bulk provisioning](/mem/intune/enrollment/windows-bulk-enroll), and [self-service: Out of Box Experience (OOBE)](/azure/active-directory/user-help/user-help-join-device-on-network). You can manage these devices with Mobile Device Management (MDM) tools like Microsoft Intune, and their identities in Azure portal.

Azure AD is intended for:

 -  **IT administrators.** IT administrators can use Azure AD to control access to your apps and your app resources, based on your business requirements. For example, you can use Azure AD to require multi-factor authentication when accessing important organizational resources. You can also use Azure AD to automate user provisioning between your existing Windows Server AD and your cloud apps, including Microsoft 365. Finally, Azure AD provides powerful tools to automatically help protect user identities and credentials and to meet your access governance requirements. By using Azure AD, organizations can easily implement features such as:
    
     -  Multi-factor authentication (MFA)
     -  Self-service password reset
     -  Device registration
     -  Conditional Access
 -  **App developers.** App developers can use Azure AD as a standards-based approach for adding single sign-on (SSO) to their apps, allowing them to work with a user's pre-existing credentials. Azure AD also provides APIs that can help you build personalized app experiences using existing organizational data.
 -  **Microsoft 365, Azure, or Dynamics CRM Online subscribers.** Subscribers are already using Azure AD. Each Microsoft 365, Azure, and Dynamics CRM Online tenant is actually an Azure AD tenant. This design enables organizations to immediately begin managing employee-access to their integrated cloud apps.

**Additional reading.** For more information, see [Azure AD and how to connect it to on-premises AD DS](/azure/active-directory/fundamentals/identity-fundamentals).

### Azure AD licenses

Microsoft Online business services, such as Microsoft 365 or Microsoft Azure, require Azure AD for sign in and to help with identity protection. If you subscribe to any Microsoft Online business service, you automatically get Azure AD with access to all the free features.

To enhance your Azure AD implementation, you can also add paid capabilities by upgrading to Azure Active Directory Premium P1 or Premium P2 licenses. Azure AD paid licenses are built on top of your existing free directory, providing self-service, enhanced monitoring, security reporting, and secure access for your mobile users.

Azure AD licenses include:<br>

 -  **Azure Active Directory Free.** Provides user and group management, on-premises directory synchronization, basic reports, self-service password change for cloud users, and single sign-on across Azure, Microsoft 365, and many popular SaaS apps.<br>
 -  **Azure Active Directory Premium P1.** In addition to the Free features, P1 also lets your hybrid users access both on-premises and cloud resources. It also supports advanced administration, such as dynamic groups, self-service group management, Microsoft Identity Manager (an on-premises identity and access management suite) and cloud write-back capabilities, which allow self-service password reset for your on-premises users.
 -  **Azure Active Directory Premium P2.** In addition to the Free and P1 features, P2 also offers Azure Active Directory Identity Protection. This service helps provide risk-based Conditional Access to your apps and critical company data. It also provides [Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-getting-started) to help discover, restrict, and monitor administrators and their access to resources and to provide just-in-time access when needed.
 -  **"Pay as you go" feature licenses.** You can also get other feature licenses, such as Azure Active Directory Business-to-Customer (B2C). B2C can help you provide identity and access management solutions for your customer-facing apps. For more information, see [Azure Active Directory B2C documentation](/azure/active-directory-b2c/).

**Additional reading.** For more information on the pricing options of these licenses, see [Azure Active Directory Pricing](https://azure.microsoft.com/pricing/details/active-directory/?azure-portal=true).
