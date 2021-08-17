To comply with business standards and industry regulations, it's critical that your organization protects sensitive information to prevent its inadvertent disclosure. Sensitive information can include financial data, health records, credit card numbers, social security numbers, and employee evaluations. Use data loss prevention (DLP) policies to identify, monitor, and automatically protect sensitive information across Microsoft 365. Microsoft DLP helps prevent users from accidentally, rather than intentionally sharing sensitive content. (If a user is determined enough to send sensitive data outside the organization, they will find another way to do so.)

DLP policies can:

- Identify sensitive information across many locations including:
  - Exchange Online
  - SharePoint Online
  - OneDrive for Business
  - Microsoft Teams
  - Windows devices
- Monitor and protect sensitive information in Excel, PowerPoint, Word, and Outlook.
- Prevent the accidental sharing of sensitive information.
- Educate users on staying compliant without interrupting their workflow.
- Produce DLP alerts and reports showing content that matches your organization's DLP policies.

Each DLP policy contains the following:

- **Where to protect the content**: Content is protected in locations like SharePoint Online, Exchange Online, OneDrive for Business accounts, Microsoft Teams chat and channel messages, and Windows 10 devices.
- **When and how to protect the content**: When and how to protect the content is defined by enforcing rules. A policy contains one or more rules, and each rule consists of conditions and actions at a minimum. For each rule, when the conditions are met, the actions are taken automatically.
  - **Conditions**: Circumstances under which a rule is enforced. For example, a condition might be configured to look only for content containing credit card information that has been shared with people outside the organization, but they can be must more sophisticated, as well.
  - **Actions**: Define what happens when content matching the conditions is identified. An action could be to block access to a document and send the user and compliance manager an email notification. The complexity of the actions you specify are based on your business requirements.

You don't want a new DLP policy to unintentionally block access to thousands of documents users require access to. DLP policies should be rolled out gradually to assess their impact and test their effectiveness. Here is a three-step process to implementing DLP policies to minimize the risk of unintended consequences:

1. Start in test mode without policy tips. Use the DLP reports and incident reports to assess the impact of the policy. You can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, you can fine-tune the rules as needed. Configuring a DLP policy in this way will not impact user productivity.
2. Move to test mode with notifications and policy tips. Adding notifications and policy tips gives you the opportunity to educate users about your compliance policies and prepare them for the rules that are going to be applied. At this stage, you can also ask users to report false positives so that you can refine the rules.
3. Start full enforcement. The actions in the rules are applied and the content is protected once full enforcement is in place. Continue to monitor the DLP reports and any incident reports or notifications to make sure that the results are what you intend.

> [!NOTE]
> For more information about the licensing requirements for this solution, see the Microsoft 365 licensing guidance for security and compliance, linked to below.

## Learn more

- [Overview of data loss prevention](/microsoft-365/compliance/data-loss-prevention-policies?azure-portal=true)
- [Microsoft 365 licensing guidance for security & compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)
