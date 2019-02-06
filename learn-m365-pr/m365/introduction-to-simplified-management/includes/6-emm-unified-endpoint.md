Unified Endpoint Management is an industry term that describes the notion of a platform that can provide overall device and app management from a single cons  ole. Microsoft’s Enterprise Mobility + Security (EM+S) provides enterprise mobility and unified endpoint management. 

The tools in EM+S help enhance management and security for mobile users. The following table describes some specific examples of how these tools work, and how to use them.

|Tool|	Usage|
|-|-|
|Enhanced authentication security|	Azure AD monitors user authentication for suspicious patterns, for credentials that are available on the black market, and for devices potentially infected by malware. You receive notifications for any of these detected scenarios, which enables you to potentially avoid problems caused by compromised credentials. For example, a suspicious pattern might be a user who signs in from two different geographic locations in rapid succession.<br><br>
If you implement multi factor authentication (MFA), you can mitigate the risk of stolen credentials. MFA requires the user to provide additional information beyond user name and password for authentication. The additional information might be a code sent to a phone via a text message, or acknowledging a prompt in an app. With MFA enabled, stolen credentials alone cannot be used to sign in.|
|Information protection|Intune helps protect information on mobile devices in multiple ways. First, if the entire device is protected, then Intune can wipe a lost or stolen device to ensure that data on the device is not accessed by unauthorized users.<br><br>
If your organization allows users to bring your own device (BYOD), Intune can separate personal and organizational data. Even managed apps are isolated from personally installed apps to prevent data from being copied between them. Furthermore, if a user leaves the organization, you can wipe the organizational data and apps without affecting personal data.
You can implement Azure Information Protection to prevent data from leaking outside of your organization to unauthorized users. Conditions set in documents control which users can access or modify the contents of the documents. Because the documents’ contents are encrypted, if they are forwarded to an unauthorized user, that user cannot view the contents.|

## Understand the EMS components

**Azure AD Premium** is the central identity store that you use for all the applications in EM+S and Microsoft   365. Some of the additional features included with the P1 and P2 plans are:
- Self-service password reset.
- Write-back from Azure AD to on-premises AD DS.
- Microsoft Azure Multi-Factor Authentication (MFA) for cloud and on-premises apps.
- Conditional access based on group, location, and device state.
- Conditional access based on sign-in or user risk (P2 plan only).

**Intune** enables you to manage mobile devices and apps. Using Intune, you can enforce security policies, wipe devices remotely, and deploy apps. 

**Azure Information Protection** encrypts documents and enforces policies on their use. Document data is more protected because only authorized users can access the contents.  

**Advanced Threat Analytics** can: 
- Detect suspicious activities and malicious attacks.
- Adapt to the changing nature of cyber-security threats.
- Provide focus and clarity around what is important with a simple attack timeline.
- Reduce false positives.

**Cloud App Security** uses data collected from your firewalls and proxy servers to identify cloud application usage. This can help identify unauthorized applications that might be a threat to your data. Additionally, it can identify unusual usage patterns that might indicate a problem. 
EM+S is provided as part of Microsoft 365 E3 and E5 p  lans, as summarized in the table below. 

|Product|	E3 plan|	E5 plan|
|-|-|-|
|Azure AD Premium|	P1 plan|	P2 plan|
|Intune|	Yes|	Yes|
|Azure Information Protection|	P1 plan|	P2 plan|
|Microsoft Advanced Threat Analytics|	Yes|	Yes|
|Cloud App Security|	No|	Yes|
