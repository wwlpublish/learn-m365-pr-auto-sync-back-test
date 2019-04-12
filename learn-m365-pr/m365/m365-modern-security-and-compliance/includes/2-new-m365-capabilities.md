Previously we reviewed considerations for moving current protections forward and things to be aware of before the shift to a new desktop. Now, let’s take a look at new capabilities to take advantage of when moving to Windows 10, Office 365 ProPlus, and cloud-based options from Enterprise Mobility + Security and beyond.

## Identity and access management
Azure Active Directory is the identity control plane for apps, devices, and Cloud services while being the modern solution to connect to Office 365 and other Cloud services. Conditional access allows IT admins to define different authentication requirements based on where an end user is logging in from, which device they’re using, as well as things like anomalous behaviors.

At the device level, biometrics can provide unique identifiers for simpler and more secure access to devices and apps - as organizations move toward the goal of eliminating passwords. Windows Hello offers device-based, multi-factor authentication relying on the device itself, your PIN, or unique biometric identifier such as your face or fingerprint which can be enforced via policy.

## Virtualization-based security
Beyond identity it is important to consider continuous protection against both known and unknown threats. To accomplish this Windows 10 uses virtualization-based security at the core to ensure boot integrity and code integrity using Secure Boot. We can also help stop credential theft with Credential Guard by maintaining user secrets in isolation from Windows. Application Guard can isolate and mitigate browser-based threats by running the browser in an isolated container. All of these technologies use virtualization-based security in Windows 10 and are foundational changes that cannot be replicated on a Windows 7 system – note that these also require UEFI, 64-bit Windows and virtualization extension support with SLAT – at the hardware level.

## Security Enhancements from Cloud Services
Cloud services provide another layer of optional protection to improve Windows and Office security. These provide IT admins a new level of often real-time control that can instantly detect, resist and respond to new attacks and attack types – especially compared to traditional software updating and AV signature files – where response and update deployment times are inherently slower.

Along with the Microsoft Intelligent Security Graph, you have faster access to both information and protections from emerging threats. Here are a few examples of what you can take advantage of, starting with Office.

**Data Loss Prevention** built into Office 365 ProPlus, helps inform users of security policies when high risk content like credit card or identification numbers are detected. Policies can inform or block sending and sharing after notifying users.

**Azure Information Protection** is a complementary service that can be used with Office, allowing users to easily classify and label their Office files. It can trigger automatic action on labeled files, such as encryption or locking down sharing.

We’ve also introduced **Safe Links** protection across Office apps to protect you against a dynamic list of known malicious websites.

Additionally, **Safe Attachments** in Outlook and as part of Exchange Online goes beyond email filtering to inspect attachments. If a high-risk attachment is identified, Safe Attachments will inform the user of known malicious attachments and remove them from email.

**Office 365 Message Encryption (OME)** can also be used to safeguard email and attachments sent, ensuring only intended recipients can view email content. OME works seamlessly with Google, Yahoo, and Microsoft consumer account authentication, and one-time passcodes allow users of other email services to securely receive email as well.

### Additional Windows 10 protections
**Windows Defender Application Control in Windows 10** operates off an approved allow and deny list of applications that Microsoft has checked for safety and all that is managed by endpoint protection policies using Microsoft Intune.

**Windows Defender Advanced Threat Protection** is a unified platform for preventative protection, post-breach detection, automated investigation, and response. It protects endpoints from cyber threats; detects advanced attacks and data breaches, automates security incidents and improves security posture.

**Exploit Guard** helps reduce the attack surface for running applications by preventing malware from getting into Windows and blocking untrusted processes from accessing protected folders.

## Microsoft Intune
Microsoft Intune serves as a Cloud based management service for mobile scenarios, including IOS, Android and Windows devices, and can now be configured for co-management to complement and extend controls for specific workloads managed by System Center Configuration Manager. One advantage here is that, devices accessing protected resources can be required to enroll into device management – even non-managed, non-domain joined or non-Azure AD joined devices. You can also take advantage of granular configuration and compliance policy enforcement at the operating system and application level. Application policies and settings can be configured centrally and enforced for Office 365 ProPlus and Store apps in Windows 10 using Microsoft Intune.
