## Overview of security and compliance
Now, let’s look at new capabilities you can take advantage of when moving to Windows 10, Office 365 ProPlus, and cloud-based options from Enterprise Mobility + Security and beyond.

## Identity and access management
Azure Active Directory is the identity control plane for apps, devices, and cloud services while being the modern solution for connecting to Office 365 and other cloud services. Conditional access allows IT admins to define different authentication requirements based on where an end user is logging in from and which device they’re using as well as responses to anomalous behaviors.

At the device level, biometrics can provide unique identifiers for simpler and more secure access to devices and apps, as organizations move toward the goal of eliminating passwords. Windows Hello offers device-based, multi-factor authentication relying on the device itself, your PIN, or a unique biometric identifier such as your face or fingerprint which can be enforced via policy.


## Virtualization-based security
Beyond identity, it is important to consider continuous protection against both known and unknown threats. Windows 10 uses virtualization-based security at the core using Secure Boot to ensure boot and code integrity. You can also help stop credential theft with Credential Guard by maintaining user secrets in isolation from Windows. Application Guard can isolate and mitigate browser-based threats by running the browser in an isolated container. All of these technologies use virtualization-based security in Windows 10 and are foundational changes that cannot be replicated on a Windows 7 system. Note that these also require UEFI, 64-bit Windows, and virtualization extension support with SLAT – at the hardware level.

## Security enhancements from cloud services
Cloud services provide another layer of optional protection to improve Windows and Office security. These provide IT admins a new level of often real-time control that can instantly detect, resist, and respond to new attacks and attack types–especially compared to traditional software updating and AV signature files – where response and update deployment times are inherently slower.

Along with the Microsoft Intelligent Security Graph, you have faster access to both information and protections from emerging threats. Here are a few examples of security enhancements you can take advantage of:


- **Data Loss Prevention,** built into Office 365 ProPlus, helps inform users of security policies when high risk content like credit card or identification numbers are detected. Policies can inform or block sending and sharing after notifying users.

- **Azure Information Protection** is a complementary service that can be used with Office, allowing users to easily classify and label their Office files. It can trigger automatic action on labeled files, such as encryption or locking down sharing.

- **Safe Links** supplies protection across Office apps to protect against a dynamic list of known malicious websites.

- **Safe Attachments** in Outlook and as part of Exchange Online goes beyond email filtering to inspect attachments. If a high-risk attachment is identified, Safe Attachments will inform the user of known malicious attachments and remove them from email.

- **Office 365 Message Encryption (OME)** safeguards sent email and attachments, ensuring only intended recipients can view email content. OME works seamlessly with Google, Yahoo, and Microsoft consumer account authentication,and one-time passcodes allow users of other email services to securely receive email as well.


- **Windows Defender Application Control** in Windows 10 operates off an approved allow and deny list of applications that Microsoft has checked for safety. It is managed by endpoint protection policies using Microsoft Intune.

- **Windows Defender Advanced Threat Protection** is a unified platform for preventative protection, post-breach detection, automated investigation, and response. It protects endpoints from cyber threats; detects advanced attacks and data breaches, automates security incidents and improves security posture.

- **Exploit Guard** helps reduce the attack surface for running applications by preventing malware from getting into Windows and blocking untrusted processes from accessing protected folders.

## Microsoft Intune
[Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune) serves as a cloud-based management service for mobile scenarios, including iOS, Android, and Windows devices, and it can now be configured by co-management to complement and extend controls for specific workloads managed by System Center Configuration Manager. Devices accessing protected resources can be required to enroll in device management, even non-managed, non-domain joined or non-Azure AD joined devices. You can also take advantage of granular configuration and compliance policy enforcement at the operating system and application level. Application policies and settings can be configured centrally and enforced for Office 365 ProPlus and Store apps in Windows 10 using Microsoft Intune.