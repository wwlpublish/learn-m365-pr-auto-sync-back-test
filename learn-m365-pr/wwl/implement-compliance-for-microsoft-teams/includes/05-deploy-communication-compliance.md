Communication compliance helps minimize communication risks by helping you detect, capture, and act on inappropriate messages in your organization. 

Communication compliance is an insider risk solution in Microsoft 365. The pre-defined and custom policies allow you to scan internal and external communications for policy matches so they can be examined by chosen reviewers. Reviewers can investigate inappropriate content and take appropriate actions to make sure they're compliant with your organization's message standards.

## Supported communication channels
Communication compliance policies scan and capture messages across several communication channels to help you quickly review and remediate compliance issues. The supported communication channels include: **Microsoft Teams**, **Exchange**,**Skype for Business**, **Yammer**, and **Third-party sources**.

For Microsoft Teams, communication compliance helps identify the inappropriate content in Teams channels, Private Teams channels, or in 1:1 and group chats. For example:

* Offensive, profane, and harassing language
* Adult, racy, and gory images
* Sharing of sensitive information

## Workflow
Identifying and resolving compliance issues with communication compliance in Microsoft 365 uses the following workflow:

:::image type="content" source="../media/communication-compliance-workflow.png" alt-text="Diagram communication compliance workflow. ":::

### Configure

You identify your compliance requirements and configure applicable communication compliance policies.  Keep in mind that you'll need to configure some [permissions and basic prerequisites](/microsoft-365/compliance/communication-compliance-configure) as part of the configuration process. Teams administrators can configure communication compliance policies at the following levels:

* **User level**. Policies at this level apply to an individual Teams user or may be applied to all Teams users in your organization. These policies cover messages that these users may send in 1:1 or group chats. Chat communications for the users are automatically monitored across all Microsoft Teams where the users are a member.

* **Teams level**. Policies at this level apply to a Microsoft Team channel. These policies cover messages sent in the Teams channel only.

You must navigate to **Microsoft 365 compliance center** > **Communication compliance** to create policies. You can choose from the following policy templates:

- **Offensive or threatening language**. Use this template to quickly create a policy that uses built-in classifiers to automatically detect content that may be considered abusive or offensive.
- **Sensitive information**. Use this template to quickly create a policy to scan communications containing defined sensitive information types or keywords to help make sure that important data isn't shared with people that shouldn't have access.
- **Regulatory compliance**. Use this template to quickly create a policy to scan communications for references to standard financial terms associated with regulatory standards.
- **Conflict of interest**. Use this template to quickly create a policy to monitor communications between two groups or two users to help avoid conflicts of interest.
- **Custom policy**. Use this template to configure specific communication channels, individual detection conditions, and the amount of content to monitor and review in your organization.

### Investigate

You look deeper into the issues detected as matching your communication compliance policies. The actions include:

- **Alerts**. When a message matches a policy condition, an alert is automatically generated. For each alert, you can see the status, the severity, the time detected, and if an Advanced eDiscovery case is assigned and its status. New alerts are displayed on the communication compliance home page and the **Alerts** page and are listed in order of severity.
- **Issue management**. For each alert, you can take investigative actions to help remediate the issue detected in the message.
- **Document review**. During the investigation of an issue, you can use several views of the message to help properly evaluate the detected issue. The views include a conversation summary, text-only, annotated, and detail views of the communication conversation.
- **Reviewing user activity history**. View the history of user message activities and remediation actions, such as past notifications and escalations, for policy matches.
- **Filters**. Use filters such as sender, recipient, date, and subject to quickly narrow down the message alerts that you want to review.

### Remediate

After you have configured your policies and have received communication compliance alerts for Microsoft Teams messages, it's time for compliance reviewers in your organization to take action on these messages. Reviewers can help safeguard your organization by reviewing communication compliance alerts and removing flagged messages from view in Microsoft Teams. 

:::image type="content" source="../media/communication-compliance-remove-teams-message.png" alt-text="Remove a message in Teams" lightbox="../media/communication-compliance-remove-teams-message.png":::

The actions to remediate communication compliance issues include:

- **Resolve**. Resolving an alert removes it from the pending alert queue, and the action is preserved as an entry in the *Resolved queue* for the matching policy. Alerts are automatically resolved after marking the alert as misclassified, sending a notice to a user about the alert, or opening a new case for the alert.

- **Tag a message**. As part of the resolution of an issue, you can tag the detected message as compliant, non-compliant, or as questionable as it relates to the policies and standards for your organization. Tagging can help you micro-filter policy alerts for escalations or as part of other internal review processes.

- **Notify the user**. Often, users accidentally or inadvertently violate a communication compliance policy. You can use the notify feature to provide a warning notice to the user and to resolve the issue.

- **Escalate to another reviewer**. Sometimes, the initial reviewer of an issue needs input from other reviewers to help resolve the incident. You can easily escalate message issues to reviewers in other areas of your organization as part of the resolution process.

- **Report as misclassified**. Messages incorrectly detected as matches of compliance policies will occasionally slip through to the review process. You can mark these types of alerts as misclassified, submit feedback to Microsoft about the misclassification to help improve global classifiers, and automatically resolve the issue.

- **Escalate for investigation**. In the most serious situations, you may need to share communication compliance information with other reviewers in your organization.  Escalating a case for investigation allows you to transfer data and management of the case to Advanced eDiscovery in Microsoft 365.It allows legal teams to manage the entire legal hold notification workflow.

- **Remove message in Teams (preview)**. Inappropriate messages may be removed from displaying in Microsoft Teams channels or personal and group chat messages. Inappropriate messages that are removed are replaced with a notification that the message has been removed for a policy violation.

    Removed messages and content can be replaced with notifications for viewers explaining that the message or content has been removed and what policy is applicable to the removal. The sender of the removed message or content is also notified of the removal status and provided with original message content for context relating to its removal. The sender can also view the specific policy condition that applies to the message removal.

    |Examples|Screenshots|
    |--|--|
    |Policy tip for sender | :::image type="content" source="../media/communication-compliance-warning-sender-tip.png" alt-text="Policy tip for sender":::|
    |Policy condition notification|:::image type="content" source="../media/communication-compliance-warning-notification.png" alt-text="Policy condition info for sender":::|
    |Policy tip for recipient|:::image type="content" source="../media/communication-compliance-warning-recipient.png" alt-text="Policy tip for recipient":::|

### Monitor
Keeping track and managing compliance issues identified by communication compliance policies spans the entire workflow process.


- **Monitor and report**. Use communication compliance dashboard widgets, export logs, and events recorded in the unified audit logs to continually evaluate and improve your compliance posture.

For more information, see [Configure communication compliance in Microsoft 365](/microsoft-365/compliance/communication-compliance-configure).


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”