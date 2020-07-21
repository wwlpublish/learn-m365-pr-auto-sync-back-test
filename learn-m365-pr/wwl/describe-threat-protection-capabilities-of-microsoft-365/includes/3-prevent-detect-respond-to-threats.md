## Microsoft Threat Protection

Microsoft Threat Protection is a unified pre- and post-breach enterprise defense suite that natively coordinates detection, prevention, investigation, and response across endpoints, identities, email, and applications to provide integrated protection against sophisticated attacks.
Microsoft Threat Protection suite protects:

* Identities with Azure ATP - Azure ATP uses Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.
* Endpoints with Microsoft Defender ATP - Microsoft Defender ATP is a unified endpoint platform for preventative protection, post-breach detection, automated investigation, and response.
* Applications with Microsoft Cloud App security - Microsoft Cloud App security is a comprehensive cross-SaaS solution bringing deep visibility, strong data controls, and enhanced threat protection to your cloud apps.
* Email and collaboration with Office 365 ATP - Office 365 ATP safeguards your organization against malicious threats by detecting, investigating, and responding to attacks across email and other collaboration vectors like Microsoft Teams, SharePoint Online, and OneDrive for Business and Office clients.

:::image type="content" source="../media/3-threat-protection-v2.png" alt-text="Integrate Microsoft Threat Protection experience":::

## Azure ATP

Azure Advanced Threat Protection (ATP) is a cloud-based security solution that leverages your on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.

Azure ATP enables security professionals struggling to detect advanced attacks in hybrid environments to:

* Monitor and profile user behavior and activities - Azure ATP monitors and analyzes user activities and information across your network, such as permissions and group membership, creating a behavioral baseline for each user.
* Protect user identities and reduce the attack surface - Azure ATP provides you invaluable insights on identity configurations and suggested security best-practices. Through security reports and user profile analytics, Azure ATP helps dramatically reduce your organizational attack surface, making it harder to compromise user credentials, and advance an attack. 
* Identify suspicious activities and advanced attacks across the cyber-attack kill-chain - Typically, attacks are launched against any accessible entity, such as a low-privileged user, and then quickly move laterally until the attacker gains access to valuable assets – such as sensitive accounts, domain administrators, and highly sensitive data.  Azure ATP identifies these advanced threats at the source throughout the entire cyber-attack kill chain.
* Investigate alerts and user activities - Azure ATP is designed to reduce general alert noise, providing only relevant, important security alerts in a simple, real-time organizational attack timeline.

For more information, read What is [Azure Advanced Threat Protection?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)

## Microsoft Defender ATP

Microsoft Defender Advanced Threat Protection is a platform designed to help enterprise networks protect endpoints, by preventing, detecting, investigating, and responding to advanced threats.

:::image type="content" source="../media/3-defender-advanced-threat-protection-v2.png" alt-text="Microsoft Defender Advanced Threat Protection":::

There are seven pillars to Microsoft Defender Advanced Threat Protection:

* Threat & vulnerability management - Threat and vulnerability management is a risk-based approach to the discovery, prioritization, and remediation of endpoint vulnerabilities and misconfigurations. It uses sensors on devices to avoid the need for agents or scans and prioritizes vulnerabilities.
* Attack surface reduction - Attack surface reduction reduces the places where your organization is vulnerable to cyberthreats and attacks.. You can ensure that only allowed apps can run and prevent apps from accessing dangerous locations.
* Next Generation protection - Microsoft Defender Antivirus is the next-generation protection component of Microsoft Defender ATP. Next-generation protection brings together machine learning, big-data analysis, in-depth threat resistance research, and the Microsoft cloud infrastructure to protect devices in your enterprise organization.
* Endpoint detection and response - Microsoft Defender ATP endpoint detection and response capabilities provide advanced attack detections that are near real-time and actionable. Security analysts can prioritize alerts, gain visibility into the full scope of a breach, and take response actions to remediate threats.
* Automated investigation & remediation - The automated investigation feature uses various inspection algorithms, and processes used by analysts (such as playbooks) to examine alerts and take immediate remediation action to resolve breaches. This significantly reduces the volume of alerts that must be investigated individually.
* Microsoft Threat Experts - Microsoft Threat Experts is a managed threat hunting service that provides Security Operation Centers (SOCs) with expert level monitoring and analysis to help them ensure that critical threats in their unique environments don’t get missed.
* Management & APIs - Besides providing a comprehensive and robust endpoint protection solution in its own right, Microsoft Defender ATP provides APIs to integrate with other solutions.

In this video, you'll learn more about Microsoft Defender Advanced Threat Protection:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4zwew]

For more information, read [Microsoft Defender Advanced Threat Protection](https://www.microsoft.com/videoplayer/embed/RE4zwew)

## Microsoft Cloud App Security

Microsoft Cloud App Security (MCAS) is a Cloud Access security broker (CASB).  It operates as an intermediary between a cloud user and the cloud provider, to provide rich visibility to your cloud services, control over data travel, and sophisticated analytics to identify and combat cyberthreats across all your cloud services.

MCAS is built on a framework that provides the following capability:

* Discover and control the use of Shadow IT: Identify the cloud apps, IaaS, and PaaS services used by your organization.  Investigate usage patterns, assess the risk levels and business readiness of more than 16,000 SaaS apps against more than 80 risks.
* Protect your sensitive information anywhere in the cloud: Understand, classify, and protect the exposure of sensitive information at rest. Leverage out-of-the-box policies and automated processes to apply controls in real time across all your cloud apps.
* Protect against cyberthreats and anomalies: Detect unusual behavior across cloud apps to identify ransomware, compromised users or rogue applications, analyze high-risk usage, and remediate automatically to limit the risk to your organization.
* Assess the compliance of your cloud apps: Assess if your cloud apps meet relevant compliance requirements, including regulatory compliance and industry standards. Prevent data leaks to non-compliant apps and limit access to regulated data.

For more information, read [Microsoft Cloud App Security overview](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security).

## Microsoft Office 365 ATP

Office 365 Advanced Threat Protection (ATP) safeguards your organization against malicious threats posed by email messages, links (URLs), and collaboration tools, including Microsoft Teams, SharePoint Online, OneDrive for Business, and other Office clients. ATP includes:

* Threat protection policies: Define threat-protection policies to set the appropriate level of protection for your organization.
* Reports: View real-time reports to monitor ATP performance in your organization.
* Threat investigation and response capabilities: Use leading-edge tools to investigate, understand, simulate, and prevent threats.
* Automated investigation and response capabilities: Save time and effort investigating and mitigating threats.

Office 365 ATP comes in two flavors, as shown in the table below.  

* Office 365 ATP Plan 1 is included in Microsoft 365 Business Premium.
* Office 365 ATP Plan 2 is included in Office 365 E5, Office 365 A5, and Microsoft 365 E5.
* Office 365 ATP Plan 1 and Office 365 ATP Plan 2 are available as an add-on for certain subscriptions.

| Office 365 ATP Plan 1                                                                                                                                                                                    | Office 365 ATP Plan 2                                                                                                                                           |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configuration, protection, and detection capabilities:                                                                                                                                                   | Office 365 ATP Plan 1 capabilities plus automation, investigation, remediation, and education capabilities:                                                     |
| [Safe Attachments](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-safe-attachments?view=o365-worldwide) – checks email attachments for malicious content.                                                                                                                                       | [Threat Trackers](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-trackers?view=o365-worldwide) - provide the latest intelligence on prevailing cybersecurity issues.                                                                           |
| [Safe Links](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-safe-links?view=o365-worldwide) - Links are scanned for each click: safe links remain accessible and malicious links are dynamically blocked.                                                                                 | [Threat Explorer](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer?view=o365-worldwide) - a real-time report that allows you to identify and analyze recent threats.                                                                    |
| [ATP for SharePoint, OneDrive, and Microsoft Teams](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-for-spo-odb-and-teams?view=o365-worldwide) - Protects your organization when users collaborate and share files, by identifying and blocking malicious files in team sites and document libraries. | [Automated investigation and response](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air) - include a set of security playbooks that can be launched automatically, such as when an alert is triggered, or manually. |
| [ATP anti-phishing protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-anti-phishing-policies?view=o365-worldwide#exclusive-settings-in-atp-anti-phishing-policies) - Detects attempts to impersonate your users and internal or custom domains.                                                                                                | [Attack Simulator](https://docs.microsoft.com/microsoft-365/security/office-365-security/attack-simulator?view=o365-worldwide) - allows you to run realistic attack scenarios in your organization to identify vulnerabilities.                                               |
| [Real-time detections](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer?view=o365-worldwide) - a real-time report that allows you to identify and analyze recent threats.                                                                                                        |                                                                                                                                                                 |

To learn more, see Office 365 [Advanced Threat Protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp?view=o365-worldwide).
