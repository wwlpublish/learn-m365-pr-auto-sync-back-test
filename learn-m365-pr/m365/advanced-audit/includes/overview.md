Auditing plays an important role in the security and compliance strategy for many organizations. Microsoft 365 delivers comprehensive audit logs and alerts across more than 15 services, so you can track user and administrator activity. Here is a short list of some of the activities available in the audit log:

- User and admin activity in Exchange Online
- Admin activity in Azure Active Directory
- User and admin activity in SharePoint Online
- eDiscovery activity in the Microsoft 365 compliance center
- User and admin activity for sensitivity labels

## Enterprise-scale audit is essential

Enterprise-scale audit is essential to most organizations, and Microsoft dedicates substantial resources to support your audit requirements. Microsoft audits over 1,500 unique event types spanning Microsoft 365 services and beyond, and processes approximately 15 billion records per day. In addition, Microsoft customers run 60 million user activity searches every day against Microsoft 365 services.  

:::image type="content" source="../media/enterprise-scale-audit.png" alt-text="Enterprise-scale audit is essential to modern organizations.":::

## Comprehensive and unified logs

Admins can go to a single place and use the same tools to access audit information from services like SharePoint Online, Exchange Online, and Microsoft Teams. A common audit activity schema makes searching a consistent experience, regardless of the event type or service. The management API enables seamless integration with other solutions, like Security Information and Event Management (SIEM) tools. Audit events are accessible in the following ways:

- Microsoft 365 compliance center
- PowerShell
- Office 365 Management API

## Using audit beyond reporting

Organizations are increasingly trying to do more with auditing as the security and compliance landscape evolves. Traditionally, auditing has been used primarily for reporting purposes. For example, an IT admin would use audit to identify who was using what and how often, or organizations may use audit to provide documented audit trails. That type of auditing remains important, but organizations now want to do more with the signals captured in the audit logs. For example, security operations teams want to use auditing for investigating breaches and identified threats with an eye on proactive attack detection and prevention. Compliance and privacy teams want to know the services that are being used, along with applicable regulations. Overall, organizations need more tools to investigate data breaches and respond to security and compliance events in a defensible manner.

## Advanced Audit in Microsoft 365

Microsoft 365 Advanced Audit adds new auditing capabilities that can help your organization with forensic and compliance investigations. Advanced Audit builds on Microsoft 365 auditing and extends it with the following capabilities:

- Access crucial events
- Preserve audit logs
- High-bandwidth access to data

> [!NOTE]
> This feature is a capability included with:
>
> - Microsoft 365 E5
> - Microsoft 365 E5 Compliance
> - Microsoft 365 E5 eDiscovery and Audit
>
> Please review [Microsoft 365 licensing guidance for security & compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance?azure-portal=true) to identify required licenses for your organization.

## Access crucial events

Basic Microsoft 365 auditing capabilities give you access to over 1,500 audit event types that satisfy most requirements. However, there are some situations where this may not provide enough information to determine when someone breached your environment, or what the attacker accessed. For example, if an earnings document was leaked in an email, the basic auditing events don't tell you who opened the email. This signal could make a critical difference in a forensic investigation. Without clear indicators, you must assume the worst, which can lead to higher cost and longer turnaround time to control risk.

New crucial security and compliance events will help you investigate security breaches. The first of these crucial audit events released is the **MailItemsAccessed** mailbox auditing action. This action is triggered when mail data is accessed by mail protocols and mail clients. The **MailItemsAccessed** action can help investigators identify data breaches and determine the scope of messages that may have been compromised. If an attacker gained access to email messages, the **MailItemsAccessed** action will be triggered even if no explicit signal messages were actually read.

## Preserve audit logs

The default Microsoft 365 audit log retention period is 90 days. Research indicates the time to detect a breach is about 200 days. Audit log events have sometimes already been aged out and deleted by the time many breaches have been identified, rendering the logs useless to the investigation. Additionally, once detected, breach investigations can take six months to one year, outlasting the basic audit log retention period.

Longer term audit log retention can help with ongoing forensic or compliance investigations. Advanced Audit retains all Exchange, SharePoint, and Azure Active Directory audit records for one year. This is accomplished by a default audit log retention policy that retains any audit record containing the value of **Exchange, SharePoint**, or **AzureActiveDirectory** for the Workload property, indicating the service with which the audit record is associated.

Audit records not covered by the default audit log retention policy in Advanced Audit are retained for 90 days. However, you can create custom policies to retain these audit activities for up to ten years, based on one or more of the following parameters:

- Microsoft 365 service where the audited activities occur
- Specific audited activities
- The user performing an audited activity

Custom audit log retention policies have priority over the default audit log retention policy. You can also set the audit log retention policy priority level so specific policies will take priority over others. A situation where this could apply is if you want to retain Exchange, SharePoint, or Azure Active Directory audit records for less than a year for some or all users in your organization. You can have a maximum of 50 custom audit log retention policies in your organization. The table below summarizes the key differences between basic audit logging and Advanced Audit retention.

|  Feature | Basic audit  |  Advanced Audit |
|---|---|---|
|  Turn audit log on/off |  Yes | Yes  |
|  Custom retention period | No  |  Yes |
|  Maximum retention duration | 90 days  | 10 years |

>[!NOTE]
> If you need to retain audit logs for 10 years, you need both the appropriate E5 license and a 10-year audit log retention add-on license.

## High-bandwidth access to data

Audit log generation and consumption is a bandwidth-intensive activity. The bandwidth required to consume audit events, especially via the Office 365 Management Activity API, could become a bottleneck due to a number of factors, including the sheer volume of audit log activity.

Advanced Audit changes the way bandwidth is allocated to enable faster access to audit events. Prior to the release of Advanced Audit, organizations accessing audit logs through the Office 365 Management Activity API were restricted by throttling limits at the publisher level. The limit for a publisher pulling data on behalf of multiple customers was shared by all those customers. This negatively impacted independent software vendors (ISVs) that built solutions like Security Information and Event Management (SIEM) systems that used the API, along with the customers of those solutions. With Advanced Audit, the publisher-level limit is now a tenant-level limit, which helps to alleviate this bottleneck.

Each organization gets their own fully allocated bandwidth to access auditing data. The bandwidth is not a static predefined limit but is modeled on a combination of factors. All organizations are initially allocated a baseline of 2,000 requests per minute. This limit will dynamically increase depending on an organization's seat count and their licensing subscription. Organizations licensed for Advanced Audit will get approximately twice as much bandwidth as those that are not. There will also be a cap on the maximum bandwidth to protect the health of the service.

## Learn more

- [Search the audit log in the compliance center](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance#introduction?azure-portal=true)
- [Office 365 Management APIs](/office/office-365-management-api/?azure-portal=true)
- [Audited Activities](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance#audited-activities?azure-portal=true)
- [Detailed properties in the audit log](/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log?azure-portal=true)
- [Microsoft 365 licensing guidance for advanced audit](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#advanced-audit?azure-portal=true)
