> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2ZahU]

Digital estates are growing more complex. They include devices, data, networks, apps, and identities, some of which your organization may own, some not. With this growth, the attack surface has expanded to the point where no single service can comprehensively:

- protect an organization from attack
- rapidly detect malicious activity
- effectively respond to and remediate threats across the digital estate

That's why Microsoft has developed different services that specialize in protecting against various threat vectors such as endpoints, networks, email, and business critical data. These services integrate via the Microsoft Graph. The Microsoft Graph uses advanced analytics to link a massive amount of threat intelligence and security data to real-time threat protection in Microsoft 365.

![Microsoft Threat Protection](../media/protection-services.png)

*Microsoft Threat Protection covers these five areas*

Let's take a closer look at some of the main Threat Protection services included in Microsoft 365.

## Azure Active Directory Identity Protection

Azure Active Directory uses adaptive machine learning algorithms and heuristics to detect anomalies and suspicious incidents that indicate potentially compromised identities. Using this data, Identity Protection generates reports and alerts so you can evaluate issues and take action.

Azure Active Directory Identity Protection is more than a monitoring and reporting tool - you can configure risk-based policies that automatically respond to issues. These policies, along with other Conditional Access controls provided by Azure Active Directory and EMS, can either automatically block or start remediation actions like resetting passwords and enforcing multifactor authentication.

## Azure Advanced Threat Protection (ATP)

Azure Advanced Threat Protection (ATP) is a cloud-based security solution that identifies, detects, and helps you investigate advanced threats, compromised identities, and malicious insider actions directed at your organization. 

Through security reports and user profile analytics, Azure ATP helps reduce your attack surface, making it harder to compromise user credentials and advance an attack.

## Microsoft Defender for Cloud

Microsoft Defender for Cloud provides unified security management and advanced threat protection across hybrid cloud workloads. Get a unified view of security across your on-premises and cloud workloads, automatically discover and onboard new Azure resources, and apply security policies to ensure compliance with security standards. You can collect, search, and analyze security data from a variety of sources, including firewalls and partner solutions.

## Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps gives you visibility into your cloud apps and services, provides analytics to identify and combat cyberthreats, and enables you to control how your data travels. The Defender for Cloud Apps framework helps you:
- Discover and control the use of Shadow IT
- Protect your sensitive information anywhere in the cloud
- Protect against cyberthreats and anomalies
- Assess the compliance of your cloud apps 

## Microsoft Exchange Online Protection (EOP)

Microsoft Exchange Online Protection (EOP) is a cloud-based email filtering service that helps protect against spam and malware and includes features to safeguard against messaging-policy violations. EOP can simplify the management of your messaging environment and alleviate many of the burdens that come with maintaining on-premises hardware and software.

## Microsoft Intune

Microsoft Intune, a component of Microsoft Endpoint Management (MEM) integrates closely with other endpoint management components, including Azure Active Directory (Azure AD) for identity and access control and Azure Information Protection for data protection. When you use it with Microsoft 365, you can help your users be productive on all their devices, while protecting your information.

## Office 365 Advanced Threat Protection

Because email is a primary way malware gets into your organization, Advanced Threat Protection helps to identify threats before they land in a user’s mailbox. This feature, included in Microsoft 365 E5 subscriptions, provides protection by scanning email and URLs, identifying malicious files, and detecting when someone tries to impersonate one of your users to access your organization's data.


### Explore how to create Office 365 ATP policies

View a [video version](https://www.microsoft.com/videoplayer/embed/RE44izH) of the interactive guide (captions available in more languages).

<a href="https://mslearn.cloudguides.com/guides/Create%20Office%20365%20ATP%20policies">![Create Office 365 ATP Policies](../media/lab-atp-image.png)</a>  

Be sure to click the full-screen option in the video player, to make it easier to see. When you're done, use the **Back** arrow in your browser to come back to this page.


## Office 365 Threat Intelligence

Office 365 Threat Intelligence is a collection of insights and information available in the Microsoft 365 Defender portal. Office 365 Threat Intelligence monitors signals and gathers data from multiple sources, such as user activity, authentication, email, compromised PCs, and security incidents. You can use this information to understand and respond to threats against users and intellectual property.

## Windows Defender Advanced Threat Protection (ATP)

Windows Defender Advanced Threat Protection (ATP) helps you prevent, detect, investigate, and respond to advanced threats. Windows Defender ATP uses technologies built into Windows 10 that connect to Microsoft's cloud services. Endpoint behavior sensors collect data and send it to cloud security analytics, Microsoft optics that use big data and machine learning to turn behavioral data into insights, detections, and recommended responses. ATP also uses threat intelligence collected from Microsoft hunters, security teams, and partners to identify attacker tools and generate alerts when it detects them in data from the endpoint sensors.

## Windows 10

Windows 10 includes built-in security protections to help safeguard against viruses, phishing, and malware. 

- **BitLocker and credential guard** help protect the integrity of the boot process and user credentials.
- **Windows Hello** uses biometric authentication (fingerprints and facial recognition) to guard against potential spoofing. 
- **Windows Information Protection (WIP)** helps protect enterprise apps and data against accidental data leaks on both enterprise-owned and personal devices.
