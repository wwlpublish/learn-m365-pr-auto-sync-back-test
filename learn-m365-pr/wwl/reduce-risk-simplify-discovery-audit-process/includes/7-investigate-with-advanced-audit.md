Advanced Audit in Microsoft 365 provides new auditing capabilities that can help your organization with forensic and compliance investigations.

> [!NOTE]
> Advanced Audit is available for organizations with a Microsoft 365 Enterprise E5 subscription. Additionally, a Microsoft 365 E5 Compliance add-on license can be assigned to users for when per-user licensing is required for Advanced Audit features, as is the case for long-term retention of audit logs and access to crucial events for investigations.

Advanced Audit includes these capabilities:

- Long-term retention of audit logs - Advanced Audit retains all Exchange, SharePoint, and Azure Active Directory audit records for one year. This is accomplished by a default audit log retention policy that retains any audit record that contains the value of **Exchange**, **SharePoint**, or **AzureActiveDirectory** for the **Workload** property.
- Audit log retention policies - All audit records generated in other services that aren't covered by the default audit log retention policy are retained for 90 days. However, now you can create customized audit log retention policies to retain other audit records for up to one year.
- Access to crucial events for investigations - The first crucial event that we're releasing is the *MailItemsAccessed* mailbox auditing action. This action is triggered when mail data is accessed by mail protocols and mail clients. The MailItemsAccessed action can help investigators identify data breaches and determine the scope of messages that may have been compromised.
- High-bandwidth access to the Office 365 Management Activity API - With the release of Advanced Audit, each organization will get their own fully allocated bandwidth quota to access their auditing data.
