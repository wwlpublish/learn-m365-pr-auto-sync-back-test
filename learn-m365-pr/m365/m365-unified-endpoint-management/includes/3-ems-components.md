Enterprise Mobility and Security is a suite of products that you get in your Microsoft 365 Enterprise subscription.

**Azure AD Premium** is the central identity store that you use for all the applications in EMS and Microsoft 365. Azure AD Premium is available with three different levels of capabilities, Basic, P1, or P2. Levels P1 and P2 provide features that are important for unified endpoint management. Some of the additional features included with the P1 and P2 plans are:
- Self-service password reset
- Write-back from Azure AD to on-premises AD DS
- Microsoft Azure Multi-Factor Authentication (MFA) for cloud and on-premises apps
- Conditional access based on group, location, and device state
- Conditional access based on sign-in or user risk (P2 plan only)

**Intune** enables you to manage mobile devices and apps. Using Intune, you can enforce security policies, wipe devices remotely, and deploy apps.  Intune supports devices running the following operating systems through device enrollment:
- Apple iOS 9.0 and later
- Mac OS X 10.9 and later
- Android 4.4 and later, including Android for Work and Samsung Knox 
- Windows Phone 8.1, Windows RT 8.1, and Windows 8.1 (sustaining mode)
- Windows 10 and Windows 10 Mobile
- Windows 10 IoT Enterprise and Windows 10 IoT Mobile Enterprise

After you have enrolled devices, you can use Intune device profiles to manage various aspects of your devices’ configuration. The following table shows the most common device profiles for Windows 10.

|Profile|	Description|
|-|-|
|Email|	Manages Exchange ActiveSync settings on devices.|
|Wi-Fi|	Allows you to manage wireless network settings for users and devices. In Windows 10, managing settings for users allows them to connect to corporate Wi-Fi without having to configure the connection manually. Instead, they can import a configuration that was previously exported from another device.|
|VPN|	Configures VPN settings for devices.|
|Education|	Configures options for the Take a Test app in Windows 10.|
|Certificates|	Allows you to configure trust and other certificates used for Wi-Fi, VPN, and email profiles.|
|Edition upgrade|	Allows you to permit users to upgrade some versions of Windows 10.|
|Endpoint protection|	Configures settings for BitLocker and Windows Defender.|
|Windows Information Protection|	Allows you to configure Windows Information Protection for data loss prevention.|

**System Center Configuration Manager (Configuration Manager)** allows you to manage PCs, servers, and mobile devices like iPhones and Android devices with on-premises and cloud-based infrastructure.

**Azure Information Protection** encrypts documents and enforces policies on their use. Document data is more protected because only authorized users can access the contents. 

**Microsoft Advanced Threat Analytics** can: 
- Detect suspicious activities and malicious attacks.
- Adapt to the changing nature of cyber-security threats.
- Provide focus and clarity around what is important with a simple attack timeline.
- Reduce false positives.

**Cloud App Security** uses data collected from your firewalls and proxy servers to identify cloud application usage. This can help identify unauthorized applications that might be a threat to your data. Additionally, it can identify unusual usage patterns that might indicate a problem. 

**Microsoft Identity Manager 2016** binds Microsoft's identity and access management solutions together by seamlessly bridging multiple on-premises authentication stores like Active Directory, LDAP, Oracle, and other applications with Azure Active Directory. This provides consistent experiences to on-premises LOB applications and SaaS solutions.
Azure Advanced Threat Protection- Azure Advanced Threat Protection (ATP) is a cloud service that helps protect your enterprise hybrid environments from multiple types of advanced targeted cyber-attacks and insider threats.

EMS is provided as part of Microsoft 365 E3 and E5 plans, as summarized in the table below. 

|Product|E3 plan|	E5 plan|
|-|-|-|
|Azure AD Premium|	P1 plan|	P2 plan|
|Intune|Yes|	Yes|
|Azure Information Protection|	P1 plan|	P2 plan|
|Microsoft Advanced Threat Analytics|	Yes|	Yes|
|Cloud App Security|	No|	Yes|
|System Center Configuration Manager|	Yes|	Yes|
