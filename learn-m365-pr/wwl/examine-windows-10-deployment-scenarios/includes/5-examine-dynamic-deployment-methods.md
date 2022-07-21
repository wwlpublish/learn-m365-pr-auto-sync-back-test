For new PCs, organizations have historically replaced the version of Windows included on the device with their own custom Windows image. Why? Because doing so was often faster and easier than using the preinstalled version. However, this process is an added expense due to the time and effort required. With the new dynamic provisioning capabilities and tools provided with Windows 10 and later, it's now possible to avoid this situation.

The goal of dynamic provisioning is to take a new PC out of the box, turn it on, and transform it into a productive organization device, with minimal time and effort. The types of transformations that are available are outlined in the following sections.

### Windows 10 and later Subscription Activation

Windows 10 and 11 Pro supports the Subscription Activation feature. This feature enables users to "step-up" from:

 -  Windows 10 Pro to Windows 10 Enterprise.
 -  Windows 11 Pro to Windows 11 Enterprise.

To use Subscription Activation, organizations must be subscribed to Windows 10/11 Enterprise E3 or E5.

Organizations can also step up from:

 -  Windows 10, version 1903 and later Pro Education to Windows 10 Windows 10 Education (Enterprise grade edition).
 -  Windows 11 Pro Eduction to Windows 11 Education (Enterprise grade edition).

If you have devices that are licensed for Windows 7, 8, and 8.1 Professional, Microsoft 365 Business Premium provides an upgrade to Windows 10 Pro, which is the prerequisite for deploying [Windows 10/11 Business](/microsoft-365/business-premium/microsoft-365-business-faqs#what-is-windows-10-business?azure-portal=true).

The Subscription Activation feature eliminates the need to:

 -  Manually deploy Enterprise or Education edition images on each target device.
 -  Then later standing up on-premises key management services such as KMS or MAK based activation, entering Generic Volume License Keys (GVLKs).
 -  Rebooting client devices.

**Additional reading**. For more information about Subscription Activation, see [Windows 10/11 Subscription Activation](/windows/deployment/windows-10-enterprise-subscription-activation?azure-portal=true).

### Azure Active Directory join with automatic mobile device management (MDM) enrollment

In this scenario, the organization member just needs to provide their work or school user ID and password. The device can then be automatically joined to Azure Active Directory and enrolled in a mobile device management (MDM) solution with no other user interaction. Once done, the MDM solution can finish configuring the device as needed.

Company owned devices are traditionally joined to the on-premises Active Directory domain of the organization. These devices can be managed using Group Policy or computer management software such as Microsoft Endpoint Configuration Manager. In Windows 10 and later, it’s also possible to manage domain joined devices with an MDM.

Windows 10 introduced a new way to configure and deploy organization-owned Windows devices. This mechanism is called Azure AD Join. Like traditional domain join, Azure AD Join allows devices to become known and managed by an organization. However, with Azure AD Join, Windows authenticates to Azure AD instead of authenticating to a domain controller.

Azure AD Join also enables company owned devices to be automatically enrolled in, and managed by an MDM. Furthermore, Azure AD Join can be performed on a store-bought PC, in the out-of-box experience (OOBE), which helps organizations streamline their device deployment. An administrator can require that users belonging to one or more groups enroll their devices for management with an MDM. If a user is configured to require automatic enrollment during Azure AD Join, this enrollment becomes a mandatory step to configure Windows. If the MDM enrollment fails, then the device won't be joined to Azure AD.

Every user enabled for automatic MDM enrollment with Azure AD Join must be assigned a valid Azure Active Directory Premium license.

**Additional reading**. For more information, see [Azure Active Directory integration with MDM](/windows/client-management/mdm/azure-active-directory-integration-with-mdm?azure-portal=true).

### Provisioning package configuration

IT administrators can use the [Windows Imaging and Configuration Designer (ICD)](/windows/configuration/provisioning-packages/provisioning-install-icd?azure-portal=true) to create a self-contained package that contains all the configuration, settings, and apps that must be applied to a machine. These packages can then be deployed to new PCs through various means, typically by IT professionals.

These scenarios can be used to enable “choose your own device” (CYOD) programs where the organization’s users can pick their own PC and not be restricted to a small list of approved or certified models (programs that are difficult to implement using traditional deployment scenarios).

The Windows 10 and later releases include various provisioning settings and deployment mechanisms. They'll continue to be enhanced and extended based on feedback from organizations. As with all Windows features, organizations can submit suggestions for other features through the Windows Feedback app or through their Microsoft Support contacts.

**Additional reading**. For more information, see [Configure devices without MDM](/windows/configuration/configure-devices-without-mdm?azure-portal=true).

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”