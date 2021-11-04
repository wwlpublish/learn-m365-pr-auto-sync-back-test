Data loss prevention (DLP) is an important component of messaging systems. Since companies make extensive use of email to send and receive business-critical enterprise data, that data needs to be protected against accidental or intentional loss. It also needs to be protected from being accidentally or intentionally shared with unauthorized users. DLP policies are designed to protect your enterprise data before it leaves your company and area of influence, while not hindering the productivity of your workers. You can configure DLP policies in the Microsoft 365 Defender portal.

A DLP policy contains the following components:

 -  **Locations.** Define where to protect the content, such as Exchange Online, SharePoint Online, and OneDrive for Business sites.
 -  **Rules.** Rules define the “when” and “how” to protect content, and they consist of conditions and actions.
    
     -  **Conditions.** Defines the requisite state the content must match before the rule is enforced. For example, look only for content containing Social Security numbers that have been shared with people outside your organization.
     -  **Actions.** The steps that you want the rule to complete when content matching the conditions is found. For example, block access to the document and send both the user and compliance officer an email notification.

You can use a rule to meet a specific protection requirement, and then use a DLP policy to group together common protection requirements, such as all the rules needed to follow a specific regulation.

:::image type="content" source="../media/data-loss-prevention-policy-91645f6c.png" alt-text="Diagram showing the relationship between rules and DLP policies":::


> [!NOTE]
> In contrast to DLP policies in Exchange, DLP policies in the Microsoft 365 Defender portal can cover many different locations and services across the entire tenant.

### DLP Rules

Rules are what enforce your business requirements on your organization's content. A policy contains one or more rules, and each rule consists of conditions and actions. When the conditions are met for each rule, the actions are taken automatically. Rules are executed sequentially, starting with the highest-priority rule in each policy.

A rule also provides options to notify users (with policy tips and email notifications) and admins (with email incident reports) that content has matched the rule.

:::row:::
  :::column:::
    **Rule part**
  :::column-end:::
  :::column:::
    **Description**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Conditions
  :::column-end:::
  :::column:::
    

Conditions are important because they determine what types of information you're looking for, and when to take an action. For example, you might choose to ignore content containing passport numbers unless the content contains more than 10 such numbers and is shared with people outside your organization.


Conditions focus on both the content, such as what types of sensitive information you're looking for, and the context, such as who the document is shared with. You can use conditions to assign different actions to different risk levels. For example, sensitive content shared internally may be a lower risk and require fewer actions than sensitive content shared with people outside the organization.


The conditions now available can determine if:

 -  Content contains a type of sensitive information.
 -  Content contains a label.
 -  Content is shared with people outside or inside your organization.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Sensitive information types
  :::column-end:::
  :::column:::
    

A DLP policy can help protect sensitive information from being accidentally or intentionally shared with unauthorized users. This data is defined as a sensitive information type. Microsoft 365 includes definitions for many common sensitive information types across many different regions that are ready for you to use, such as a credit card number, bank account numbers, national ID numbers, and passport numbers.


When a DLP policy looks for a sensitive information type such as a credit card number, it doesn't look just for a 16-digit number. Each sensitive information type is defined and detected by using a combination of:

 -  Keywords
 -  Internal functions to validate checksums or composition.
 -  Evaluation of regular expressions to find pattern matches.
 -  Other content examination

This process helps DLP detection achieve a high degree of accuracy while reducing the number of false positives that can interrupt peoples' work.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Actions
  :::column-end:::
  :::column:::
    When content matches a condition in a rule, you can apply actions to automatically protect the content. For example, you can restrict access to the content. For emails, this action blocks the message from being sent. Depending on how the DLP rule is configured, the sender will see an NDR or (if the rule uses a notification) a policy tip and an email notification.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    User notifications and user overrides
  :::column-end:::
  :::column:::
    

You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to send an email containing sensitive information, a DLP policy can display a policy tip that explains, why content conflicts with a DLP policy.


If you choose, the email notification and policy tip can allow users to override a rule by reporting a false positive or providing a business justification. This process helps organizations educate their users about their DLP policies. It also helps organizations enforce them without preventing people from doing their work.

Information about overrides and false positives is also logged for reporting (see below about the DLP reports) and included in the incident reports. Logging enables the compliance officer to regularly review this information.


  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Incident reports
  :::column-end:::
  :::column:::
    When a rule is matched, you can send an incident report to your compliance officer (or any people you choose) with details of the event. This report includes information about the item that was matched, the actual content that matched the rule, and the name of the person who last modified the content. For email messages, the report also includes as an attachment the original message that matches a DLP policy.
  :::column-end:::
:::row-end:::


**Additional reading**. For more information, see [What the sensitive information types look for](/microsoft-365/compliance/sensitive-information-type-entity-definitions?azure-portal=true).

### DLP reports

DLP reports gain insight about the number of DLP policy and rule matches and the number of false positives and overrides. For each report, you can filter those matches by location, time frame, and even narrow it down to a specific policy, rule, or action.

The following business insights are available with DLP reports:

 -  Focus on specific time periods and understand the reasons for spikes and trends.
 -  Discover business processes that violate your organization's compliance policies.
 -  Understand any business impact of the DLP policies.

You can also use the DLP reports to fine-tune your DLP policies as you run them.

### How DLP relates to other features

Several features can be applied to content containing sensitive information:

 -  A retention label and a retention policy can both enforce retention actions on this content.
 -  A DLP policy can enforce protection actions on this content. And before enforcing these actions, a DLP policy can require other conditions to be met besides the content containing a label.

:::image type="content" source="../media/data-loss-prevention-sensitive-info-f45344f5.png" alt-text="Graphic showing the objects that can be applied to sensitive information.":::


A DLP policy has a richer detection capability than a label or retention policy applied to sensitive information. A DLP policy can enforce protective actions on content containing sensitive information, and if the sensitive information is removed from the content, those protective actions are undone the next time the content's scanned. But if a retention policy or label is applied to content containing sensitive information, that's a one-time action that won't be undone even if the sensitive information's removed.

By using a label as a condition in a DLP policy, both retention and protection actions can be enforced on content with that label. Consider content containing a label exactly like content containing sensitive information - both a label and a sensitive information type are properties used to classify content so that you can enforce actions on that content.
