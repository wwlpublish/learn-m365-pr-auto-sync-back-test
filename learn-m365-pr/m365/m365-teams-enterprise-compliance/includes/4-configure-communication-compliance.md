It can be challenging to ensure that your users are always using appropriate language and images when they communicate within and outside the company.

In your firm of legal advisors, most staff have undergone training on the appropriate use of language and images. However, because you sometimes work with consultants who may not have been trained, you want to take extra steps to ensure compliance in this area.

Here, you'll learn how to use communication compliance features in Microsoft Teams to spot and prevent offensive communications.

## What is communication compliance?

Communication compliance helps you to detect, capture, and act on inappropriate messages within your organization. Communication compliance helps identify the following types of content:

- Offensive, profane, or harassing language
- Adult or gory images
- Sensitive information

Using communication compliance in Microsoft Teams can help minimize communication risks in your organization. After you've configured a communication compliance policy, you can actively manage inappropriate Microsoft Teams messages and content. Any inappropriate content will be automatically flagged in alerts.

> [!NOTE]
> Private Microsoft Teams channels are not supported by communication compliance. Also, chat communications sent by guest users to Teams users aren't monitored for inappropriate content.

## Communication compliance policies

Teams administrators can configure communication compliance policies for:

- User policies apply to an individual Teams user or may be applied to all Teams users in your organization. These policies cover messages that these users may send in 1:1 or group chats. Chat communications for the users are automatically monitored across all Microsoft Teams where the users are a member.
- Teams policies apply to a Microsoft Team channel. These policies cover messages sent in the Teams channel only.

## Communication compliance permissions

To manage communication policies and alerts, create one or more admin role groups. Assign users to specific role groups to manage different areas of communication compliance features or create one role group for all the communication compliance roles. The following table summarizes the roles and permissions:

|Role  |Role permissions  |
|---------|---------|
|Communication Compliance Admin     |   Permissions to create, read, update, and delete communication compliance policies, global settings, and role group assignments. No permissions to view message alerts.      |
|Communication Compliance Analysis    | Permissions to view policies where they are assigned as Reviewers, view message metadata, but not message content, escalate to additional reviewers, or send notifications to users. No permissions to resolve pending alerts.   |
|Communication Compliance Investigation    |  Permissions to view message metadata and content, escalate to additional reviewers, escalate to an Advanced eDiscovery case, send notifications to users, and resolve the alert.    |
|Communication Compliance Viewer     |    Permissions to access all reporting widgets on the communication compliance home page and view all communication compliance reports.     |
|Communication Compliance Case Management     |  Permissions to manage cases and act on alerts. Required when creating custom role groups for administrators, analysts, and investigators. Custom groups for viewers do not need this role assigned.       |
| | |

## Enable the audit log

Communication compliance requires that the audit log is enabled. The log shows alerts and tracks remediation actions taken by reviewers. The audit logs are a summary of all activities associated with a defined organizational policy or anytime a communication compliance policy changes.
You can use the Microsoft 365 Defender portal or PowerShell to turn on audit log search. You have to be assigned the Audit Logs role in Exchange Online to turn on audit log search.

To enable the audit log, follow these steps:

1. Sign into the [Microsoft 365 Defender portal](https://security.microsoft.com).
1. In the left navigation, select **Search** > **Audit log search**.
1. Select **Turn on auditing** on the **Audit log search** page.

:::image type="content" source="../media/4-switching-audit-logging.png" alt-text="A screenshot of the Audit log search page":::

After you turn on auditing, a message is displayed that says the audit log is being prepared and that you can run a search in a couple of hours after the preparation is complete. You only have to do this action once.

## Create a communication compliance policy for Microsoft Teams

Once the audit log is enabled, you can start creating policy for communication compliance:

1. Sign into the [Microsoft 365 compliance center](https://compliance.microsoft.com), from the left navigation, select **Show all** > **Communication compliance**.
1. Select the **Policies** tab.
1. Select **Create policy** to create a custom policy, or from a template.
1. When you choose a policy template, you will:
    - Give the policy a **name**. This cannot be changed once the policy is created.
    - Select **users or groups to supervise**, including users or groups you'd like to exclude.
    - Select the **reviewers** for the policy. Reviewers are individuals with a mailbox hosted on Exchange Online.
    - Select a **limited condition** field, usually a sensitive info type or keyword dictionary to apply to the policy.
1. If you choose a custom policy, you will:
    - Give the policy a **name** and optional description. Policy names can't be changed once the policy is created.
    - Select **users or groups to supervise**, including users or groups you'd like to exclude.
    - Select the **reviewers** for the policy. Reviewers are individuals with a mailbox hosted on Exchange Online.
    - Select the **communication channels** to scan, including Exchange, Microsoft Teams, Yammer, or Skype for Business. You'll also choose to scan third-party sources if you've configured a connector in Microsoft 365.
    - Select the **communication direction**, including inbound, outbound, or internal communications.
    - Define the communication compliance **policy conditions**. You can choose from message address, keyword, file types, and size match conditions.
    - Select whether to include default or custom sensitive information types. Pick from existing custom sensitive information types or use the custom keyword dictionaries.
    - Select whether to enable **classifiers** to detect inappropriate language and images. Choose one or more of the following built-in classifiers: Threat, Profanity, Targeted harassment, Adult images, Racy images, and Gory images. The Offensive Language classifier has been deprecated, so use the Threat, Profanity, and Targeted harassment built-in classifiers instead.
    - Define the **percentage** of communications to review.
1. **Review** your policy selections and then create the policy.
1. The **Your policy was created** page is displayed with guidelines on when policy will be activated and which communications will be captured.

## Learn more

To learn more about the topics covered in this unit, see:

- [Communication compliance with Microsoft Teams](/microsoftteams/communication-compliance).
- [Get started with communication compliance](/microsoft-365/compliance/communication-compliance-configure).
- [Turn audit log search on or off](/microsoft-365/compliance/turn-audit-log-search-on-or-off).
- [Search the audit log in the Microsoft 365 Defender portal](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance).
