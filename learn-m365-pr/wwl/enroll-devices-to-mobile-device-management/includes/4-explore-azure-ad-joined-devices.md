Any organization can deploy Azure AD joined devices no matter the size or industry. Azure AD join works even in hybrid environments, enabling access to both cloud and on-premises apps and resources. The following table summarizes the features of Azure AD joined devices.

| **Azure AD Join**      | **Description**                                                                                                                                                                                                                                                                                                                    |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Definition             | Joined only to Azure AD requiring organizational account to sign in to the device.                                                                                                                                                                                                                                                 |
| Primary audience       | - Suitable for both cloud-only and hybrid organizations.<br>\- Applicable to all users in an organization.                                                                                                                                                                                                                         |
| Device ownership       | Organization                                                                                                                                                                                                                                                                                                                       |
| Operating Systems      | - All Windows 10 and 11 devices, except Home editions.<br>\- [Windows Server 2019 Virtual Machines running in Azure](/azure/active-directory/devices/howto-vm-sign-in-azure-ad-windows?azure-portal=true) (Server core isn't supported).                                                                 |
| Provisioning           | - Self-service: Windows Out of Box Experience (OOBE) or Settings<br>\- Bulk enrollment<br>\- Windows Autopilot                                                                                                                                                                                                                     |
| Device sign-in options | Organizational accounts using:<br>\- Password<br>\- Windows Hello for Business<br>\- FIDO2.0 security keys (preview)                                                                                                                                                                                                               |
| Device management      | - Mobile Device Management (example: Microsoft Intune)<br>\- [Configuration Manager standalone or co-management with Microsoft Intune](/mem/configmgr/comanage/overview?azure-portal=true)                                                                                                               |
| Key capabilities       | - Single Sign On (SSO) to both cloud and on-premises resources<br>\- Conditional Access through MDM enrollment and MDM compliance evaluation<br>\- [Self-service Password Reset and Windows Hello PIN reset on lock screen](/azure/active-directory/authentication/howto-sspr-windows?azure-portal=true) |

Users can sign-in to Azure AD joined devices using an organizational Azure AD account. Access to resources can be controlled based on Azure AD account policies and [Conditional Access policies](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device?azure-portal=true) applied to the device.

Administrators can secure and further control Azure AD joined devices using either:

 -  Mobile Device Management (MDM) tools like Microsoft Intune.
 -  Co-management scenarios using Microsoft Endpoint Configuration Manager.

These tools provide a means to enforce organization-required configurations, such as:

 -  Requiring storage to be encrypted.
 -  Password complexity.
 -  Software installation.
 -  Software updates.

Azure AD join can be accomplished using self-service options like the Out of Box Experience (OOBE), bulk enrollment, or Windows Autopilot. Azure AD joined devices can still maintain single sign-on access to on-premises resources when they're on the organization's network. Devices that are Azure AD joined can still authenticate to on-premises servers such file servers, print servers, and other application servers.

### Scenarios

Azure AD join can be used in various scenarios, such as when an organization:

 -  Wants to transition to a cloud-based infrastructure using Azure AD and a Mobile Device Management solution such as Intune.
 -  Can’t use an on-premises domain join. For example, the organization needs to get mobile devices such as tablets and phones under control.
 -  Has users who must access Microsoft 365 or other SaaS apps integrated with Azure AD.
 -  Wants to manage a specific group of users in Azure AD instead of its on-premises Active Directory. This scenario can apply, for example, to seasonal workers, contractors, or students.
 -  Wants to provide joining capabilities to workers who work from home or are in remote branch offices with limited on-premises infrastructure.

An organization can configure Azure AD join for all Windows 10 and 11 devices, except for Home editions.

The goal of Azure AD joined devices is to simplify:

 -  Windows deployments of work-owned devices.
 -  Access to organizational apps and resources from any Windows device.
 -  Cloud-based management of work-owned devices.
 -  User sign-in to their devices with their Azure AD or synced Active Directory work or school accounts.

:::image type="content" source="../media/azure-ad-joined-device-f78c5b7e.png" alt-text="Diagram showing Azure A D joined company-owned laptops and Azure A D interacting with A D D S.":::


Azure AD Join can be deployed by using any of the following methods:

 -  [Windows Autopilot](/windows/deployment/windows-autopilot/windows-10-autopilot?azure-portal=true)
 -  [Bulk deployment](/intune/windows-bulk-enroll?azure-portal=true)
 -  [Self-service experience](/azure/active-directory/devices/azuread-joined-devices-frx?azure-portal=true)
