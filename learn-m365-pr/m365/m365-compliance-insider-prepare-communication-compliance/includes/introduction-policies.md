## Communication compliance policies

Communication compliance policies define which communications and users are subject to review in your organization, define the conditions the communications must meet, and specifies who should do reviews. Users included in the **Supervisory Review Administrator** role group can set up policies, and anyone who has this role assigned can access the **Communication compliance** page in the Microsoft 365 compliance center. If needed, you can export the history of modifications made to a policy to a .csv file that also includes the status of alerts pending review, escalated items, and resolved items. Policies cannot be renamed but can be deleted when no longer needed.

You create communication compliance policies for Microsoft 365 organizations in the Microsoft 365 compliance center. Using PowerShell to create and manage communication compliance policies is not supported.

### Policy templates

Policy templates contain pre-defined policy settings that you can use to quickly create policies to address common compliance scenarios. Each of these templates has differences in conditions and scope, and all the templates use the same types of scanning signals. You can choose from the following policy templates in the Microsoft 365 compliance center:

- **Offensive language and anti-harassment**: Use this template to quickly create a policy that uses the threat, profanity, and harassment language classifiers to automatically detect content that may be considered abusive or offensive.
- **Sensitive information**: Use this template to create a policy to scan communications containing defined sensitive information types or keywords to help make sure that important data isn't shared with people that shouldn't have access.
- **Regulatory compliance**: Use this template to create a policy to scan communications for references to standard financial terms associated with regulatory standards.

### Policy settings

There are several policy settings you can customize, including the following:

- **Users.** You can select **All users** or specific users in a communication compliance policy. Selecting **All users** applies the policy to all users and all groups that any user is included in as a member. Defining specific users applies the policy to the defined users and any groups the defined users are included in as a member.
- **Direction.** Direction settings in a policy can be chosen individually or together:
  - **Inbound.** You can choose **Inbound** to review communications sent *to* the people you chose to supervise.
  - **Outbound.** You can choose **Outbound** if you want to review communications sent *from* the people you chose to supervise.
  - **Internal.** You can choose **Internal** to review communications sent *between* the people you identified in the policy.
- **Sensitive information types.** You have the option of including sensitive information types to help identify and protect credit card numbers, bank account numbers, passport numbers, and more. As part of [data loss prevention (DLP)](/microsoft-365/compliance/data-loss-prevention-policies?azure-portal=true), the sensitive information configuration can use patterns, character proximity, confidence levels, and even custom data types to help identify and flag content that may be sensitive. To learn more about sensitive information details and the patterns included in the default types, see [What sensitive information types look for](/microsoft-365/compliance/what-the-sensitive-information-types-look-for?azure-portal=true).
- **Custom keyword dictionaries.** You can create custom dictionaries when you need to support terms or languages specific to your organization and policies. For more information, see [Create a keyword dictionary](/microsoft-365/compliance/create-a-keyword-dictionary?azure-portal=true).

- **Classifiers.** Built-in classifiers scan sent or received messages across all communication channels in your organization for different types of compliance issues. Classifiers use a combination of artificial intelligence and keywords to identify language in messages likely to violate anti-harassment policies. Communication compliance built-in classifiers scan communications for terms and sentiment for the following types of language:
  - **Harassment.** Scans for offensive conduct targeting people regarding race, color, religion, national origin.
  - **Profanity.** Scans for profane expressions that embarrass most people.
  - **Threat.** Scans for threats to commit violence or physical harm to a person or property.

   For information about classifiers in Microsoft 365, see [Classifiers](/microsoft-365/compliance/classifier-getting-started-with?azure-portal=true).

- **Conditional settings**. The conditions you choose for the policy apply to communications from both email and third-party sources in your organization (like from Facebook or DropBox). This [table](/microsoft-365/compliance/communication-compliance-feature-reference?conditional-settings?azure-portal=true) explains more about each condition that is available and when to use it.

- **Review percentage.** If you want to reduce the amount of content to review, you can specify a percentage of all the communications governed by a supervision policy. A real-time, random sample of content is selected from the total percentage of content that matches chosen policy conditions. If you want reviewers to review all items, you can configure *100%* in a communication compliance policy.

## Supervised users and reviewers

Before you start using communication compliance, you must determine who needs their communications reviewed. In the policy, user email addresses identify individuals or groups of people to supervise. Some examples of these groups are Microsoft 365 Groups, Exchange-based distribution lists, and Microsoft Teams channels. You also can exclude specific users or groups from scanning with a specific exclusion group or a list of groups.

Before you create a communication compliance policy, you must also determine who reviews the messages of the supervised users. In the policy, user email addresses identify individuals or groups of people to review supervised communications. All reviewers must have mailboxes hosted on Exchange Online and must be assigned the **Case Management** and **Review** roles.

To simplify your setup, you can create groups for people who need their communications reviewed and groups for people who review those communications. If you're using groups, you might need several. For example, if you want to scan communications between two distinct groups of people, or if you want to specify a group that isn't supervised.

When you select a Microsoft 365 group for supervised users, the policy scans the content of the shared Office 365 mailbox and the Microsoft Teams channels associated with the group. When you select a distribution list, the policy scans individual user mailboxes.

## Supported communication types

With communication compliance policies, you can choose to scan messages in one or more of the following communication platforms, individually or as a group. By default, communications captured across these platforms are retained for seven years for each policy, even if users leave your organization and their mailboxes are deleted.

- **Microsoft Teams**: Chat communications and associated attachments in both public and private Microsoft Teams channels and individual chats can be scanned. Teams chats and attachments matching communication compliance policy conditions may take up to 24 hours to process. You can use the following group management configurations to supervise individual user chats and channel communications in Teams:
  - **For Teams chat communications**: Assign individual users or assign a distribution group to the communication compliance policy. This setting is for one-to-one or one-to-many user/chat relationships.
  - **For Teams channel communications**: Assign every Microsoft Team channel or Microsoft 365 group you want to scan that contains a specific user to the communication compliance policy. If you add the same user to other Microsoft Teams channels or Microsoft 365 groups, be sure to add these new channels and groups to the communication compliance policy.
- **Exchange email**: All mailboxes hosted on Exchange Online as part of your Microsoft 365 subscription are all eligible for message scanning. Supported attachment types for communication compliance are the same as the [file types supported for Exchange mail flow rule content inspections](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection?azure-portal=true).
- **Yammer**: Private messages and public community conversations in [Yammer](/yammer/yammer-landing-page?azure-portal=true) are supported in communication compliance policies. Yammer is an optional channel and must be in [native mode](/yammer/configure-your-yammer-network/overview-native-mode?azure-portal=true) to support scanning of messages and attachments.
- **Skype for Business Online**: Chat communications and associated attachments in Skype for Business Online can be supervised. Skype for Business Online chats matching communication compliance policy conditions may take up to 24 hours to process. Supervised chat conversations are sourced from previous conversations saved in Skype for Business Online. To supervise user chat communications in Skype for Business Online, assign individual users or assign a distribution group to the communication compliance policy. This setting is for one-to-one or one-to-many user/chat relationships.
- **Third-party sources**: You can scan communications from third-party sources for data imported into mailboxes in your Microsoft 365 organization. Connectors support the following third-party resources:

  - [Instant Bloomberg](/microsoft-365/compliance/archive-instant-bloomberg-data?azure-portal=true)
  - [Facebook](/microsoft-365/compliance/archive-facebook-data-with-sample-connector?azure-portal=true)
  - [LinkedIn](/microsoft-365/compliance/archive-linkedin-data?azure-portal=true)
  - SAP SuccessFactors
  - [Twitter](/microsoft-365/compliance/archive-twitter-data-with-sample-connector?azure-portal=true)
  - [Custom data connector](/microsoft-365/compliance/archiving-third-party-data?azure-portal=true)

## Transitioning from Supervision Policies in Microsoft 365

Supervision policies in Microsoft 365 will be fully replaced by the communication compliance solution. Organizations using Supervision policies and planning to transition to communication compliance policies in Microsoft 365 need to understand these important points:

- Both solutions may be used side by side in your organization, but policies used in each solution must have *unique* policy names. Groups and custom keyword dictionaries can be shared between solutions during a transition period.
- Messages saved in supervision policy matches cannot be moved or shared into communication compliance.
- It is recommended that you create new policies in communication compliance that have the same *conditions* as existing supervision policies to use the new investigation and remediation improvements.
- When transitioning to communication compliance in Microsoft 365, you should plan to export reporting data from supervision in Office 365 if you have internal compliance retention policy requirements.

## Learn more

- [Archive third-party data](/microsoft-365/compliance/archiving-third-party-data?azure-portal=true)
