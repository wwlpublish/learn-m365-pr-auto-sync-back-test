One of the tools you can use to manage all of the devices in your organization is Enterprise Mobility + Security (EMS), an intelligent mobility management and security platform that helps protect and secure your organization and empowers your employees to work in new and flexible ways. EMS is a suite of products included in your Microsoft 365 Enterprise subscription. Learn how these products help manage devices in your organization.

EMS is provided as part of Microsoft 365 E3 and E5 plans, as summarized in the table below. 

|Product|E3 plan|	E5 plan|
|-|-|-|
|Azure AD Premium|	P1 plan|	P2 plan|
|Intune|Yes|	Yes|
|Azure Information Protection|	P1 plan|	P2 plan|
|Microsoft Advanced Threat Analytics|	Yes|	Yes|
|Cloud App Security|	No|	Yes|
|Configuration Manager|	Yes|	Yes|

**Azure AD Premium** is the central identity store used for all the applications in EMS and Microsoft 365. Azure AD Premium is available with three different levels of capabilities: Basic, P1, or P2. P1 and P2 include features that are important for unified endpoint management. Some of the additional features included with the P1 and P2 plans are:

- Self-service password reset
- Write-back from Azure AD to on-premises Active Directory Domain Services (meaning your cloud and on-premises data is linked)
- Microsoft Azure Multi-Factor Authentication (MFA) for cloud and on-premises apps
- Conditional access based on group, location, and device state
- Conditional access based on sign-in or user risk (P2 plan only)

**Intune** is a cloud-based enterprise mobility management (EMM) service that enables user productivity while keeping your corporate data protected. Intune integrates with Azure Active Directory for identity and access control, and Azure Information Protection for data protection. Intune can enforce security policies, wipe devices remotely, and deploy apps. 

Use Intune to manage apps and mobile devices by “enrolling” devices. When you enroll, you can use profiles to manage different settings and features on devices. The following table shows the most common device profiles for Windows 10.

|Profile|	Description|
|-|-|
|Email|	Manages Exchange ActiveSync settings on devices.|
|Wi-Fi|	Allows you to manage wireless network settings for users and devices. In Windows 10, managing settings for users allows them to connect to corporate Wi-Fi without having to configure the connection manually. |
|VPN|	Adds a virtual private network (VPN) with your organizational settings so your users' devices get network access quickly and easily.|
|Education|Configures different options for the Take a Test app on Windows 10 devices in classroom environments.|
|Certificates|	Allows you to configure trust and certificates used for Wi-Fi, VPN, email profiles, and more.|
|Edition upgrade|	Upgrades Windows 10 devices to Windows 10 Enterprise, S mode, and more.|
|Endpoint protection|	Configures settings for BitLocker and Windows Defender.|
|Windows Information Protection|	Allows you to configure Windows Information Protection for data loss prevention.|

**System Center Configuration Manager** is an on-premises product used to manage Windows, macOS PCs, and servers. Configuration Manager has a rich set of capabilities that allow you to highly customize the following areas:

- Application management 
- OS deployment 
- Software update management 
- Device compliance

**Azure Information Protection** encrypts documents and enforces policies on how they can be used. Document data is more protected because only authorized users can access the contents. 

**Microsoft Advanced Threat Analytics** can: 
- Detect suspicious activities and malicious attacks.
- Adapt to the changing nature of cyber-security threats.
- Provide focus and clarity around what is important with a simple attack timeline.
- Reduce false positives.

**Cloud App Security** uses data collected from your firewalls and proxy servers to identify cloud application usage. This can help identify unauthorized applications that might be a threat to your data. Additionally, it can identify unusual usage patterns that might indicate a problem. 

**Microsoft Identity Manager 2016** binds Microsoft's identity and access management solutions together by seamlessly bridging multiple on-premises authentication stores like Active Directory, LDAP, Oracle, and other applications with Azure Active Directory. This provides consistent identity experiences for both on-premises business applications and SaaS solutions.

**Azure Advanced Threat Protection** (ATP) is a cloud-based solution to identify, detect, and investigate threats, compromises, and malicious actions. ATP helps you: 
- Detect and investigate advanced attacks on-premises and in the cloud.
- Identify suspicious user and device activity with both known-technique detection and behavioral analytics.
- Analyze threat intelligence from the cloud and on-premises.
- Protect user identities and credentials stored in Active Directory.
- View clear attack information on a simple timeline for fast triage.
- Monitor multiple entry points through integration with Windows Defender Advanced Threat Protection.

