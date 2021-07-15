Companies considering a migration to Microsoft Teams need to know that their data will be protected with industry-leading tools. They also need to comply with data protection regulations in force wherever they operate.

Suppose you've reassured yourself that Microsoft has built Teams with secure principals but you're still concerned about malicious or disgruntled internal users and the use of attachments to chat messages. You also want to know how you'll comply with regulations in your jurisdiction, if legal action is taken against you.

Here, you'll learn about the advanced protection tools that are available in Teams and compliance features.

## Manage security

**Microsoft Defender for Endpoint** is a unified platform for detecting and blocking files identified as malicious. Microsoft Defender for Endpoint protects endpoints from cyber threats, detects advanced attacks and data breaches, and automates the handling of security incidents. It's available for Microsoft Teams, and SharePoint and OneDrive, which are used by Teams for content management. Microsoft Defender for Office 365 allows you to identify malicious content in any of these applications and block the content from user access.

**Safe attachments** detects malicious attachments. Global or security administrators create policies for handling these suspected malicious attachments to prevent them from being sent to users, clicked, and acted upon. Safe attachment protection is available to SharePoint, OneDrive, and Microsoft Teams.

**Conditional Access** is a security feature of Azure Active Directory (Azure AD). Microsoft Teams relies on Exchange Online, SharePoint, and Skype for Business Online for core features such as meetings, calendars, interop chats, and file sharing. When a user signs into Microsoft Teams, the Conditional Access policies that are set for these cloud apps apply to the Teams user.

Conditional Access uses multiple signals to determine whether a user or device is trustworthy. Conditional Access policies are made up of if-then statements that are enforced after first-factor authentication is complete. Microsoft Teams is supported separately as a cloud app in Azure Active Directory Conditional Access policies.

## Manage compliance

Teams has a range of tools to help you with compliance, including information barriers, communication compliance for channels, chats, and attachments, retention policies, Data Loss Protection (DLP), and e-discovery. To manage the settings for the features covered in this topic, go to the Microsoft 365 compliance center.

**Information barriers** are policies put in place by Teams administrators to prevent people or groups from communicating with one another. You set information barriers in cases where there's no business need for people to communicate, or there's a regulatory reason to prevent them from communicating. Information barriers also allow you to set policies such as lookups and e-discovery. These policies can affect users in one-to-one chats, group chats, or at a team level.

**Communication compliance** is a Microsoft 365 feature that mitigates the risk of users sending inappropriate messages. Communication compliance helps you to detect, capture, and act on inappropriate messages in your organization. Use predefined and custom policies to scan for offensive language, sensitive information, and information related to internal and regulatory standards. Both internal and external communications can be scanned for policy matches. Reviewers can investigate scanned email, Microsoft Teams, Yammer, or third-party communications. Reviewers make sure content is compliant with your organization's message standards and take action where necessary.

**Retention policies** help you to manage information retention in your organization. Use retention policies to keep data that must be stored to comply with your organization's internal policies, industry regulations, or legal needs. Retention policies are also used to delete data that's considered a liability, that you're no longer required to keep, or has no legal or business value.

By default, Teams chat, channel, and files data are kept indefinitely. Retention policies for Teams are created and managed in the Microsoft 365 compliance center or by using the Microsoft 365 Defender portal PowerShell cmdlets. You can apply a Teams retention policy to your entire organization or to specific users and teams. You can set up Teams retention policies for chat and channel messages, and decide whether to retain the data, delete it, or keep it for a specific period of time.

**DLP capabilities** include Microsoft Teams chat and channel messages, and private channel messages. If your organization has DLP, you can define policies that prevent people from sharing sensitive information in a Microsoft Teams channel or chat session.

**E-discovery** is the process of identifying, collecting, and producing electronically stored information (ESI) when needed. E-discovery allows you to respond to a legal case involving people in your organization. This process might involve finding and keeping specific information in email, documents, instant messaging conversations, and other locations. Within Teams, e-discovery includes chat, messaging, files, meeting, and call summaries.
You can do these and other similar activities in the Microsoft 365 Defender portal.

## Learn more

- [Security and compliance in Microsoft Teams](/microsoftteams/security-compliance-overview)
- [Information barriers in Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [Microsoft Compliance Center](https://compliance.microsoft.com/)
- [Retention policies in Microsoft Teams](/microsoftteams/retention-policies)
- [Data loss prevention and Microsoft Teams](/microsoft-365/compliance/dlp-microsoft-teams)
- [Manage legal investigations in Microsoft 365](/microsoft-365/compliance/manage-legal-investigations)
