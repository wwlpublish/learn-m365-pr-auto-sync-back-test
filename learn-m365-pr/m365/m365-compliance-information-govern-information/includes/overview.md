
Information governance helps you manage the end-to-end lifecycle of all content across your organization's digital estate, including Microsoft 365, third-party clouds, hybrid deployments, and any content you bring into Microsoft 365. Trainable classification and automated retention simplify the governance process.   It is about keeping the data necessary for business, regulatory, legal, or other reasons, and removing any data from your digital estate that should not be kept. This decreases your attack surface and minimizes compliance risk.

Retention policies help ensure you retain content as long as it is required, but no longer. With information governance, you can take two approaches to retention. You can use organization-wide policies, and you can use label-driven policies applied manually by a user or automatically by Microsoft 365.

Using organization-wide policies, you can choose to retain content for a specific time period or permanently delete content at the end of the retention period. Policies can apply to one or more locations where information is stored like Exchange Online, SharePoint Online and Microsoft Teams.

Label-driven policies enable users to contribute to the accuracy of your data retention implementation. Users can manually label their own content to classify it. You can also auto-apply labels to specific content to make things easier on users. As with organization-wide policies, you can choose to retain or delete content based on when it was created or last modified. In addition, you can base retention on when it was labeled or an event, such as an employee leaving the organization. Retention labels can be automatically applied to content containing sensitive data, specific words or phrases, or having certain metadata, or that it matches a trainable classifier.

> [!NOTE]
> Please refer to the Microsoft 365 licensing guidance for security and compliance for additional information on the licensing requirements for this solution.

## Customer scenarios

Here is some common scenarios Microsoft's solution for information governance can address:

- Create an organization-wide retention policy to delete all Microsoft Teams communications older than seven days.
- Review documents stored in a SharePoint document library prior to them being deleted because a retention policy expired.
- Implement a 5-year retention policy where automatically labeled content will be kept five years and then automatically deleted.

## Retention policy precedence

Situations may arise where content has several retention policies apply (or a combination of retention policies and a single retention label policy). These policies might have different actions (retain, delete, or both) and different retention periods. The following retention principles explain what takes precedence. The principles are applied from top to bottom. If the rules applied by all policies are the same at one level, the flow moves down to the next level to determine which rule is applied.

:::image type="content" source="../media/principles-of-retention.png" alt-text="Flowchart displaying the levels of Principles of retention.":::

### Retention wins over deletion

Suppose one retention policy says to delete Exchange email after three years, but another retention policy says to retain Exchange email for five years and then delete it. Any content that reaches three years old will be deleted and hidden from the user, but still retained in the Recoverable Items folder until the content reaches the five-year retention period. Then it would be permanently deleted. Content being retained by one policy cannot be permanently deleted by another policy.

### Longest retention period wins

If content is subject to multiple policies that retain content, it will be retained until the end of the longest retention period.

### Explicit inclusion wins over implicit inclusion

If a label with retention settings is manually assigned (known as an explicit label) by a user to an item, such as an Exchange email or OneDrive document, that label takes precedence over a policy assigned at the site or mailbox level or a default label assigned by the document library. For example, if the explicit label says to retain the item for 10 years, but the policy assigned to the site says to retain it for five years, the label takes precedence. Auto-applied labels are considered implicit, not explicit, because they are applied automatically by Microsoft 365.

If a retention policy includes a specific location, such as a specific user's mailbox or OneDrive account, that policy takes precedence over another retention policy that applies to all users' mailboxes or OneDrive accounts but does not specifically include that user's mailbox.

### Shortest deletion period win

If content is subject to multiple policies that delete content (with no retention), it will be deleted at the end of the shortest retention period.

## Getting started with information governance

 Deciding what you want to keep and for how long is at the core of information governance. Business, legal, and compliance requirements can impact your information governance strategy. Those responsible for information governance in your organization should identify the content to retain or dispose for business and legal requirements. The governance team will also need to identify the regulations that apply to your organization, many of which include information governance requirements.

**Microsoft Compliance Score** maps these compliance regulations, like the US Health Insurance Portability and Accountability Act (HIPAA), to actions recommended to achieve compliance. Many of these actions can be addressed using the **Information governance** solution. The image below shows the improvement actions in the **Information governance** solution the organization can take to improve its compliance posture relative to HIPAA.
  
:::image type="content" source="../media/compliance-score.png" alt-text="Screenshot showing Microsoft compliance score.":::

One of the first steps in creating a retention label is to tell Microsoft 365 if you want to apply retention settings. You may want to consider keeping this setting **Off** when creating and publishing (or auto-applying) a new label. You can then modify the retention label settings to add a retention period once you are satisfied it is working correctly. The image below shows the step during the retention label creation process where you specify if you want the label to apply retention. It may take as long as seven days for new retention labels to take effect after you publish or auto-apply them, so plan accordingly.

:::image type="content" source="../media/label-settings.png" alt-text="Screenshot shows Retention label settings. The retention button is turned off.":::

The instructions in the rest of this module assume you have added **Information governance** to the **Microsoft 365 compliance center** menu. This is also recommended if you are going to be working with the solution frequently. Here are the steps:

1. Open [**Microsoft 365 compliance center**](https://compliance.microsoft.com?azure-portal=true) in your web browser address bar.
1. Click **Customize navigation**.
1. Check the box that says **Information governance**.
1. Click **Save**.

## Learn more

- [Manage information governance](/microsoft-365/compliance/manage-information-governance?azure-portal=true)
- [Microsoft 365 security & compliance licensing guidance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance?azure-portal=true)
- [Information governance licensing guidance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance)
- [Applying a retention label automatically](/microsoft-365/compliance/labels?applying-a-retention-label-automatically-based-on-conditions?azure-portal=true)
