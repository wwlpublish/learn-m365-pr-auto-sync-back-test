Many devices being used today, such as Android, iOS, and Windows 10 S, can't be joined to on-premises AD DS. But to manage devices centrally, they must trust the authority that defines configuration settings. In on-premises AD DS environments, such authorities were domain controllers. In today’s cloud world, they're MDM authorities. You can manage a device only if it's enrolled to MDM. An enrolled device means that it trusts the MDM authority, such as Intune or Basic Mobility and Security.

In this module, you'll examine the benefits of enrolling devices to MDM, how to enroll Windows 10, Android, and iOS devices, and how to create enrollment rules. And since Apple devices have their own enrollment mechanism, you'll be introduced to enrolling Apple devices using the Apple Device Enrollment Program (DEP).

You can't require that users enroll their devices to MDM, but you can require that users only access company resources from enrolled devices. Because users access company resources, they must first enroll their devices to access those resources. This module shows you how to configure a security policy with such a requirement, while using a conditional access policy in Intune to achieve the same goal and more.

In this module, you'll also learn how to manage the enrollment of devices. While users can enroll up to five devices to MDM by themselves, some companies want to provide employees with devices that are already enrolled. Intune addresses this need by employing device enrollment managers (DEM). This module introduces you to device enrollment managers, who can each enroll up to 1000 devices.

Finally, if your environment requires stronger security, you can configure Azure AD to require multifactor authentication (MFA) for users who are enrolling devices to MDM. This module examines how to implement MFA so that users have to prove their identity with another authentication factor before they can enroll their devices.

After completing this module, you'll be able to:

 -  Enroll Windows 10 and Android devices to MDM.
 -  Enroll iOS devices to MDM using the Apple Device Enrollment Program.
 -  Describe the use of enrollment rules to regulate device enrollment.
 -  Explain how users can enroll their personal devices.
 -  Explain the permissions assigned to the Device Enrollment Manager role.
 -  Explain why MFA helps secure the sign-in to Microsoft 365 or Intune for mobile device enrollment.
