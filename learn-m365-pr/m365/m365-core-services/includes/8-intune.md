Intune is a cloud service that helps you manage computers, laptops, tablets, and other mobile devices. This includes iOS, Android, and Mac OS X devices. It uses Azure Active Directory (Azure AD) as a directory store for identity, and it can integrate with local management infrastructures such as Microsoft System Center Configuration Manager (SCCM). Intune is especially useful for devices that are beyond the management scope of Group Policy, such as mobile phones, devices that are not AD DS domain members, or Windows 10 devices that are joined to Azure AD. 

By using Intune, you can:
- Allow staff to more safely access organizational data by using personal devices, which is commonly known as a Bring Your Own Device (BYOD) program.
- Manage company-owned phones.
- Control access to Microsoft Office 365 from unmanaged devices, such as public kiosks and mobile devices.
- Help to ensure that devices and apps that do connect to corporate data are compliant with security policies.

Intune is a component of EMS. Intune integrates with Azure AD and device operating-system features to provide a complete solution. For example, when a user attempts to access Office 365 data through a line of business app (LOB app) on a mobile phone, Office 365 checks with Azure AD to authenticate the user and verify whether that user can access the data from that app on that device. The results depend on: 
- Conditional access policies defined within Azure AD. 
- Whether Intune tells Azure AD that the device is compliant with device configuration and data protection policies.
- Whether the app on that device complies with app configuration and data protection policies. 

If the device and app are both compliant with all policies, Azure AD notifies Office 365 that the data can be accessed.