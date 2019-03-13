Microsoft Threat Protection helps protect users, identities, devices, user data, apps, and your infrastructure.

![Microsoft Threat Protection](../media/2-threat-protection.png)

- **Identities**. Detect suspicious user behavior, logins from multiple locations, and more. Solutions include Azure Active Directory Identity Protection, Azure Advanced Threat Protection, Microsoft Cloud App Security.
- **Endpoints**. Help prevent attacks on devices, detect anomalous behavior, like suspicious processes, and automatically block potential threats. Solutions include Windows Defender Advanced Threat Protection, Windows 10, Microsoft Intune.
- **User Data**. Apply analytics and intelligence to prevent threats such as phishing and 0-day attacks. Microsoft solutions include: Exchange Online Protection, Office 365 Advanced Threat Protection, Office 365 Threat Intelligence, Windows Defender Advanced Threat Protection, Microsoft Cloud App Security.
- **Cloud Apps**. Exchange Online Protection, Office 365 Advanced Threat Protection, Microsoft Cloud App Security.
- **Infrastructure**. Azure Security Center, SQL Server, Linux.

Microsoft threat protection solutions help you deal with threats to your users, devices, and data.

## Azure Active Directory Identity Protection 
Azure Active Directory Identity Protection, a feature of the Azure AD Premium P2 edition, helps you:

- Detect potential identity vulnerabilities.
- Configure automated responses to detected suspicious actions related to your organization’s identities. 
- Investigate suspicious incidents and take appropriate action to resolve them.

Azure Active Directory uses adaptive machine learning algorithms and heuristics to detect anomalies and suspicious incidents that indicate potentially compromised identities. Using this data, Identity Protection generates reports and alerts so you can evaluate issues and take action.

Azure Active Directory Identity Protection is more than a monitoring and reporting tool - you can configure risk-based policies that automatically respond to issues. These policies, along with other conditional access controls provided by Azure Active Directory and EMS, can either automatically block or start remediation actions like resetting passwords and enforcing multifactor authentication.

## Azure Advanced Threat Protection (ATP)
Azure Advanced Threat Protection (ATP) is a cloud-based security solution that identifies, detects, and helps you investigate advanced threats, compromised identities, and malicious insider actions directed at your organization. Azure ATP enables you to:
- Monitor users, entity behavior, and activities with learning-based analytics.
- Protect user identities and credentials stored in Active Directory.
- Identify and investigate suspicious user activities and advanced attacks throughout the kill chain.
- Provide clear incident information on a simple timeline for fast triage.

Through security reports and user profile analytics, Azure ATP helps reduce your attack surface, making it harder to compromise user credentials and advance an attack.

## Azure Security Center
Azure Security Center provides unified security management and advanced threat protection across hybrid cloud workloads. Get a unified view of security across your on-premises and cloud workloads, automatically discover and onboard new Azure resources, and apply security policies to ensure compliance with security standards. You can collect, search, and analyze security data from a variety of sources, including firewalls and partner solutions.

## Microsoft Cloud App Security
Microsoft Cloud App Security gives you visibility into your cloud apps and services, provides analytics to identify and combat cyberthreats, and enables you to control how your data travels. The cloud app security framework includes:
- **Cloud Discovery**. Discover all cloud use in your organization, including shadow IT reporting and control and risk assessment.
- **Data Protection**. Monitor and control your data in the cloud by gaining visibility, enforcing DLP policies, alerting, and investigation.
- **Threat Protection**. Detect anomalous use and security incidents. Use behavioral analytics and advanced investigation tools to mitigate risk and to set policies and alerts to achieve maximum control over network cloud traffic.

## Microsoft Exchange Online Protection (EOP)
Microsoft Exchange Online Protection (EOP) is a cloud-based email filtering service that helps protect against spam and malware and includes features to safeguard against messaging-policy violations. EOP can simplify the management of your messaging environment and alleviate many of the burdens that come with maintaining on-premises hardware and software.

You can use EOP for messaging protection in the following ways:
- In a **standalone scenario** EOP provides cloud-based email protection for your on-premises Microsoft Exchange Server 2013 environment, legacy Exchange Server versions, or for any other on-premises SMTP email solution.
- As a **part of Microsoft Exchange Online** by default, EOP protects Microsoft Exchange Online cloud-hosted mailboxes.
- In a **hybrid deployment** you can configure EOP to protect your messaging environment and control mail routing when you have a mix of on-premises and cloud mailboxes.

## Microsoft Intune
Microsoft Intune is the component of Enterprise Mobility + Security (EMS) that manages mobile devices and apps. Intune provides a single management experience to control the mobile devices and computers in your organization. Intune helps you set the enrollment, policies, and configurations for iOS, Android, Windows, and macOS devices. 

With Intune, you can:
- Manage the mobile devices and PCs used to access company data.
- Manage the mobile apps your users need.
- Protect company information by helping to control the way users access and share it.
- Ensure devices and apps are compliant with company security requirements.

Intune integrates closely with other EMS components like Azure Active Directory (Azure AD) for identity and access control and Azure Information Protection for data protection. When you use it with Office 365, you can help your users be productive on all their devices, while protecting your information.

## Office 365 Advanced Threat Protection
Because email is a primary way malware gets into your organization, Advanced Threat Protection helps to identify threats before they land in a user’s mailbox. This feature, included in Microsoft 365 E5 subscriptions, provides protection by:
- Scanning email attachments for malware. 
- Scanning URLs in email messages and Microsoft Office documents. 
- Identifying and blocking malicious files found in online libraries, Microsoft SharePoint, Microsoft OneDrive, and Microsoft Teams.
- Checking email messages for unauthorized spoofing. 
- Detecting when someone attempts to impersonate your users and access your organization's custom domains. 

## Office 365 Threat Intelligence
Office 365 Threat Intelligence helps protect your Office 365 users by:
- Making it easy to identify, monitor, and understand attacks.
- Helping to quickly address threats in Exchange Online and SharePoint Online.
- Providing insights and knowledge to help prevent attacks.

Office 365 Threat Intelligence is a collection of insights and information available in the Office 365 Security & Compliance Center. These insights can help protect Office 365 users from attacks. Office 365 Threat Intelligence monitors signals and gathers data from multiple sources, such as user activity, authentication, email, compromised PCs, and security incidents. Business decision makers and Office 365 global administrators, security administrators, and security analysts can all use this information to understand and respond to threats against users and intellectual property.

## Windows Defender Advanced Threat Protection (ATP)
Windows Defender Advanced Threat Protection (ATP) helps you prevent, detect, investigate, and respond to advanced threats. Windows Defender ATP uses technologies built into Windows 10 that connect to Microsoft's cloud services:
- **Endpoint behavioral sensors**. Collect and process behavioral signals from the OS and send this sensor data to your private, isolated, cloud instance of Windows Defender ATP.
- **Cloud security analytics**. Leverage big-data, machine-learning, Microsoft optics across the Windows ecosystem, to translate behavioral signals into insights, detections, and recommended responses to advanced threats.
- **Threat intelligence**. Generated by Microsoft hunters, security teams, and augmented by threat intelligence provided by partners, threat intelligence enables Windows Defender ATP to identify attacker tools, techniques, and procedures, and generate alerts when these are observed in collected sensor data.

## Windows 10
Windows 10 has built-in security protections to help safeguard you against viruses, phishing, and malware. Hardware and software security features like BitLocker and credential guard help protect the integrity of the boot process and user credentials. Windows Hello helps strengthen authentication and helps to guard against potential spoofing through fingerprint matching and facial recognition. Windows Information Protection (WIP) helps protect against potential data leakage without interfering with the employee experience. WIP also helps to protect enterprise apps and data against accidental data leaks on both enterprise-owned and personal devices without requiring changes to your environment or other apps. Azure Rights Management works alongside WIP to extend data protection for data that leaves the device, such as when email attachments are sent from an enterprise-aware version of a rights management mail client.
