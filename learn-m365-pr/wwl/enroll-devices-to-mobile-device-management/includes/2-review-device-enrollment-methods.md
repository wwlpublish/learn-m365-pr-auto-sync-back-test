This module examines the following methods of enrolling devices for Mobile Device Management (MDM):

 -  Azure AD joined
 -  Azure AD joined with Autopilot
 -  Bulk enrollment
 -  Device enrollment manager (DEM)
 -  Bring your own device (BYOD)
 -  Group policy objects (GPO)
 -  Co-management

Azure AD Join can be deployed by using any of the following methods:

 -  Windows Autopilot
 -  Bulk deployment
 -  Self-service experience

Later units in this module focus solely on Azure AD joined, hybrid Azure AD joined, and BYOD devices. However, this unit introduces you to the other enrollment methods.

### Windows Autopilot

Windows Autopilot is a collection of technologies used to set up and pre-configure new devices, getting them ready for productive use. Windows Autopilot can be used to deploy Windows PCs. You can also use Windows Autopilot to reset, repurpose, and recover devices. This solution enables an IT department to updates devices with little to no infrastructure to manage, and with a process that's easy to perform.

Windows Autopilot simplifies the Windows device lifecycle, for both IT and end users, from initial deployment to end of life. Using cloud-based services, Windows Autopilot:

 -  reduces the time IT spends on deploying, managing, and retiring devices.
 -  reduces the infrastructure required to maintain the devices.
 -  maximizes ease of use for all types of end users.

When Windows Autopilot initially deploys new Windows devices, it uses the OEM-optimized version of Windows client. This version is preinstalled on the device. As such, organizations don't have to maintain custom images and drivers for every device model. Instead of reimaging the device, an organization's existing Windows installation can be transformed into a "business-ready" state that can:

 -  Apply settings and policies.
 -  Install apps.
 -  Change the edition of Windows being used to support advanced features. For example, from Windows Pro to Windows Enterprise.

Once Windows devices are deployed, organizations can manage them with:

 -  Microsoft Intune
 -  Windows Update for Business
 -  Microsoft Endpoint Configuration Manager
 -  Other similar tools

### Bulk deployment

Bulk deployment is restricted to Windows 10 and 11 devices. Organizations can join large numbers of new Windows devices to Azure Active Directory and Intune. For an organization to bulk enroll devices for its Azure AD tenant, it must create a provisioning package with the Windows Configuration Designer (WCD) app. When an organization applies the provisioning package to corporate-owned devices, it joins the devices to its Azure AD tenant and enrolls them for Intune management. Once the package is applied, it's ready for the company's Azure AD users to sign in.

> [!NOTE]
> Creating a provisioning package doesn't require any administrator roles in your Azure AD tenant. However, the user account that retrieves the token must [be allowed to join devices to Azure AD](/azure/active-directory/devices/device-management-azure-portal#configure-device-settings?azure-portal=true).

Azure AD users are standard users on these devices. They receive assigned Intune policies and required apps. Windows devices that are enrolled into Intune using Windows bulk enrollment can use the Company Portal app to install available apps.

An organization must complete the following steps to provision devices for bulk deployment:

1.  Access the provisioning package in the location specified in Project folder specified in the app.
2.  Choose how it's going to apply the provisioning package to the device. A provisioning package can be applied to a device in one of the following ways:
     -  Place the provisioning package on a USB drive, insert the USB drive into the device you'd like to bulk enroll, and apply it during initial setup.
     -  Place the provisioning package on a network folder, and apply it after initial setup.For step-by-step instruction on applying a provisioning package, see [Apply a provisioning package](/windows/configuration/provisioning-packages/provisioning-apply-package?azure-portal=true).
3.  After the package is applied, the device will automatically restart in one minute.
4.  When the device restarts, it connects to the Azure Active Directory and enrolls in Microsoft Intune.

### Device enrollment manager

A device enrollment manager (DEM) is a non-administrator user who can enroll devices in Intune. Device enrollment managers are useful to have when an organization must enroll and prepare many devices for distribution.

> [!IMPORTANT]
> People signed in to a DEM account can enroll and manage up to 1,000 devices. A standard non-admin account can only enroll 15 devices.

A DEM account requires an Intune user or device license, and an associated Azure AD user. Global Administrators and Intune Service Administrators can add and manage device enrollment managers in the Microsoft Endpoint Manager admin center.

A device enrollment manager can use the following methods to enroll devices in Intune:

 -  Windows Autopilot
 -  Bulk enrollment
 -  DEM-initiated through Company Portal enrollment
 -  DEM-initiated through Azure AD-join

An organization should complete the following steps to add a device enrollment manager:

1.  Sign in to the Microsoft Endpoint Manager admin center.
2.  Select **Devices** &gt; **Enroll devices**.
3.  Select **Device enrollment managers**.
4.  Select **Add**.
5.  In the **User name** field, enter the user principal name of the user you're adding.
6.  Select **Add**. The new device enrollment manager is added to the list of DEM users.

To remove someone as a device enrollment manager, select their name in the list and then select **Delete**.

The DEM account can't be used with all features in Microsoft Intune. It also has some limitations when used with others MDM solutions. Organizations may encounter the following limitations while setting up devices from a DEM account:

 -  **Android Enterprise**. You can enroll up to 10 personally owned devices with work profiles. The following types of Android Enterprise devices can't be set up through DEM:
     -  Corporate-owned with a work profile
     -  Fully managed
 -  **Apple Automated Device Enrollment**. DEM isn't compatible with Apple Automated Device Enrollment.
 -  **Apple volume purchased apps**. DEM-enrolled devices can install VPP apps if they have Apple VPP device licenses. Organizations can't use apps purchased through Apple VPP with Apple VPP user licenses, because of per-user Apple ID requirements for app management.
 -  **Azure AD**. Applying an Azure AD device restriction to a DEM account will prevent organizations from reaching the 1,000 device limit the DEM account can enroll.
 -  **Conditional access**. Conditional access is only supported with DEM on devices running:
     -  Windows 10, version 1803 and later
     -  Windows 11

DEM enrolls Windows 10/11 devices in shared device mode. As such, device limit restrictions won't work on them. Instead, a hard limit can be configured for these devices in the Azure AD admin center. For more information, see [Manage device identities by using the Azure portal](/azure/active-directory/devices/device-management-azure-portal#configure-device-settings?azure-portal=true).

### Group policy objects

Starting with Windows 10, version 1709, organizations can use Group policy objects (GPO) to trigger auto-enrollment to Mobile Device Management (MDM) for Active Directory (AD) domain-joined devices.

The enrollment into Intune is triggered by a group policy created on an organization's local AD. Enrollment happens without any user interaction. This cause-and-effect mechanism enables organizations to automatically mass-enroll a large number of domain-joined corporate devices into Microsoft Intune. The enrollment process starts in the background once a user signs in to their device with their Azure AD account.

Organizations must satisfy the following requirements to use GPO to trigger auto-enrollment to MDM for AD domain-joined devices:

 -  Active Directory-joined devices running Windows 10 (version 1709 or later) or 11.
 -  The enterprise has configured a mobile device management (MDM) service.
 -  The on-premises Active Directory must be [integrated with Azure AD (through Azure AD Connect)](/azure/architecture/reference-architectures/identity/azure-ad?azure-portal=true).
 -  Devices can't be enrolled in Intune using the classic agents (devices managed using agents will fail enrollment with error 0x80180026).
 -  The minimum Windows Server version requirement is based on the Hybrid Azure AD joined requirement. For more information, see [How to plan your hybrid Azure Active Directory join implementation](/azure/active-directory/devices/hybrid-azuread-join-plan?azure-portal=true).

**Additional reading**. For more information, see:

 -  [How to configure automatic registration of Windows domain-joined devices with Azure Active Directory](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup?azure-portal=true).
 -  [How to plan your hybrid Azure Active Directory join implementation](/azure/active-directory/devices/hybrid-azuread-join-plan?azure-portal=true).
 -  [Azure Active Directory integration with MDM](/windows/client-management/mdm/azure-active-directory-integration-with-mdm?azure-portal=true).

Auto-enrollment relies on the presence of an MDM service and the Azure Active Directory registration for the PC. Starting in Windows 10, version 1607, once the enterprise has registered its AD with Azure AD, a Windows PC that is domain joined is automatically Azure AD–registered.

When the auto-enrollment Group Policy is enabled, a task is created in the background that initiates the MDM enrollment. The task will use the existing MDM service configuration from the Azure Active Directory information of the user. If multi-factor authentication is required, the user will receive a prompt to complete the authentication. Once the enrollment is configured, the user can check the status in the Settings page.

In Windows 10, version 1709 or later, when the same policy is configured in Group Policy and MDM, Group Policy policy takes precedence over MDM. Since Windows 10, version 1803, a new setting allows organizations to change precedence to MDM. For more information, see [Windows 10 Group Policy vs. Intune MDM Policy - who wins?](/archive/blogs/cbernier/windows-10-group-policy-vs-intune-mdm-policy-who-wins?azure-portal=true)

For this policy to work, an organization must verify the MDM service provider allows Group Policy initiated MDM enrollment for domain-joined devices.

### Co-management

Co-management is one of the primary ways for an organization to attach its existing Configuration Manager deployment to the Microsoft 365 cloud. It helps organizations unlock more cloud-powered capabilities like conditional access.

Co-management enables organizations to concurrently manage Windows 10 or later devices by using both Configuration Manager and Microsoft Intune. It lets them cloud-attach their existing investment in Configuration Manager by adding new functionality. By using co-management, organizations have the flexibility to use the technology solution that works best for them.

When a Windows device has the Configuration Manager client and is enrolled to Intune, its organization gets the benefit of both services. It controls which workloads, if any, it can switch the authority from Configuration Manager to Intune. Configuration Manager continues to manage all other workloads, including those workloads the organization doesn't switch to Intune, and all other features of Configuration Manager that co-management doesn't support.

Organizations are also able to pilot a workload with a separate collection of devices. Piloting allows an organization to test the Intune functionality with a subset of devices before switching a larger group.

When an organization concurrently manages devices with both Configuration Manager and Microsoft Intune, this configuration is called co-management. When it manages devices with Configuration Manager and enrolls to a third-party MDM service, this configuration is called coexistence. Having two management authorities for a single device can be challenging if not properly orchestrated between the two. With co-management, Configuration Manager and Intune balance the workloads to ensure there are no conflicts. This interaction doesn't exist with third-party services. As such, there are limitations with coexistence management capabilities. For more information, see [Third-party MDM coexistence with Configuration Manager](/mem/configmgr/comanage/coexistence?azure-portal=true).

There are two main paths to reach co-management:

 -  **Existing Configuration Manager clients**. An organization has Windows 10 or later devices that are already Configuration Manager clients. The organization sets up hybrid Azure AD, and enrolls them into Intune.
 -  **New internet-based devices**. An organization has new Windows 10 or later devices that join Azure AD and automatically enroll to Intune. The organization installs the Configuration Manager client to reach a co-management state.

**Additional reading**. For more information on the paths, see [Paths to co-management](/mem/configmgr/comanage/quickstart-paths?azure-portal=true).

When an organization enrolls existing Configuration Manager clients in co-management, it gains the following immediate value:

 -  Conditional access with device compliance.
 -  Intune-based remote actions, for example: restart, remote control, or factory reset.
 -  Centralized visibility of device health.
 -  Link users, devices, and apps with Azure Active Directory (Azure AD).
 -  Modern provisioning with Windows Autopilot.
 -  Remote actions.
