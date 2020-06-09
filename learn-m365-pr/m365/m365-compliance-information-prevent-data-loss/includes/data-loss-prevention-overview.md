To comply with business standards and industry regulations, it's critical that your organization protect sensitive information to prevent its inadvertent disclosure. Sensitive information can include financial data or personally identifiable information (PII) such as credit card numbers, social security numbers, or health records. To help with this, use data loss prevention (DLP) policies to identify, monitor, and automatically protect sensitive info across Microsoft 365. DLP is more about preventing users from accidentally sharing sensitive information. If a user is determined to send sensitive data outside the organization, they will find another way to do so. DLP policies can:
- Identify sensitive information across many locations, such as Exchange Online, SharePoint Online, OneDrive for Business, and Microsoft Teams.
- Prevent the accidental sharing of sensitive information.
- Monitor and protect sensitive information in the desktop versions of Excel, PowerPoint, and Word.
- Help users learn how to stay compliant without interrupting their workflow.

Each DLP policy contains the following information:
- **Where to protect the content**. Content is protected in locations like SharePoint Online, Exchange Online, OneDrive for Business accounts, and Microsoft Teams chat and channel messages.
- **When and how to protect the content**. When and how to protect the content is defined by enforcing rules. A policy contains one or more rules, and each rule consists of conditions and actions at a minimum. For each rule, when the conditions are met, the actions are taken automatically. 
    - **Conditions**. The content must match a set of conditions before the rule is enforced. A condition might be configured to look only for content containing credit card information that has been shared with people outside the organization, for example.
    - **Actions**. These are what happens when content matching the conditions is identified. An action could be to block access to a document and send the user and compliance manager an email notification.

> [!NOTE]
> Information the user should notice even if skimmingPlease refer to the Microsoft 365 licensing guidance for security and compliance for additional information on the licensing requirements for this solution.

## Customer scenarios

Here is some scenarios Microsoft’s solution for data loss prevention can address:
- Identify any document containing credit card number stored in users’ OneDrive for Business accounts.
- Automatically block an email containing employee personally identifiable information (PII) from being sent outside the organization.

## Getting started with data loss prevention
You don't want a new DLP policy to unintentionally block access to thousands of documents users require access to. Consider rolling DLP policies out gradually to assess their impact and test their effectiveness before fully enforcing them. 

Here is a three-step process to implementing DLP policies to minimize the risk of unintended consequences:
1. **Start in test mode without policy tips**. Use the DLP reports and incident reports to assess the impact of the policy. You can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, you can fine-tune the rules as needed. Configuring a DLP policy in this way will not impact user productivity.
1. **Move to test mode with notifications and policy tips**. Adding notifications and policy tips gives you the opportunity to educate users about your compliance policies and prepare them for the rules that are going to be applied. At this stage, you can also ask users to report false positives so that you can refine the rules.
1. **Start full enforcement**. The actions in the rules are applied and the content is protected once full enforcement is in place. Continue to monitor the DLP reports and any incident reports or notifications to make sure that the results are what you intend.

These options are configured in the policy settings step of the DLP policy configuration process, which is covered in this module.

## Learn more
- [Overview of data loss prevention](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies?azure-portal=true)
- [Microsoft 365 security & compliance licensing guidance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance?azure-portal=true)
- [Data loss prevention for Exchange Online, SharePoint Online, and OneDrive for Business licensing guidance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance%23office-365-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business?azure-portal=true)
- [Data loss prevention for Teams chat and channel messages licensing guidance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-loss-prevention-for-teams-chat-and-channel-messages?azure-portal=true)
