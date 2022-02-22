Many organizations just like Contoso are moving some or all of their computing resources into the cloud. There are many drivers behind such moves, but typically organizations seek to take advantage of the efficiencies offered by cloud providers. These efficiencies include enabling flexibility for both employees and IT administrators.

For your users, the cloud provides the ability to work from pretty much anywhere using a range of different devices. But this flexibility presents challenges for IT administrators, particularly in the area of data security. You must balance the needs of your users to access data from anywhere, and your need to secure that data. Microsoft Defender for Cloud Apps can help you strike the right balance.

## Overview of Defender for Cloud Apps

For your organizational data, Defender for Cloud Apps provides you with the following:

- Visibility
- Control
- Analytics

These capabilities enable you to identify and defeat security threats across your organization, both in Microsoft cloud services, and those services provided by other vendors.

Defender for Cloud Apps has several deployment modes, which are described in the following table:

| Mode            | Description                                                  |
| --------------- | ------------------------------------------------------------ |
| Log collection | Enables you to gather data logging data from various sources for analysis. |
| API connectors | Enables you to connect Defender for Cloud Apps to both Microsoft and third-party software as a service (SaaS) platforms. |
| Reverse proxy | Enables you to implement Conditional Access app control over your data. |

### What does Defender for Cloud Apps do?

Defender for Cloud Apps acts as a cloud access security broker (CASB). You use CASBs as gatekeepers to your organizational data. You use a CASB to provide the following capabilities:

- Discover how users use organizational apps.
- Monitor user activities for suspicious or unusual behavior.
- Control access to your resources.
- Classify data and help prevent sensitive data leaks.
- Help protect against malicious hackers.
- Assess the compliance of your cloud services.

By implementing Defender for Cloud Apps, you get a better understanding of what's happening within your organization's IT infrastructure; this helps you to protect your sensitive data from malicious persons. This protection is based on four key pillars:

- Visibility:
  - Detect connected cloud services.
  - Assess each connected service for risk and assign a risk ranking.
  - Identify users and third-party apps that are able to sign in.
- Data security:
  - Identify and control sensitive information (also known as data loss prevention).
  - Respond to classification labels on content.

    > [!NOTE]
    > Data classification labels enable you to categorize your data based on sensitivity.

- Threat protection:
  - Implement adaptive access control.
  - Provide user behavior analysis.
  - Help to mitigate malware.
- Compliance:
  - Provide tools and reports to help validate cloud governance.
  - Help you to conform to data compliance requirements.

### Architecture

In the following diagram, Defender for Cloud Apps sites as an intermediary layer between your users and the apps and data they want to access. Within Defender for Cloud Apps:

- App connectors use APIs to facilitate connections to discovered apps.
- Cloud discovery uses cloud traffic logs to create configuration scripts.
- Proxy access and session provides and manages cloud traffic to and from the discovered apps and your users.

> [!NOTE]
> You can use Defender for Cloud Apps to sanction or un-sanction apps by using the Cloud app catalog.

:::image type="content" source="../media/proxy-architecture.png" alt-text="A diagram that describes the role of Defender for Cloud Apps architecture as detailed in the preceding text." lightbox="../media/proxy-architecture.png":::

### Discovery capabilities of Defender for Cloud Apps versus Azure Active Directory

Azure Active Directory (Azure AD) Premium P1 includes a feature called Azure AD Cloud App Discovery. This feature is based on Cloud Discovery features of Microsoft Defender for Cloud Apps. However, Cloud Discovery in Microsoft Defender for Cloud Apps provides extra capabilities, as described in the following table:

| Capability             | Feature                                                    | Microsoft   Defender for Cloud Apps                      | Azure   AD Cloud App Discovery   |
| ---------------------- | ---------------------------------------------------------- | --------------------------------------------------- | -------------------------------- |
| Cloud Discovery        | Discovered apps                                            | 16,000 + cloud apps                                 | 16,000 + cloud apps              |
|                        | Deployment  for discovery analysis                         | Manual  and automatic log upload                    | Manual  and automatic log upload |
|                        | Log anonymization for user privacy                         | Yes                                                 | Yes                              |
|                        | Access  to full Cloud App Catalog                          | Yes                                                 | Yes                              |
|                        | Cloud app risk assessment                                  | Yes                                                 | Yes                              |
|                        | Cloud  usage analytics per app, user, IP address           | Yes                                                 | Yes                              |
|                        | Ongoing analytics & reporting                              | Yes                                                 | Yes                              |
|                        | Anomaly  detection for discovered apps                     | Yes                                                 |                                  |
| Information Protection | Data Loss Prevention (DLP) support                         | Cross-SaaS DLP and data sharing  control            |                                  |
|                        | App  permissions and ability to revoke access (OAuth apps) | Yes                                                 |                                  |
|                        | Policy setting and enforcement                             | Yes                                                 |                                  |
|                        | Integration  with Azure Information Protection             | Yes                                                 |                                  |
|                        | Integration with third-party DLP  solutions                | Yes                                                 |                                  |
| Threat  Detection      | Anomaly  detection and behavioral analytics                | For  Cross-SaaS apps                                |                                  |
|                        | Manual and automatic alert  remediation                    | Yes                                                 |                                  |
|                        | SIEM  connector                                            | Yes.  Alerts and activity logs for cross-SaaS apps. |                                  |
|                        | Integration to Microsoft Intelligent  Security Graph       | Yes                                                 |                                  |
|                        | Activity policies                                          | Yes                                                 |                                  |

### Differences between Microsoft Defender for Cloud Apps and Office 365 Cloud App Security

Office 365 Cloud App Security provides a subset of the features of Microsoft Defender for Cloud Apps, as described in the following table:

| Capability                     | Feature                                              | Microsoft   Defender for Cloud Apps                      | Office   365 Defender for Cloud Apps                              |
| ------------------------------ | ---------------------------------------------------- | --------------------------------------------------- | ------------------------------------------------------------ |
| Cloud Discovery                | Discovered apps                                      | 16,000 + cloud apps                                 | 750+ cloud apps with similar  functionality to Office 365    |
|                                | Deployment  for discovery analysis                   | Manual  and automatic log upload                    | Manual  log upload                                           |
|                                | Log anonymization for user privacy                   | Yes                                                 |                                                              |
|                                | Access  to full Cloud App Catalog                    | Yes                                                 |                                                              |
|                                | Cloud app risk assessment                            | Yes                                                 |                                                              |
|                                | Cloud  usage analytics per app, user, IP address     | Yes                                                 |                                                              |
|                                | Ongoing analytics & reporting                        | Yes                                                 |                                                              |
|                                | Anomaly  detection for discovered apps               | Yes                                                 |                                                              |
| Information Protection         | Data Loss Prevention (DLP) support                   | Cross-SaaS DLP and data sharing  control            | Uses existing Office DLP (available  in Office E3 and above) |
|                                | App  permissions and ability to revoke access        | Yes                                                 | Yes                                                          |
|                                | Policy setting and enforcement                       | Yes                                                 |                                                              |
|                                | Integration  with Azure Information Protection       | Yes                                                 |                                                              |
|                                | Integration with third-party DLP  solutions          | Yes                                                 |                                                              |
| Threat  Detection              | Anomaly  detection and behavioral analytics          | For  Cross-SaaS apps including Office 365           | For  Office 365 apps                                         |
|                                | Manual and automatic alert  remediation              | Yes                                                 | Yes                                                          |
|                                | SIEM  connector                                      | Yes.  Alerts and activity logs for cross-SaaS apps. | For  Office 365 alerts only                                  |
|                                | Integration to Microsoft Intelligent  Security Graph | Yes                                                 | Yes                                                          |
|                                | Activity  policies                                   | Yes                                                 | Yes                                                          |
| Conditional Access App Control | Real-time session monitoring and control             | Any cloud and on-premises app                       | For Office 365 apps                                          |
| Cloud  Platform Security       | Security  configurations                             | For  Azure, AWS, and GCP                            | For  Azure                                                   |

## Get started with Defender for Cloud Apps

To get started using Defender for Cloud Apps, your organization must meet the following prerequisites:

- Have a license to use Defender for Cloud Apps.
- Activate Defender for Cloud Apps via the portal.
- Be a Global Administrator or a Security Administrator in Azure AD or Office 365 to setup Defender for Cloud Apps.
- Use a supported browser to access the Defender for Cloud Apps portal: Microsoft Edge (latest), Google Chrome (latest), Mozilla Firefox (latest), or Apple Safari (latest).

Then, to start using Defender for Cloud Apps, complete the following high-level steps:

1. Connect your apps.
2. Create policies to control cloud apps.
3. Enable Cloud Discovery.
4. Personalize your experience by configuring email settings, admin notifications, and score metrics.
5. Organize the data according to your needs with IP address tags, domains, and report settings.

Watch the following video for an overview of Microsoft Defender for Cloud Apps:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4MD8S]
