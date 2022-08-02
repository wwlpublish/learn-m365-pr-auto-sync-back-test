Many devices being used today, such as Android, iOS, and Windows 10 S, can't be joined to on-premises AD DS. But to manage devices centrally, they must trust the authority that defines configuration settings. In on-premises AD DS environments, such authorities were domain controllers. In today’s cloud world, they're MDM authorities. You can manage a device only if it's enrolled to MDM. An enrolled device means that it trusts the MDM authority, such as Intune or Basic Mobility and Security.

In this module, you'll examine the benefits of enrolling devices to MDM, how to enroll Windows 10, Android, and iOS devices, and how to create enrollment rules. You can't require that users enroll their devices to MDM, but you can require that users only access company resources from enrolled devices. Because users access company resources, they must first enroll their devices to access those resources. This module shows you how to configure a security policy with such a requirement, while using a conditional access policy in Intune to achieve the same goal and more.

In this module, you'll be introduced to the various methods of enrolling devices. You'll examine the basic features of enrolling devices using:

 -  Azure AD joined
 -  Azure AD joined with Autopilot
 -  Bulk enrollment
 -  Device enrollment manager (DEM)
 -  Bring your own device (BYOD)
 -  Group policy objects (GPO)
 -  Co-management

The module examines how Azure AD registered devices provide an organization's users with support for Bring Your Own Device (BYOD) and mobile device scenarios. You'll then learn how Azure AD joined devices simplifies Windows deployments of work-owned devices. The module then examines how organizations with existing Active Directory implementations can benefit from some of the functionality provided by Azure Active Directory (Azure AD) by implementing hybrid Azure AD joined devices. These devices are joined to an organization's on-premises Active Directory and registered with Azure Active Directory.

The module concludes by examining how to set up enrollment for Windows devices. You'll learn how to enable Windows for automatic enrollment, which lets users enroll their Windows devices in Intune. You'll also learn how organizations can simplify enrollment by creating a domain name server (DNS) alias (CNAME record type) that redirects enrollment requests to Intune servers.

After completing this module, you'll be able to:

 -  Enroll devices to mobile device management in Microsoft Intune.
 -  Explore the use of Azure AD joined and hybrid Azure AD joined devices.
 -  Explain how users can enroll their personal devices.
 -  Describe best practices and capabilities for each device enrollment method.
 -  Set up enrollment for Windows devices.
