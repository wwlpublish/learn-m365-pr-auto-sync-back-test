Organizations with existing Active Directory implementations can benefit from some of the functionality provided by Azure Active Directory (Azure AD) by implementing hybrid Azure AD joined devices. These devices are joined to an organization's on-premises Active Directory and registered with Azure Active Directory.

Hybrid Azure AD joined devices require periodic network line of sight to an organization's on-premises domain controllers. Without this connection, devices become unusable. If this requirement is a concern, organizations should consider [Azure AD joining](/azure/active-directory/devices/concept-azure-ad-join?azure-portal=true) their devices.

Bringing devices to Azure AD maximizes user productivity through single sign-on (SSO) across an organization's cloud and on-premises resources. An organization can secure access to its resources with [Conditional Access](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device) at the same time.

The following table summarizes the features of hybrid Azure AD joined devices.

| **Hybrid Azure AD Join** | **Description**                                                                                                                                                                                                                                                                                                                                      |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Definition               | Joined to on-premises AD and Azure AD requiring organizational account to sign in to the device.                                                                                                                                                                                                                                                     |
| Primary audience         | - Suitable for hybrid organizations with existing on-premises AD infrastructure.<br>\- Applicable to all users in an organization.                                                                                                                                                                                                                   |
| Device ownership         | Organization                                                                                                                                                                                                                                                                                                                                         |
| Operating Systems        | - Windows 10 or newer, 8.1 and 7<br>\- Windows Server 2008/R2, 2012/R2, 2016 and 2019                                                                                                                                                                                                                                                                |
| Provisioning             | - Windows 10 or newer, Windows Server 2016/2019<br>\- Domain joined by IT and autojoined through Azure AD Connect or ADFS config<br>\- Domain joined by Windows Autopilot and autojoined through Azure AD Connect or ADFS config<br>\- Windows 8.1, Windows 7, Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 - Require MSI |
| Device sign in options   | Organizational accounts using:<br>\- Password<br>\- Windows Hello for Business for Win10 and above                                                                                                                                                                                                                                                   |
| Device management        | - Group Policy<br>\- Configuration Manager standalone or co-management with Microsoft Intune                                                                                                                                                                                                                                                         |
| Key capabilities         | - Single Sign On (SSO) to both cloud and on-premises resources.<br>\- Conditional Access through Domain join or through Intune if co-managed.<br>\- [Self-service Password Reset and Windows Hello PIN reset on lock screen](/azure/active-directory/authentication/howto-sspr-windows?azure-portal=true).                 |

:::image type="content" source="../media/azure-ad-hybrid-joined-device-46a3b7c5.png" alt-text="Diagram showing hybrid Azure A D joined company-owned laptops and Azure A D interacting with A D D S.":::


### Scenarios

Hybrid Azure AD join can be used in various scenarios, such as when an organization:

 -  Supports down-level devices running Windows 7 and 8.1.
 -  Wants to continue using Group Policy to manage device configuration.
 -  Wants to continue using existing imaging solutions to deploy and configure devices.
 -  Has Win32 apps deployed to devices that rely on Active Directory machine authentication.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”